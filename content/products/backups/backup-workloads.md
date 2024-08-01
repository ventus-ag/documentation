---
title: Backup Workloads
weight: 1
---
___
On this page, you can find an explanation of how to create, edit, delete Backup Workload and instructions for other steps to manage Backup Workload in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Backup Workloads page](#backup-workloads-page)
  - [Create Backup Workload](#create-backup-workload)
  - [Workload details page](#workload-details-page)
  - [Edit Backup Workload](#edit-backup-workload)
  - [Delete Backup Workload](#delete-backup-workload)
  
{{% notice note %}}
Please be aware that the Backup feature in the Cloud Console is currently in beta. This means it has not been fully tested across all use cases but aims to provide a user-friendly way to manage backups for your VMs. If you’re willing to accept the associated risks of using a beta service, you’re welcome to proceed. Rest assured, customer support is readily available for any questions or issues you may encounter.  
{{% /notice %}}

## Introduction
A Backup Workload is a task that ensures the safety of one or more Virtual Machines according to a defined policy. 
The workload policy definition declares the frequency and retention required for the workload. 

You can create as many backup workloads as you need, but each VM can only be included in one workload.

## Backup Workloads page
To get to the *Backup Workloads page*, select the **Backups** from the VIRTUAL DATACENTER block in the *side-bar menu*:
![](../../../assets/images/backups/1.png?width=15pc&classes=border,shadow) 

On this page you can find all created Backup Workloads in the current Project, with the *Create button, Search bar* and *Actions icon*, which opens a list of available management actions for the selected workload:
![](../../../assets/images/backups/2.png?classes=border,shadow)

**Actions** icon opens the next list of available management actions:  
- *Edit* - this option is used to reconfigure the policy and schedule of the backup workload;      
- *Delete* - this option is for workload removing;  

Additionally, from this page, you can navigate to the detail page of each workload by clicking on its name. There, you will find detailed information about its policy and schedule and gain access to backup and restore options, among other management actions for the selected workload. More information about the details page will be provided in the following sections.   
![](../../../assets/images/backups/4.png?classes=border,shadow)

## Create Backup Workload

{{% notice note %}}
You can create as many backup workloads as you need, but each VM can only be included in one workload.
{{% /notice %}}

To create new Backup Workload, do the following:
- open the *Backup Workload page* and click on the CREATE WORKLOAD icon in the upper left corner;
- fill in the form on the next opened *Create Workload window*:

![](../../../assets/images/backups/3.png?width=35pc&classes=border,shadow)
  - *Name* - set a name for the Workload; 
  - *Description* - set a description for the Workload;  
  - *Instances* - specify one or more instances to include in the workload. Ensure that none of the selected instances are already part of another workload;   
  - *Backup Workload Type* - select between Serial or Parallel workload type.   
    Serial - runs backups in specific order;   
    Parallel - runs backups simultaneously.  
  - *Retention Policy Type* - select your retention method: either by the "number of backups to keep" or the "number of days to retain" each backup;  
  - *Retention Value* - set either the "number of incremental backups to keep" or the "number of days to retain backups", depending on the chosen Retention Policy Type;  
  - *Full backup interval* - choose how often to perform a full backup:
    - Always full - perform a full backup every time;  
    - Never full - only perform incremental backups;  
    - After number of incremental backups - specify the number of incremental backups after which a full backup will be performed.
  - *Scheduler Settings* - configure the scheduling of backups:
    - Enable Scheduler - check this option to activate the backup schedule;   
    - Start and End Date - define the start and end dates for the backup schedule;  
    - Time for Incremental Backups - specify the UTC time to start incremental backups;  
    - Interval - determine how frequently backups should occur.

After these steps, the newly created Workload will be added to the *Backup Workload page* and you can click on its name to navigate to the *Workload details page* to view all necessary information about it, including created backups and assigned VMs, initiate a backup outside the schedule, and access each backup's details page. More information about the *Workload details page* will be provided in the following sections.   

## Workload details page
To open the *Backup Workload details page*, click on the **Name** of the corresponding workload:
![](../../../assets/images/backups/5.png?classes=border,shadow)

This action will redirect you to the *Backup Workload details page*, where you can find panel with available **quick actions** on the selected workload and 3 tabs:
![](../../../assets/images/backups/6.png?width=35pc&classes=border,shadow)

**WORKLOAD INFO TAB** - shows the workload's general information, such as workload type and retention policy type; schedule details; and storage usage, which includes the count and memory usage of full and incremental backups:
![](../../../assets/images/backups/7.png?classes=border,shadow)
  
**ASSIGNED VM's TAB** - lists all the Virtual Machines assigned to this workload. These VMs will have backups created according to the workload's schedule, allowing for future restoration from any of these backups:  
![](../../../assets/images/backups/8.png?classes=border,shadow)

Clicking on a VM name will navigate you to the *VM details page*. More information about it you can find here - [Virtual Machine details page](https://docs.ventuscloud.eu/products/compute/virtual-machines/#virtual-machine-details-page):
  
**CREATED BACKUPS TAB** - shows all backups created according to the workload's schedule for the VMs assigned to this workload:
![](../../../assets/images/backups/9.png?classes=border,shadow)

Clicking on a Backup name will navigate you to the *Backup details page*, where you can find all necessary information about it and restore the corresponding VM. More information about it will be provided in the following sections.   

## Edit Backup Workload
To edit the Backup Workload, do the following:
- identify Workload, that you want to edit, on the *Backup Workloads page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update all desired workload settings, including name, assigned VMs, retention policy and schedule on the next opened *Edit Workload window*, and click on the EDIT icon: 
  
![](../../../assets/images/backups/10.png?width=35pc&classes=border,shadow)

After these steps, the selected Workload will be updated.  

Also, you can edit the Workload from the *Workload details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/backups/11.png?width=30pc&classes=border,shadow)

## Delete Backup Workload
To delete the Backup Workload, do the following:
- identify this unnecessary Workload on the *Backup Workloads page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Workload deletion on the next opened *Confirmation window*.

After these steps, the selected Workload will be deleted.  

Also, you can delete the Workload from the *Workload details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/backups/12.png?width=30pc&classes=border,shadow)
