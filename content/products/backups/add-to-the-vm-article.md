---
title: VM
weight: 5
---
___

## Backup Virtual Machine

{{% notice note %}}
Please be aware that Backup feature in the Cloud Console is currently in beta. This means it has not been fully tested across all use cases but aims to provide a user-friendly way to manage backups for your VMs. If you’re willing to accept the associated risks of using a beta service, you’re welcome to proceed. Rest assured, customer support is readily available for any questions or issues you may encounter.  
{{% /notice %}}

Now, in the Cloud Console you have the option to set up regular backups for your virtual machines by creating a backup workload and assigning the virtual machine to it.  
The VM will be backed up according to the workload's schedule. If the schedule is turned off, you can still perform a manual one-time backup. However, to perform any backup, the VM must be assigned to a specific backup workload. 

To get to the *Backup Workloads page*, select the **Backups** from the VIRTUAL DATACENTER block in the *side-bar menu*:
![](../../../assets/images/backups/1.png?width=15pc&classes=border,shadow) 

On this page you can find all created Backup Workloads in the current Project, with the *Create button, Search bar* and *Actions icon*, which opens a list of available management actions for the selected workload.  
![](../../../assets/images/backups/5.png?classes=border,shadow)

Additionally, from this page, you can navigate to the detail page of each created workload by clicking on its **name**. There, you will find detailed information about its policy and schedule and gain access to backup and restore options, among other management actions for the selected workload:
![](../../../assets/images/backups/32.png?classes=border,shadow)

More information about backup workloads you can find here - [Backup Workloads](https://docs.ventuscloud.eu/products/backups/backup-workloads/).

## Restore Virtual Machine

{{% notice note %}}
Please be aware that Restore feature in the Cloud Console is currently in beta. This means it has not been fully tested across all use cases but aims to provide a user-friendly way to manage backups for your VMs. If you’re willing to accept the associated risks of using a beta service, you’re welcome to proceed. Rest assured, customer support is readily available for any questions or issues you may encounter.  
{{% /notice %}}

If your VM is assigned to a Backup Workload and has a successfully created Backup, you can restore it when needed with the same settings and data.  

The restore process will return the VM to its previous state, including the same project, network, image, and key pair. However, you can assign a new name and flavor to the restored VMs during the process.

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

More information about restores can be found here - [Restores](https://docs.ventuscloud.eu/products/backups/restores/).
















