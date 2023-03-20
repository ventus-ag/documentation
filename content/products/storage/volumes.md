---
title: Volumes
weight: 25
---
___
On this page, you can find an explanation of how to create, edit, delete Volumes and instructions for other steps to manage Volumes in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Volumes page](#volumes-page)
  - [Create Volume](#create-volume)
  - [Attach Volume](#attach-volume)
  - [Detach Volume](#detach-volume)
  - [Create VM from Snapshot](#create-vm-from-snapshot)
  - [Edit Volume](#edit-volume)
  - [Extend Volume](#extend-volume)
  - [Delete Volume](#delete-volume)

## Volumes page
To get to the *Volumes page*, select the **Storage** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Volumes TAB:**
![](../../../assets/images/vol/1.png?width=15pc&classes=border,shadow) 
![](../../../assets/images/vol/2.png?width=30pc&classes=border,shadow) 

On this page you can find all your own Volumes, created in the current Project, and the Volumes created during Cluster and VM creation, with the *Create button*, *Search bar* and *Actions icon* which opens a list of available management actions for the selected Volume:
![](../../../assets/images/vol/3.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions:
- *Attach* - this option is used to attach the Volume to the VM; you can attach only Volumes with state *available*;  
- *Detach* -  this option is used to detach the Volume to the VM; you can detach only Volumes with state *in-use*;  
- *Edit* - this option is used to change the Volume name;
- *Extend* - this option is used to change the Volume size; volume extension will restart the VM it is attached to;
- *Delete* - this option is for Volume deletion.

There are two ways to *attach*, *detach*, *edit* and *extend* Volumes:
1. from the *Volumes page*;
2. from the *VOLUMES TAB* on the *Virtual Machine details page*.

In this article we will explain the first way - to manage Volumes from the *Volumes page*. Information about the second one you can find in the next article - [VM's Volumes](https://docs.ventuscloud.eu/products/storage/manage-volumes/).  

## Create Volume
To create new Volume from the *Volumes page*, do the following:
- go to the *Volumes page* and click on the CREATE VOLUME icon in the upper left corner;
- fill in the form on the next opened *Create Volume window* and click on the CREATE icon:

![](../../../assets/images/vol/4.png?width=35pc&classes=border,shadow) 
  - *Name* - set a name for the Volume; if Volume was created during Cluster or VM creation, its name will be generated automatically;
  - *Description* - set a description for the Volume;
  - *Volume Type* - select Volume type from the list of available;
  - *Volume Size* - specify volume size; it can be in the range from 10 GB to 1000 GB; minimal available size 10 GB is selected by default.

After these steps, the newly created Volume will be added to the *Volumes page* with the status *available*:
![](../../../assets/images/vol/5.png?classes=border,shadow) 

Also, Volume can be created from the Snapshot.  
To find instructions how to do this, please, see the article - [Snapshots](https://docs.ventuscloud.eu/products/storage/snapshots/).

## Attach Volume
{{% notice note %}}
You can attach only Volumes with state *available*. 
{{% /notice %}}

To attach the Volume from the *Volumes page*, do the following:
- identify Volume, that you want to attach, on the *Volumes page*;
- click on the **Actions** icon  and select the **Attach** in the list of available options;
- choose VM to which you want to attach selected Volume on the next opened *Attach Volume window* and on the ATTACH icon:

![](../../../assets/images/vol/8.png?width=35pc&classes=border,shadow) 

After these steps, the Volume will be attached to the selected VM and on the *Volumes page* its status will change to *in-use:
![](../../../assets/images/vol/9.png?classes=border,shadow) 

Also, this Volume will be displayed on the *VOLUMES TAB* on the *Virtual Machine details page*:
![](../../../assets/images/vol/10.png?classes=border,shadow) 

{{% notice note %}}
If the Volume was created from the Snapshot, after attaching it to the VM, related with this Volume Snapshot will be displayed on the *SNAPSHOTS TAB* on the *Virtual Machine details page*. 
{{% /notice %}}

Attach Volume you can also from the *VOLUMES TAB* on the *Virtual Machine details page*, how to do this, please, see the article - [VM's Volumes](https://docs.ventuscloud.eu/products/storage/manage-volumes/).

## Detach Volume
{{% notice note %}}
You can detach only Volumes with state *in-use*. 
{{% /notice %}}

To detach the Volume from the *Volumes page*, do the following:
- identify Volume, that you want to detach, on the *Volumes page*;
- click on the **Actions** icon  and select the **Detach** in the list of available options;
- confirm the Volume detaching on the next opened *Confirmation window*.

After these steps, the Volume will be detached from the selected VM and on the *Volumes page* its status will change to *available*.

Detach Volume you can also from the *VOLUMES TAB* on the *Virtual Machine details page*, how to do this, please, see the article - [VM's Volumes](https://docs.ventuscloud.eu/products/storage/manage-volumes/).

## Create VM from Snapshot
{{% notice note %}}
You can Create Virtual Machines only from Volumes with state *available*. 
{{% /notice %}}

To create Virtual Machine from Volume do the following:
- open the *Virtual Machines page* - select the **Virtual Machines** from the VIRTUAL DATACENTER block in the *side-bar menu*:

![](../../../assets/images/vms/1.png?width=15pc&classes=border,shadow)  
- click on the CREATE VM icon in the upper left corner of the *Virtual Machines page*;
- fill in the form on the next opened *Create Virtual Machine window* and click on the CREATE icon:
![](../../../assets/images/tutorials/21.png?width=30pc&classes=border,shadow)

After these steps, the newly created VM will be added to the *Virtual Machine page* with the status ACTIVE.

To find more information about Virtual Machines and how to connect to them, please, see next articles - [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/), [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/). 

## Edit Volume
To edit the Volume from the *Volumes page*, do the following:
- identify Volume, that you want to edit, on the *Volumes page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Volume Name, Description or/and make the it bootable on the next opened *Edit Volume window* and click on the SAVE icon:

![](../../../assets/images/vol/6.png?width=35pc&classes=border,shadow)

After these steps, the selected Volume will be updated.

Edit Volume you can also from the *VOLUMES TAB* on the *Virtual Machine details page*, how to do this, please, see the article - [VM's Volumes](https://docs.ventuscloud.eu/products/storage/manage-volumes/).

## Extend Volume
To extend the Volume from the *Volumes page*, do the following:
- identify Volume, that you want to extend, on the *Volumes page*;
- click on the **Actions** icon and select the **Extend** in the list of available options;
- change the Volume Size on the next opened *Extend Volume window* and click on EXTEND icon:

![](../../../assets/images/vol/7.png?width=35pc&classes=border,shadow)

After these steps, the selected Volume will be updated.

Extend Volume you can also from the *VOLUMES TAB* on the *Virtual Machine details page*, how to do this, please, see the article - [VM's Volumes](https://docs.ventuscloud.eu/products/storage/manage-volumes/).


## Delete Volume
{{% notice note %}}
You can't delete the Volume with the state *in-use,* firstly, you need to detach it. 
{{% /notice %}}

To delete the Volume, do the following:
- identify this unnecessary Volume on the *Volumes page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Volume deletion on the next opened *Confirmation window*.

After these steps, the selected Volume will be deleted.

