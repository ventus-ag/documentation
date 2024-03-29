---
title: Snapshots
weight: 30
---
___
On this page, you can find an explanation of how to create, edit, delete Snapshots and how to create Volumes from the Snapshots in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Snapshots page](#snapshots-page)
  - [Create Snapshot](#create-snapshot)
  - [Create Volume from Snapshot](#create-volume-from-snapshot)
  - [Create VM from Snapshot](#create-vm-from-snapshot)
  - [Create image from Snapshot](#create-image-from-snapshot)
  - [Edit Snapshot ](#edit-snapshot)
  - [Delete Snapshot](#delete-snapshot)

## Snapshots page
To get to the *Snapshots page*, select **Storage** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Snapshots TAB**:
![](../../../assets/images/vol/1.png?width=15pc&classes=border,shadow) 
![](../../../assets/images/snap/1.png?width=30pc&classes=border,shadow)  

On this page you can find all created Snapshots with the *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Snapshot:
![](../../../assets/images/snap/2.png?classes=border,shadow)

**Actions** icon opens the next list of available management actions:
- *Create volume* - this option is used to create a Volume from the selected Snapshot;
- *Edit* - this option is used to change Name and/or Description of the selected Snapshot;
- *Delete* - this option is for the Snapshot removing.

There are two ways to *create*, *edit* and *delete* Snapshots:
1. from the *Snapshots page*;
2. from the *SNAPSHOTS TAB* on the *Virtual Machine details page*.

In this article we will explain the first way - to manage Snapshots from the *Snapshots page*. Information about the second one you can find in the next article - [VM's Snapshots](https://docs.ventuscloud.eu/products/storage/manage-snapshots/).  

## Create Snapshot
To create new Snapshot from the *Snapshots page*, do the following:
- go to the *Snapshots page* and click the *CREATE SNAPSHOT* icon in the upper left corner;
- fill in the form on the next opened *Create Snapshot window* and click on the CREATE icon:

![](../../../assets/images/snap/3.png?width=35pc&classes=border,shadow) 
  - *Name* - set a name for the Snapshot;
  - *Description* - set a description for the Snapshot;
  - *Volume* - select volume from what you want to create a Snapshot.

{{% notice warning %}}
Snapshot, created from the volume with "in-use", status can contain corrupted data.
{{% /notice %}}  

After these steps, the newly created Snapshot will be added to the *Snapshots page*:
![](../../../assets/images/snap/4.png?classes=border,shadow)

Now, if you attach the Volume, from which this Snapshot was created,  to the Virtual Machine - this Snapshot will be displayed on the *SNAPSHOTS TAB* on this *Virtual Machine details page*:
![](../../../assets/images/snap/5.png?classes=border,shadow)

Also, new Snapshot can be created from the *SNAPSHOTS TAB* on the *Virtual Machine details page*, how to do this, please, see the article - [VM's Snapshots](https://docs.ventuscloud.eu/products/storage/manage-snapshots/).

## Create Volume from Snapshot
To create a Volume from the selected Snapshot, do the following:
- identify Snapshot from which you want to create a Volume on the *Snapshots page*;
- click on the **Actions** icon and select the **Create volume** in the list of available options;
- fill in the form on the next opened *Create volume from snapshot window* and click on the CREATE icon:

![](../../../assets/images/snap/7.png?width=35pc&classes=border,shadow)
  - *Name* - set a name for the Volume;
  - *Description* - set a description for the Volume.

After these steps, the newly created Volume will be added to the *Volumes page* with the status *available*:
![](../../../assets/images/snap/8.png?classes=border,shadow)

How to manage Volumes, you can find in the next articles: [Volumes](https://docs.ventuscloud.eu/products/storage/volumes/), [VM's Volumes](https://docs.ventuscloud.eu/products/storage/manage-volumes/).  

## Create VM from Snapshot
To create Virtual Machine from Snapshot do the following:
- open the *Virtual Machines page* - select the **Virtual Machines** from the VIRTUAL DATACENTER block in the *side-bar menu*:

![](../../../assets/images/vms/1.png?width=15pc&classes=border,shadow)  
- click on the CREATE VM icon in the upper left corner of the *Virtual Machines page*;
- fill in the form on the next opened *Create Virtual Machine window* and click on the CREATE icon:
![](../../../assets/images/tutorials/0-8.png?width=30pc&classes=border,shadow)

After these steps, the newly created VM will be added to the *Virtual Machine page* with the status ACTIVE.

To find more information about Virtual Machines and how to connect to them, please, see next articles - [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/), [Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/). 

## Create image from Snapshot
The Cloud Console functionality allows to upload custom Images to the system, which will be available for all resources in the current Project.

To find full workflow, of creating a custom Image from Snapshot, please see the article - [Create Image from Snapshot](https://docs.ventuscloud.eu/products/images/image-from-snapshot/).

## Edit Snapshot 
To edit the Snapshot from the *Snapshots page*, do the following:
- identify Snapshot, that you want to edit, on the *Snapshots page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Snapshot Name or/and Description on the next opened *Edit Snapshot window* and click on the SAVE icon.

After these steps, the selected Snapshot will be updated.  

Edit Snapshot you can also from the *SNAPSHOTS TAB* on the *Virtual Machine details page*, how to do this, please, see the article - [VM's Snapshots](https://docs.ventuscloud.eu/products/storage/manage-snapshots/).


## Delete Snapshot
To delete the Snapshot from the *Snapshots page*, do the following:
- identify this unnecessary Snapshot on the *Snapshots* *page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Snapshot deletion on the next opened *Confirmation window*.

After these steps, the selected Snapshot will be deleted.

Delete Snapshot you can also from the *SNAPSHOTS TAB* on the *Virtual Machine details page*, how to do this, please, see the article - [VM's Snapshots](https://docs.ventuscloud.eu/products/storage/manage-snapshots/).
