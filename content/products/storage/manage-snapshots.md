---
title: VM's Snapshots
weight: 32
---
___
On this page, you can find an explanation of how to manage Snapshots, related to the selected Virtual Machine, from the *Virtual Machine details page* in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [VM's SNAPSHOTS TAB](#vms-snapshots-tab)
  - [Create Snapshot](#create-snapshot)
  - [Edit Snapshot ](#edit-snapshot)
  - [Delete Snapshot](#delete-snapshot)

## VM's SNAPSHOTS TAB
To find all Snapshots, related to the selected Virtual Machine, you need:
- open the *Virtual Machines page* - for this select the **Virtual Machines** from the VIRTUAL DATACENTER block in the *side-bar menu*:

![](../../../assets/images/conn-lin/7.png?width=15pc&classes=border,shadow)

- open the *Virtual Machine details page* - for this click on the **Name** of the corresponding Virtual Machine: 

![](../../../assets/images/conn-lin/8.png?classes=border,shadow)

- open the *SNAPSHOTS page of this VM* - for this click on the SNAPSHOTS TAB:

![](../../../assets/images/snap/9.png?width=25pc&classes=border,shadow) 

On this page you can find all Snapshots, related to the corresponding VM, with the *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Snapshot: 
![](../../../assets/images/snap/10.png?classes=border,shadow)   

**Actions** icon opens the next list of available management actions:
- *Edit* - this option is used to change Name and/or Description of the selected Snapshot;
- *Delete* - this option is for the Snapshot removing.

There are two ways to *create*, *edit* and *delete* Snapshots:
1. from the *Snapshots page*;
2. from the *SNAPSHOTS TAB* on the *Virtual Machine details page*.

In this article we will explain the second way - to manage Snapshots from the *SNAPSHOTS TAB* on the *Virtual Machine details page*. Information about the first one you can find in the next article - [Snapshots](https://docs.ventuscloud.eu/products/storage/snapshots/).    

## Create Snapshot
To create new Snapshot from the *SNAPSHOTS TAB* on the *Virtual Machine details page*, do the following:
- go to the *SNAPSHOTS TAB* and click the *CREATE SNAPSHOT* icon in the upper left corner;
- fill in the form on the next opened *Create Snapshot window* and click on the CREATE icon:

![](../../../assets/images/snap/11.png?width=35pc&classes=border,shadow)
  - *Name* - set a name for the Snapshot;
  - *Description* - set a description for the Snapshot;
  - *Volume* - select volume from what you want to create a Snapshot.

{{% notice warning %}}
Snapshot, created from the volume with "in-use" status, can contain corrupted data.
{{% /notice %}}  

After these steps, the newly created Snapshot will be added to the *SNAPSHOTS TAB* on the *Virtual Machine details page*:
![](../../../assets/images/snap/12.png?classes=border,shadow)

Also, this Snapshot will be displayed on the *Snapshots page*:
![](../../../assets/images/snap/13.png?classes=border,shadow)

Create Snapshot you can also from the *Snapshots page*, how to do this, please, see the article - [Snapshots](https://docs.ventuscloud.eu/products/storage/snapshots/).

## Edit Snapshot 
To edit the Snapshot from the *SNAPSHOTS TAB* on the *Virtual Machine details page*, do the following:
- identify Snapshot, that you want to edit, on the *SNAPSHOTS TAB*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Snapshot Name or/and Description on the next opened *Edit Snapshot window* and click on the SAVE icon.

After these steps, the selected Snapshot will be updated.

Edit Snapshot you can also from the *Snapshots page*, how to do this, please, see the article - [Snapshots](https://docs.ventuscloud.eu/products/storage/snapshots/).

## Delete Snapshot
To delete the Snapshot from the *SNAPSHOTS TAB* on the *Virtual Machine details page*, do the following:
- identify this unnecessary Snapshot on the *SNAPSHOTS TAB*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Snapshot deletion on the next opened *Confirmation window*.

After these steps, the selected Snapshot will be deleted.

Delete Snapshot you can also from the *Snapshots page*, how to do this, please, see the article - [Snapshots](https://docs.ventuscloud.eu/products/storage/snapshots/).
