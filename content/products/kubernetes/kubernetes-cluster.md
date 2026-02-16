---
title: K8S Cluster
weight: 10
---
___
On this page, you can find an explanation of how to create, resize, delete Kubernetes Cluster and instructions for other steps to manage Kubernetes Cluster and its Node Pools in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Clusters page](#clusters-page)
  - [Create Cluster](#create-cluster)
  - [Cluster details page](#cluster-details-page)
  - [Node Pools Management](#node-pools-management)
    - [Node Pool Types and Scaling Behavior](#node-pool-types-and-scaling-behavior)
    - [Create Node Pool](#create-node-pool)
    - [Resize Node Pool](#resize-node-pool)
    - [Node Pool Autoscaling Configuration](#node-pool-autoscaling-configuration)
    - [Upgrade Node Pool](#upgrade-node-pool)
  - [Upgrade Cluster](#upgrade-cluster)
  - [Download kubeconfig file](#download-kubeconfig-file)
  - [Delete Cluster](#delete-cluster)


## Clusters page
To get to the *Clusters page*, select the **Clusters** from the VIRTUAL DATACENTER block in the *side-bar menu*:
![](../../../assets/images/clusters/1.png?width=15pc&classes=border,shadow)  

On this page you can find all created Kubernetes Clusters in the current Project of the selected Organization, with the *Create button, Search bar* and *Actions icon* which opens a list of available management actions for the selected Cluster:
![](../../../assets/images/clusters/2.png?classes=border,shadow)   

**Actions** icon opens the next list of available management actions:
- *Download kubeconfig file* - this option is used to get the kubeconfig file, that pertains to the selected Cluster;
- *Delete* - this option is for Cluster removing.

## Create Cluster
To create new Cluster, do the following:
- go to the *Clusters page* and click on the CREATE CLUSTER icon in the upper left corner;
- fill in the form on the next opened *Create Cluster window* and click on the CREATE icon:

![](../../../assets/images/clusters/3.png?width=30pc&classes=border,shadow) 
  - *Name* - set a name for the Cluster;
  - *Cluster Template* - select the template that will be used to create Cluster;     
  - *Master Flavor* - select the size of the Cluster master-nodes (min is VC-2);  
  - *Node Flavor* - select the size of the Cluster worker-nodes (min is VC-2);  
  - *Key pair* - select the SSH Keypair that was previously created on the *Keypair page* or create a new one;   
    💡 SSH Keypair you will use to configure in the Cluster servers for ssh access;    
  - *Docker image size (GB)* - provide the preferred disc size where container images will be stored;  
    💡 the range - from 50 GB to 1000 GB;  
  - *Master Count* - set how many master-nodes the Cluster will contain;   
    💡 for production environments, use at least 3 master-nodes;  
  - *Node Count* - set how many worker-nodes the Cluster will contain;     
  - *Enable auto-scaling* - if you choose to enable this option, please set the  limits of node count;  
    💡 the max count is 10 nodes; 
  - *Accessible on private network only*.

After these steps, the newly created Cluster will be added to the *Clusters page* with the status CREATE_COMPLETE.  
Estimate creation time about 5 minutes.

## Cluster details page
To open the *Cluster details page*, click on the **Name** of the corresponding Cluster:
![](../../../assets/images/clusters/7.png?classes=border,shadow)

This action will redirect you to the *Cluster details page*, where you can find:  
- Cluster **details area** with actual information about it - Status, Health, Kube Version, Created timestamp; Current Master Nodes count, Flavor and Connection section with API Address:  

![](../../../assets/images/clusters/29.png?classes=border,shadow)

- panel with available **quick actions** include management actions with this cluster such as: delete, download kubeconfig file and cluster upgrade:
![](../../../assets/images/clusters/30.png?width=15pc&classes=border,shadow)

- transition to the NODE POOLS and LABELS pages related to this Cluster:  
![](../../../assets/images/clusters/31.png?width=15pc&classes=border,shadow)
  
**NODE POOLS TAB** - opens the *Cluster Node Pools page* where you can find all available Node Pools of corresponding Cluster with their details; add, delete, resize, and configure autoscaling for individual Node Pools.  

💡 More information about the *Node Pools Management* will be provided in the following sections.  
![](../../../assets/images/clusters/32.png?classes=border,shadow)  

**LABELS TAB** - opens the *Cluster Labels page* with some additional information about this cluster:
![](../../../assets/images/clusters/33.png?classes=border,shadow) 

## Node Pools Management

The **NODE POOLS** tab displays all node pools within the selected Kubernetes cluster, showing their current status, node count, flavor specifications, and base images. Each node pool can be managed independently with different scaling and configuration options.

### Node Pool Types and Scaling Behavior

**Master Node Pool (default-master):**  
- Supports horizontal scaling up only (1→2→3 nodes)
- Cannot be scaled down once additional nodes are added
- Critical for cluster control plane high availability
- **Upgrade**: Requires whole cluster upgrade using **Action Button > Upgrade**

**Worker Node Pool (default-worker):**  
- Supports bidirectional scaling (scale up and down)
- Configurable autoscaling can be enabled or disabled
- Handles application workload distribution
- **Upgrade**: Requires whole cluster upgrade using **Action Button > Upgrade**

### Create Node Pool

When creating new node pools using the **ADD NODE POOL** button, administrators can:

- **Kubernetes Version**: Deploy node pools with different Kubernetes versions than the cluster default
- **Node Sizing**: Configure specific node flavors and resource allocations
- **Autoscaling Options**: 
  - Enable autoscaling with minimum and maximum node limits
  - Create fixed-size pools without autoscaling
- **Custom Configuration**: Define labels, taints, and other node-specific settings
- **Independent Upgrades**: Create and upgrade separate node pools to newer versions independently

![](../../../assets/images/clusters/25.png?width=30pc&classes=border,shadow)

### Resize Node Pool

To resize the Node Pool, do the following:
- identify the Node Pool, that you want to resize, on the *Cluster details page*;
- click on the **Actions** icon  and select the **Resize** in the list of available options;
- update the count of Worker-nodes in the Node Pool on the opened *Resize Node Pool window* and click on the SAVE icon:

![](../../../assets/images/clusters/27.png?width=30pc&classes=border,shadow)

### Node Pool Autoscaling Configuration

To enable or disable the Autoscaling for the Node Pool, do the following:
- identify the Node Pool, that you want to upgrade, on the *Cluster details page*;
- click on the **Actions** icon  and select the **Configure Autoscaling** in the list of available options;
- select the option to enable or disable the Autoscaling for the selected Node Pool on the opened *Autoscaling Node Pool window* or change the minimum and maximum node count and click on the SAVE icon:

![](../../../assets/images/clusters/28.png?width=30pc&classes=border,shadow)

### Upgrade Node Pool

To upgrade the Node Pool, do the following:
- identify the Node Pool, that you want to upgrade, on the *Cluster details page*;
- click on the **Actions** icon  and select the **Upgrade** in the list of available options;
- select the version to which you want to upgrade the selected Node Pool on the opened *Upgrade Node Pool window* and click on the UPGRADE icon:

## Upgrade Cluster

{{% notice note %}}
📌 For cluster upgrading you can select only a version that is higher than current one or you can choose the current version to re-apply the configuration.
{{% /notice %}}

To upgrade the Cluster, do the following:
- identify the Cluster, that you want to upgrade, on the *Clusters page*;
- go to the *Cluster details page*;
- click on the **Actions** icon  and select the **Upgrade** in the list of available options;

![](../../../assets/images/clusters/34.png?width=15pc&classes=border,shadow)

- select the version to which you want to upgrade the selected Cluster on the opened *Upgrade Cluster window* and click on the UPGRADE icon:

![](../../../assets/images/clusters/23.png?width=30pc&classes=border,shadow)

After these steps, the selected Cluster will be upgraded after a few minutes with the status UPDATE_COMPLETE.  

## Download kubeconfig file

{{% notice note %}}
💡 The kubeconfig file is required to configure access to a cluster and switch between multiple clusters, multiple users, and with different authentication mechanisms such as passwords or tokens.
{{% /notice %}}

To download the kubeconfig file that pertains to Cluster, do the following:
- identify this desired Cluster on the *Clusters page*;
- click on the **Actions** icon and select the **Download kubeconfig file** in the list of available options.  

After these steps, the *kubeconfig file* will be downloaded. 

Also, you can download the kubeconfig file from *Cluster details page*, by clicking on the appropriative **quick actions** icon there:

![](../../../assets/images/clusters/35.png?width=15pc&classes=border,shadow)

## Delete Cluster
To delete the Cluster, do the following:
- identify this unnecessary Cluster on the *Clusters page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Cluster deletion on the next opened *Confirmation window*. 

After these steps, the selected Cluster will be deleted after a few minutes.  

Also, you can delete the Cluster from *Cluster details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/clusters/36.png?width=10pc&classes=border,shadow)



