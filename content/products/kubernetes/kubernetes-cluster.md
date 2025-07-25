---
title: K8S Cluster
weight: 10
---
___
On this page, you can find an explanation of how to create, resize, delete Kubernetes Cluster and instructions for other steps to manage Kubernetes Cluster in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Clusters page](#clusters-page)
  - [Create Cluster](#create-cluster)
  - [Cluster details page](#cluster-details-page)
  - [Download kubeconfig file](#download-kubeconfig-file)
  - [Resize Cluster](#resize-cluster)
  - [Upgrade Cluster](#upgrade-cluster)
  - [Delete Cluster](#delete-cluster)


## Clusters page
To get to the *Clusters page*, select the **Clusters** from the VIRTUAL DATACENTER block in the *side-bar menu*:
![](../../../assets/images/clusters/1.png?width=15pc&classes=border,shadow)  

On this page you can find all created Kubernetes Clusters in the current Project of the selected Organization, with the *Create button, Search bar* and *Actions icon* which opens a list of available management actions for the selected Cluster:
![](../../../assets/images/clusters/2.png?classes=border,shadow)   

**Actions** icon opens the next list of available management actions:
- *Download kubeconfig file* - this option is used to get the kubeconfig file, that pertains to the selected Cluster;
- *Resize* - this option is used to change the count of Worker-nodes in the selected Cluster;
- *Upgrade* - this option is used to update template (version) of the selected Cluster;
- *Delete* - this option is for Cluster removing.

## Create Cluster
To create new Cluster, do the following:
- go to the *Clusters page* and click on the CREATE CLUSTER icon in the upper left corner;
- fill in the form on the next opened *Create Cluster window* and click on the CREATE icon:

![](../../../assets/images/clusters/3.png?width=30pc&classes=border,shadow) 
  - *Name* - set a name for the Cluster;
  - *Cluster Template* - select the template that will be used to create Cluster;  
    by default, the newest one is pre-selected;   
  - *Master Flavor* - select the size of the Cluster master-nodes (min is VC-2);  
    by default, "VC-4 (2 vCPUs, 4 GiB memory)" is pre-selected;   
  - *Node Flavor* - select the size of the Cluster worker-nodes (min is VC-2);  
    by default, "VC-4 (2 vCPUs, 4 GiB memory)" is pre-selected;   
  - *Key pair* - select the SSH Keypair that was previously created on the *Keypair page* or create a new one;   
    SSH Keypair you will use to configure in the Cluster servers for ssh access;  
    if you have only one created SSH Key, it will be pre-selected by default;  
  - *Docker image size (GB)* - provide the preferred disc size where container images will be stored, it can be specified in the range from 50 GB to 1000 GB;  
    by default, 50 GB is pre-selected;  
  - *Master Count* - set how many master-nodes the Cluster will contain;   
    by default, 1 is pre-selected;  
  - *Node Count* - set how many worker-nodes the Cluster will contain;  
    by default, 1 is pre-selected;    

  And the last field you can make a marks: 
  - *Enable auto-scaling* - if you choose to enable this option, please set the  limits of node count; the max count is 10 nodes; 
  - *Accessible on private network only*.

After these steps, the newly created Cluster will be added to the *Clusters page* with the status CREATE_COMPLETE (Estimate creation time about 5 minutes).

## Cluster details page
To open the *Cluster details page*, click on the **Name** of the corresponding Cluster:
![](../../../assets/images/clusters/7.png?classes=border,shadow)

This action will redirect you to the *Cluster details page*, where you can find four tabs with additional information about selected Cluster and panel with available **quick actions**:
- panel with available **quick actions** include all available management actions with this cluster such as: resize, delete, upgrade and download kubeconfig file:

![](../../../assets/images/clusters/12.png?width=25pc&classes=border,shadow)

- INFO Tab with actual information about this Cluster: ID, Current Status, Errors, Creation Date, Date of the last update and Cluster template:

![](../../../assets/images/clusters/8.png?width=30pc&classes=border,shadow)

- NODES Tab with actual information about Cluster's Nodes: Master and Node count, their IP addresses and API address of the Cluster:

![](../../../assets/images/clusters/9.png?width=30pc&classes=border,shadow)

- MISCELLANEOUS Tab with next information: Discovery URL, Cluster create timeout, Key pair that was used during the Cluster creation, Master and Node flavors, and current Health status of the selected Cluster:

![](../../../assets/images/clusters/10.png?width=30pc&classes=border,shadow)

- LABELS Tab with some additional information about this cluster:

![](../../../assets/images/clusters/11.png?width=30pc&classes=border,shadow)

## Download kubeconfig file

{{% notice info %}}
The kubeconfig file is required to configure access to a cluster and switch between multiple clusters, multiple users, and with different authentication mechanisms such as passwords or tokens.
{{% /notice %}}

To download the kubeconfig file that pertains to Cluster, do the following:
- identify this desired Cluster on the *Clusters page*;
- click on the **Actions** icon and select the **Download kubeconfig file** in the list of available options.  

After these steps, the *kubeconfig file* will be downloaded. 

Also, you can download the kubeconfig file from *Cluster details page*, by clicking on the appropriative **quick actions** icon there:

![](../../../assets/images/clusters/20.png?width=25pc&classes=border,shadow)

## Resize Cluster
To resize the Cluster, do the following:
- identify the Cluster, that you want to resize, on the *Clusters page*;
- click on the **Actions** icon  and select the **Resize** in the list of available options;
- update the count of Worker-nodes in the Cluster on the opened *Resize Cluster window* and click on the SAVE icon:

![](../../../assets/images/clusters/5.png?width=30pc&classes=border,shadow)

After these steps, the selected Cluster will be resized after a few minutes with the status UPDATE_COMPLETE.  

Also, you can resize the Cluster from *Cluster details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/clusters/21.png?width=25pc&classes=border,shadow)

## Upgrade Cluster

{{% notice note %}}
For cluster upgrading you can select only a version that is higher than current one or you can choose the current version to re-apply the configuration.
{{% /notice %}}

To upgrade the Cluster, do the following:
- identify the Cluster, that you want to upgrade, on the *Clusters page*;
- click on the **Actions** icon  and select the **Upgrade** in the list of available options;
- select the version to which you want to upgrade the selected Cluster on the opened *Upgrade Cluster window* and click on the UPGRADE icon:

![](../../../assets/images/clusters/23.png?width=30pc&classes=border,shadow)

After these steps, the selected Cluster will be upgraded after a few minutes with the status UPDATE_COMPLETE.  

Also, you can upgrade the Cluster from *Cluster details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/clusters/24.png?width=25pc&classes=border,shadow)

## Delete Cluster
To delete the Cluster, do the following:
- identify this unnecessary Cluster on the *Clusters page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Cluster deletion on the next opened *Confirmation window*. 

After these steps, the selected Cluster will be deleted after a few minutes.  

Also, you can delete the Cluster from *Cluster details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/clusters/22.png?width=25pc&classes=border,shadow)



