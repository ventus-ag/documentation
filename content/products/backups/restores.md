---
title: Restores
weight: 5
---
___
On this page, you can find an explanation of what is the Restore in the Cloud Console, how to recover backed-up Virtual Machines and instructions for other steps to manage Restores in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Restores page](#restores-page)
  - [Initiate Restore](#initiate-restore)
  - [Cancel Restore](#cancel-restore)
  - [Delete Restore](#delete-restore)
  
{{% notice note %}}
Please be aware that Backup and Restore features in the Cloud Console is currently in beta. This means it has not been fully tested across all use cases but aims to provide a user-friendly way to restore your VMs from backups. If you’re willing to accept the associated risks of using a beta service, you’re welcome to proceed. Rest assured, customer support is readily available for any questions or issues you may encounter.
{{% /notice %}}

## Introduction
Restore in the Cloud Console is the procedure used to recover backed-up Virtual Machines (VMs) from a saved backup. This process allows you to bring VMs back to their original state using the available backup data.

{{% notice note %}}
The restore process will bring back all selected VMs to the same state as when they were backed up.
{{% /notice %}}

So, to initiate a Restore, you first need to have an available Backup. More information about backups can be found here - [Backups](https://docs.ventuscloud.eu/products/backups/backups/)

## Restores page

To get to the *Restores page* do the following:   
1) Open the *Backup Workloads page* - select the **Backups** from the VIRTUAL DATACENTER block in the *side-bar menu*:    
![](../../../assets/images/backups/1.png?width=15pc&classes=border,shadow) 

2) Navigate to the *Workload details page* by clicking on the desired workload **name**:    
![](../../../assets/images/backups/4.png?classes=border,shadow)

3) Select *CREATED BACKUPS TAB* on the opened *Workload details page*:  
![](../../../assets/images/backups/13.png?width=25pc&classes=border,shadow)

4) Navigate to the *Backup details page* by clicking on the desired backup **name**:    
![](../../../assets/images/backups/26.png?classes=border,shadow)

4) Select *RESTORES TAB* on the opened *Backup details page*:  
![](../../../assets/images/backups/27.png?width=20pc&classes=border,shadow)

On this page you can find all records of the restore operation initiated from the current Backup, with the *Restore VM button, Search bar* and *Actions icon*, which opens a list of available management actions for the selected Restore:
![](../../../assets/images/backups/28.png?classes=border,shadow)

**Actions** icon opens the next list of available management actions:  
- *Cancel restore* - this option is used to stop ongoing restore;      
- *Delete restore* - this option is used for the restore removing.

## Initiate Restore 

{{% notice note %}}
Restore can only be initiated if current Backup and Workload are in available states.
{{% /notice %}}

To restore VMs from Backup, do the following:

- open the *Restores TAB* or *Backuped VMs TAB* on the *Backup details page* and click on the RESTORE VM icon in the upper left corner;
- fill in the form on the next opened *Restore from Backup window*:
  - *Name* - assign a name to the Restore record;  
  - *Description* - provide a description for the Restore record;  
  - *Instances* - if the backup includes multiple VMs, select which ones you want to restore.

![](../../../assets/images/backups/31.png?width=35pc&classes=border,shadow). 

After these steps, the newly created Restore record will be added to the *Restores TAB* and  you can navigate to the *Virtual Machines page* to see that the restored VM is being created and will be in ACTIVE status in a few minutes.

The restore process will bring back all selected VMs to the same state as when they were backed up. They will:  
- be created in the same project;
- connect to the same network;
- have the same image and flavor;
- use the same key pair.

## Cancel Restore
To cancel the ongoing Restore, do the following:
- identify Restore, that you want to cancel, on the *Restores TAB* of the *Backup details page*;
- click on the **Actions** icon and select the **Cancel restore** in the list of available options;
- confirm your action on the next opened *Confirmation window*. 
  
![](../../../assets/images/backups/29.png?classes=border,shadow)

After these steps, the selected Restore will be canceled.

## Delete Restore

{{% notice note %}}
Deleting a Restore will only remove the record of the restore operation. The restored VMs will not be affected or deleted.
{{% /notice %}}

To delete the Restore, do the following:
- identify this unnecessary Restore on the *Restore TAB* of the *Backup details page*;
- click on the **Actions** icon and select the **Delete restore** in the list of available options;
- confirm the Restore deletion on the next opened *Confirmation window*.

![](../../../assets/images/backups/30.png?classes=border,shadow)

After these steps, the selected Restore will be deleted.  
