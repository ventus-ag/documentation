---
title: Backups
weight: 5
---
___
On this page, you can find an explanation of how to mange already created Backups, create Backup on demand and by schedule, multi-delete Backups and instructions for other steps to manage Backups in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Backups page](#backups-page)
  - [Create Backup](#create-backup)
  - [Backup details page](#backup-details-page)
  - [Cancel Backup](#cancel-backup)
  - [Delete Backup](#delete-backup)
  - [Multi-Delete Backups](#multi-delete-backups)
  
{{% notice note %}}
Please be aware that Backup and Restore features in the Cloud Console is currently in beta. This means it has not been fully tested across all use cases but aims to provide a user-friendly way to manage backups for your VMs. If you’re willing to accept the associated risks of using a beta service, you’re welcome to proceed. Rest assured, customer support is readily available for any questions or issues you may encounter.  
{{% /notice %}}

## Introduction
Backups in the Cloud Console refer to VM backups created within a specific Backup Workload and contain the information of all VM's that are protected by this workload. Backup Workload settings also control the number of backups by deleting oldest ones based on retention policy and creating new backups according to the schedule if it is enabled.

So, to create a backup on demand or by schedule, you first need to create a Backup Workload. More information about backup workloads you can find here - [Backup Workloads](https://docs.ventuscloud.eu/products/backups/backup-workloads/).

## Backups page

To get to the *Backups page* do the following:   
1) Open the *Backup Workloads page* - select the **Backups** from the VIRTUAL DATACENTER block in the *side-bar menu*:    
![](../../../assets/images/backups/1.png?width=15pc&classes=border,shadow) 

2) Navigate to the *Workload details page* by clicking on the desired workload **name**:    
![](../../../assets/images/backups/4.png?classes=border,shadow)

3) Select *CREATED BACKUPS TAB* on the opened *Workload details page*:  
![](../../../assets/images/backups/13.png?width=25pc&classes=border,shadow)

On this page, you can find all backups within the selected workload, whether they are automatically created by the workload scheduler or created on demand manually when the scheduler is deactivated. You will also find the *Create button*, *Search bar*, and *Actions icon*, which opens a list of available management actions for the selected backup:
![](../../../assets/images/backups/14.png?classes=border,shadow)

**Actions** icon opens the next list of available management actions:  
- *Cancel* - this option is used to stop ongoing backups;      
- *Delete* - this option is used for the backup removing;  
- *Restore from backup* - this option is used to bring back all VMs from the backup in the same state as they were backed up.

Additionally, from this page, you can navigate to the detail page of each backup by clicking on its **name**. There, you will find detailed information about backup and gain access to the restore options, among other management actions for the selected backup. More information about the *Backup details page* will be provided in the following sections.   
![](../../../assets/images/backups/15.png?classes=border,shadow)

## Create Backup 

{{% notice note %}}
Backups are created automatically according to the workload schedule.   
However, if needed or if the scheduler is deactivated, it is also possible to create backup manually on demand.
{{% /notice %}}

{{% notice note %}}
Manually Backups can only be taken if the workload is in an available state.
{{% /notice %}}

To create new Backup on demand manually, do the following:
- open the *Backups TAB* on the *Workload details page* and click on the CREATE BACKUP icon in the upper left corner;
- fill in the form on the next opened *Create Backup window*:

![](../../../assets/images/backups/16.png?width=35pc&classes=border,shadow)
  - *Name* - set a name for the Backup; 
  - *Description* - set a description for the Backup;  

After these steps, the newly created Backup will be added to the *Backups TAB* and you can click on its **name** to navigate to the *Backup details page* to view all necessary information about it, including assigned VMs and created restores. More information about this page will be provided in the following sections.   

## Backup details page
To open the *Backup details page*, click on the **Name** of the corresponding backup on the *Backups TAB*:
![](../../../assets/images/backups/15.png?classes=border,shadow)

This action will redirect you to the *Backup details page*, where you can find backup **details area** with actual information about it, panel with available **quick actions** on the selected backup and **2 tabs**:
![](../../../assets/images/backups/17.png?width=35pc&classes=border,shadow)

**BACKUPED VMs TAB** - lists all protected virtual machines by this workload, that are part of the this backup:
![](../../../assets/images/backups/18.png?classes=border,shadow)

From here it is possible to restore a VM and, if it is still available, navigate to the *VM details page* by clicking on the VM **name**. More information about this page you can find here - [Virtual Machine details page](https://docs.ventuscloud.eu/products/compute/virtual-machines/#virtual-machine-details-page).
  
**RESTORES TAB** - displays a list of restores initiated from the current backup, with available actions to start a new restore, cancel, or delete an existing ones:
![](../../../assets/images/backups/19.png?classes=border,shadow)

More information about Restores you can find here - [Restores](https://docs.ventuscloud.eu/products/backups/restores/).

## Cancel Backup
To cancel the ongoing Backup, do the following:
- identify Backup, that you want to cancel, on the *Backups TAB* of the *Workload details page*;
- click on the **Actions** icon and select the **Cancel** in the list of available options;
- confirm your action on the next opened *Confirmation window*. 
  
![](../../../assets/images/backups/23.png?classes=border,shadow)

After these steps, the selected Backup will be canceled.  

{{% notice note %}}
Canceled Backups will be treated like errored Backups.
{{% /notice %}}

Also, you can cancel the Backup from the *Backup details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/backups/24.png?width=30pc&classes=border,shadow)

## Delete Backup

{{% notice note %}}
Backups will be automatically deleted by the retention policy according to the configured settings.   
However, if needed it is also possible delete backups manually on demand.
{{% /notice %}}

{{% notice note %}}
Backup can be deleted only when it is in available, error, or canceled state;   
and the current workload is in available state.
{{% /notice %}}

To delete the Backup, do the following:
- identify this unnecessary Backup on the *Backups TAB* of the *Workload details page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Backup deletion on the next opened *Confirmation window*.

![](../../../assets/images/backups/21.png?classes=border,shadow)

After these steps, the selected Backup will be deleted.  

Also, you can delete the Backup from the *Backup details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/backups/20.png?width=30pc&classes=border,shadow)

## Multi-Delete Backups

{{% notice note %}}
Backups can be deleted only when they are in available, error, or canceled state;   
and the current workload is in available state.
{{% /notice %}}

Backups multi-delete action is available only from *Workload details page*.

To delete group of Backups, do the following:
- select these unnecessary Backups on the *Backups TAB* of the *Workload details page*;
- click on the appropriative **quick actions** icon in the upper right corner;
- confirm the Backups deletion on the next opened *Confirmation window*.

![](../../../assets/images/backups/22.png?classes=border,shadow)

![](../../../assets/images/backups/25.png?width=30pc&classes=border,shadow)

After these steps, the selected Backups will be deleted.  
