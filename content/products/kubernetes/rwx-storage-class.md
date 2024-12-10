---
title: RWX Storage Class
weight: 15
---
___
On this page, you can find an explanation of how to access your Kubernetes cluster and configure ReadWriteMany (RWX) storage using SeaweedFS.

# Table of contents
- [Configuring SeaweedFS as RWX Storage in Kubernetes](#configuring-seaweedfs-as-rwx-storage-in-kubernetes)
  - [Why SeaweedFS for RWX Storage?](#why-seaweedfs-for-rwx-storage)
  - [SeaweedFS Components](#seaweedfs-components)
  - [Non-HA vs. HA](#non-ha-vs-ha)
  - [Installing SeaweedFS and the CSI Driver](#installing-seaweedfs-and-the-csi-driver)
  - [Testing RWX Storage](#testing-rwx-storage)

# Configuring SeaweedFS as RWX Storage in Kubernetes

This guide walks you through setting up SeaweedFS as an NFS-like RWX (ReadWriteMany) storage solution in a Kubernetes cluster. We’ll cover:

- What SeaweedFS is and why it’s used
- Non-HA (single-replica) vs. HA (multi-replica) configurations
- The roles of the Master, Volume servers, and Filer
- Installing and configuring SeaweedFS and its CSI driver
- Testing your RWX storage with real applications
- Production recommendations (e.g., resource limits, scaling, etc.)

## Why SeaweedFS for RWX Storage?

**RWX (ReadWriteMany)** storage classes allow multiple pods to read and write to the same persistent volume simultaneously. This is essential for workloads that share state or content, such as web applications serving identical static content or workloads that must scale horizontally without losing access to shared data.

While traditional solutions like NFS servers or managed cloud file systems are available, **SeaweedFS** stands out for its:

- **Scalability**: Designed to handle billions of files efficiently.
- **Simplicity**: Easier to set up compared to many distributed block storage solutions.
- **Performance**: SeaweedFS provides near O(1) disk seek for small files, and can handle large amounts of data.
- **Flexibility**: Supports replication, making it easy to achieve a highly available (HA) setup.

## SeaweedFS Components

**Master**:
Coordinates the cluster and stores metadata about volume locations. A single master can run for a basic setup. For HA, multiple masters (usually 3) are used to form a consensus group. The metadata stored here is relatively small compared to actual file data.

**Volume Server(s)**:
Store the actual file data in "volumes." You can have one volume server for a non-HA setup, or multiple for redundancy. Volume servers can replicate data according to your replication policy (e.g., "001" for one additional copy).

**Filer**:
The Filer provides a filesystem interface on top of volume servers. It manages directories and file metadata. The Filer is what you point your CSI driver at to gain NFS-like RWX semantics. Typically, the Filer stores minimal metadata compared to the raw data in volumes.

## Non-HA vs. HA

### Non-HA Setup

- **Single Master, Single Volume Server, Single Filer**
- Simpler and uses fewer resources
- Recommended for development or testing
- If the Master or Volume server fails, the data or metadata may become unavailable
- Example: A single replica of each component (master, volume, filer) with no replication.

### HA Setup

- **Multiple Masters (e.g., 3), Multiple Volume Servers (e.g., 2), Multiple Filer Replicas**
- Set replication policies (e.g., `001`) for automatic data redundancy
- Failover capabilities: If one Master or Volume server fails, others take over
- Ideal for production environments
- Supports horizontal scaling
- More complex and resource-intensive, but provides continuous availability

**Production Recommendations:**

- Set resource limits on Master, Volume, and Filer pods to ensure stable performance.
- Use replication settings like `001` to maintain availability during node failures.
- Employ liveness and readiness probes to ensure pods self-heal.
- Allocate PVC sizes thoughtfully:
  - Master & Filer PVCs can be relatively small (a few Gi), as they store metadata.
  - Volume servers need larger PVCs depending on your data requirements (e.g., 100Gi or more).
- Consider using multiple replicas of each component and robust StorageClasses.

## Installing SeaweedFS and the CSI Driver

1. **Add Repositories and Update:**

   ```bash
   helm repo add seaweedfs https://seaweedfs.github.io/seaweedfs/helm
   helm repo add seaweedfs-csi-driver https://seaweedfs.github.io/seaweedfs-csi-driver/helm
   helm repo update
   ```

2. **Deploying a Non-HA Setup (for testing):**

   ```bash
   helm upgrade --install seaweedfs seaweedfs/seaweedfs --create-namespace --namespace seaweedfs \
    --set global.enableSecurity=false \
    --set global.enableReplication=false \
    --set master.enabled=true \
    --set master.defaultReplication=000 \
    --set master.data.type=persistentVolumeClaim \
    --set master.data.size=2Gi \
    --set master.logs.type=persistentVolumeClaim \
    --set master.logs.size=1Gi \
    --set volume.enabled=true \
    --set volume.dataDirs[0].name=data1 \
    --set volume.dataDirs[0].type=persistentVolumeClaim \
    --set volume.dataDirs[0].size=50Gi \
    --set filer.enabled=true \
    --set filer.defaultReplicaPlacement=000 \
    --set filer.data.type=persistentVolumeClaim \
    --set filer.data.size=10Gi \
    --set filer.logs.type=persistentVolumeClaim \
    --set filer.logs.size=1Gi \
    --set filer.s3.enabled=false \
    --set s3.enabled=false \
    --set cosi.enabled=false
   ```

3. **Deploying a HA Setup (for production):**

   --set volume.dataDirs[0].size=100Gi - Adjust as needed

   ```bash
   helm upgrade --install seaweedfs seaweedfs/seaweedfs --create-namespace --namespace seaweedfs \
    --set global.enableSecurity=false \
    --set global.enableReplication=true \
    --set global.replicationPlacment=001 \
    --set master.enabled=true \
    --set master.replicas=3 \
    --set master.defaultReplication=001 \
    --set master.data.type=persistentVolumeClaim \
    --set master.data.size=2Gi \
    --set master.logs.type=persistentVolumeClaim \
    --set master.logs.size=1Gi \
    --set volume.enabled=true \
    --set volume.replicas=2 \
    --set volume.dataDirs[0].name=data1 \
    --set volume.dataDirs[0].type=persistentVolumeClaim \
    --set volume.dataDirs[0].size=100Gi \
    --set filer.enabled=true \
    --set filer.replicas=2 \
    --set filer.defaultReplicaPlacement=001 \
    --set filer.data.type=persistentVolumeClaim \
    --set filer.data.size=10Gi \
    --set filer.logs.type=persistentVolumeClaim \
    --set filer.logs.size=1Gi \
    --set filer.s3.enabled=false \
    --set s3.enabled=false \
    --set cosi.enabled=false
   ```

4. **Deploy the SeaweedFS CSI Driver:**

   ```bash
   helm upgrade --install seaweedfs-csi seaweedfs-csi-driver/seaweedfs-csi-driver --namespace seaweedfs \
    --set seaweedfsFiler="seaweedfs-filer:8888"
   ```

    Now you have a seaweedfs-storage StorageClass that supports RWX.

## Testing RWX Storage

1. **Test with BusyBox**

    ```bash
    cat <<EOF | kubectl apply -f -
    ---
    apiVersion: v1
    kind: PersistentVolumeClaim
    metadata:
      name: nfs-test
    spec:
      accessModes:
      - ReadWriteMany
      resources:
        requests:
          storage: 10Gi
      storageClassName: seaweedfs-storage
    ---
    apiVersion: apps/v1
    kind: Deployment
    metadata:
      labels:
        app: nfs-demo
      name: nfs-busybox
    spec:
      replicas: 5
      selector:
        matchLabels:
          app: nfs-demo
      template:
        metadata:
          labels:
            app: nfs-demo
        spec:
          volumes:
          - name: nfs-test-vol
            persistentVolumeClaim:
              claimName: nfs-test
          terminationGracePeriodSeconds: 5
          containers:
          - image: busybox
            imagePullPolicy: IfNotPresent
            name: busybox
            volumeMounts:
            - name: nfs-test-vol
              mountPath: "/mnt"
            command:
              - sh 
            args:
              - -c
              - |
                while true; do
                  echo "\$(date) \$(hostname)" > /mnt/shared.log
                  sleep $(($RANDOM % 5 + 5))
                done
    EOF
    ```

    Check any BusyBox pod’s log file:

    ```bash
    kubectl exec -it $(kubectl get pod -l app=nfs-demo -o jsonpath='{.items[0].metadata.name}') -- cat /mnt/shared.log
    ```

    You should see entries from multiple pod hostnames, confirming RWX functionality.

This documentation provides a robust framework for deploying and testing SeaweedFS as an RWX solution in Kubernetes. For additional customization or troubleshooting, refer to the [SeaweedFS documentation](https://github.com/seaweedfs/seaweedfs).
