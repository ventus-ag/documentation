---
title: Virtual Machines
weight: 10
---
___
On this page, you can find an explanation of how to create, resize, delete Linux and Windows Virtual Machine, and instructions for other steps to manage Virtual Machines in Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Virtual Machines page](#virtual-machines-page)
  - [Create Linux Virtual Machine](#create-linux-virtual-machine)
  - [Create Windows Virtual Machine](#create-windows-virtual-machine)
  - [Virtual Machine details page](#virtual-machine-details-page)
  - [Download RDP File](#download-rdp-file)
  - [Associate/Disassociate Floating IP](#associatedisassociate-floating-ip)
  - [Edit Virtual Machine](#edit-virtual-machine)
  - [Resize Virtual Machine](#resize-virtual-machine)
  - [Delete Virtual Machine](#delete-virtual-machine)


## Virtual Machines page 
{{% notice note %}}
In the Cloud Console you can create Windows and Linux Virtual Machines from official and custom images, snapshots or volumes.
{{% /notice %}}
To get to the *Virtual Machines page*, select the **Virtual Machines** from the VIRTUAL DATACENTER block in the *side-bar menu*:
![](../../../assets/images/vms/1.png?width=15pc&classes=border,shadow)  

On this page you can find all created Virtual Machines in the current Project of the selected Organization, with the *Create button, Search bar* and *Actions icon*, which opens a list of available management actions for the selected VM:
![](../../../assets/images/vms/2.png?classes=border,shadow)   

**Actions** icon opens the next list of available management actions:  
- *Associate Floating IP* - this option is used to make the VM publicly available if it was created in the internal network;  
- *Start* - this option is used to start the VM if it was stopped;   
- *Stop* - this option is used to stop the VM;  
- *Soft reboot* - this option is used a graceful shut down and restart of the VM;  
- *Edit* - this option is used to change VM's name;  
- *Resize* - this option is used to change the Flavor for the VM;  
- *Delete* - this option is for VM removing;  
- *Remote console* - this option is used to use remote console for VM;  
- *Download RDP file* - this option is available only for Windows VMs and is used to download RDP file for the remote connection to the Windows VMs.  

## Create Linux Virtual Machine
To create new Linux VM, do the following:
- go to the *Virtual Machines page* and click on the CREATE VM icon in the upper left corner;
- fill in the form on the next opened *Create Virtual Machine window* and click on the CREATE icon:
![](../../../assets/images/vms/3.png?width=30pc&classes=border,shadow)
  - *Name* - set a name for the VM;  
  - *Source* - choose the source which you want to use for VM creating: image, volume or snapshot;  
    by default, "Image" is pre-selected;    
  - *OS Platform* - choose the desired OS Platform for your VM: Linux or Windows (in this example we will create the Linux VM);   
    by default, "Linux" is pre-selected;   
  - *Linux Distribution* - if in the previous step, you choose the Linux OS, next you need to choose what Linux distribution to use for your VM;   
    by default, "Ubuntu" is pre-selected;   
  - *Image Version*/*Volume name*/*Snapshot name* - set the name or ID of the previously selected Source for VM creating (Image Version, Volume name or Snapshot name);   
  - *Flavor* - select the size for new VM;   
    by default, "VC-4 (2 vCPUs, 4 GiB memory)" is pre-selected;   
  - *Key pair* - this field is necessary only for Linux VMs; select here the SSH Key that was previously created on the *SSH Keys page* or create a new one, which you will use to connect to the Linux VM;  
    if you have only one created SSH Key, it will be pre-selected by default;   
  - *Networks* - choose one or more networks;   
    by default, "public" network is pre-selected;   
  - *Firewalls*- choose what collection of network access rules will control the traffic to this VM;     
    by default, "default" Firewall is pre-selected;   
    default Firewall allows access to the Internet from the VMs, but denies almost all access on the VMs from outside, except for objects belonging to the same default Firewall.   
      >**NOTE:** To connect to the selected **Linux Virtual Machine** remotely via SSH, you need to add an additional Firewall with a rule, that will allow incoming traffic to TCP port 22 (like shown below) - to find additional information about this, please see the article **[Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/)**;
  
  ![](../../../assets/images/fw/17.png?width=35pc&classes=border,shadow) 

  - *Tags* - this field is optional; use it if you need to set some tags for the VM;    
  - *Volume size (GB)* - provide the preferred disk size for the VM, it can be specified in the range from 10 GB to 1000 GB. Minimal available size for Linux VMs - 10 GB; for Windows VMs - 50 GB;   
  by default, "50 GB" is pre-selected;    
  and also just below this field you can make a mark ***for auto-deleting volume*** when the VM is terminated;    

After these steps, the newly created Linux VM will be added to the *Virtual Machine page* with the status ACTIVE:
![](../../../assets/images/vms/6.png?classes=border,shadow)


## Create Windows Virtual Machine
To create new Windows VM, do the following:
- go to the *Virtual Machines page* and click on the CREATE VM icon in the upper left corner;
- fill in the form on the next opened *Create Virtual Machine window* and click on the CREATE icon:
![](../../../assets/images/vms/7.png?width=30pc&classes=border,shadow)
  - *Name* - set a name for the VM;  
  - *Source* - choose the source which you want to use for VM creating: image, volume or snapshot;  
    by default, "Image" is pre-selected;  
  - *OS Platform* - choose the desired OS Platform for your VM: Linux or Windows (in this example we will create the Windows VM);  
    by default, "Linux" is pre-selected;  
  - *Image Version*/*Volume name*/*Snapshot name* - set the name or ID of the previously selected Source for VM creating (Image Version, Volume name or Snapshot name);  
  - *Flavor* - select the size for new VM;  
    by default, "VC-4 (2 vCPUs, 4 GiB memory)" is pre-selected;  
  - *Password* - this field is necessary only for Windows VMs;come up with the root password (it must contain at least one Latin letter in upper case, one Latin letter in lower case, digit, special character, and must be at least 8 characters long);  
  - *Confirm password;*  
  - *Networks* - choose one or more networks;  
    by default, "public" network is pre-selected;  
  - *Firewalls* - choose what collection of network access rules will control the traffic to this VM;   
    by default, "default" Firewall is pre-selected;  
    default Firewall allows access to the Internet from the VMs, but denies almost all access on the VMs from outside, except for objects belonging to the same default Firewall. 
    >**NOTE:** To connect to the selected **Windows Virtual Machine** remotely via RDP you need to add an additional Firewall with a rule that will allow incoming traffic to TCP port 54000 like shown below - to find additional information about this, please see the article **[Access Windows VM](https://docs.ventuscloud.eu/products/compute/connect-windows-vm/)**;
  
  ![](../../../assets/images/fw/18.png?width=35pc&classes=border,shadow)

  - *Tags* - this field is optional; use it if you need to set some tags for the VM;   
  - *Volume size (GB)* - provide the preferred disk size for the VM, it can be specified in the range from 10 GB to 1000 GB. Minimal available size for Linux VMs - 10 GB; for Windows VMs - 50 GB;  
  by default, "50 GB" is pre-selected;   
and also just below this field you can make a mark ***for auto-deleting volume*** when the VM is terminated;      

After these steps, the newly created Windows VM will be added to the *Virtual Machine page* with the status ACTIVE:
![](../../../assets/images/vms/8.png?classes=border,shadow)

## Virtual Machine details page
To open the *Virtual Machine details page*, click on the **Name** of the corresponding Virtual Machine:
![](../../../assets/images/vms/10.png?classes=border,shadow)

This action will redirect you to the *Virtual Machine details page*, where you can find:
- VM **details area** with actual information about it - name, ID, public IP, region, status, memory and image that was used for VM's creation:

![](../../../assets/images/vms/13.png?width=25pc&classes=border,shadow)

- panel with available **quick actions**:
![](../../../assets/images/vms/11.png?width=15pc&classes=border,shadow)
  - *Start* - this option is used to start the VM if it was stopped; 
  - *Reboot* - this option is used to reboot power cycles the VM;
  - *Stop* - this option is used to stop the VM;
  - *Edit* - this option is used to change VM's name;
  - *Remote console* - this option is used to use remote console for VM;
  - **Additional Actions:**
    - *Resize* - this option is used to change the VM flavor;
    - *Download RDP File* - this option is used to download RDP file for the Windows VM;
    - *Delete* - this option is for VM removing;

- transition to the NETWORKS & SECURITY, VOLUMES, SNAPSHOTS and LOG pages related to this VM:
![](../../../assets/images/networks/net-16.png?width=25pc&classes=border,shadow) 

**NETWORKS & SECURITY TAB** - opens the *Networks & Security page* where you can find all available Interfaces and Security Groups (Firewalls) of corresponding VM, add new Interface or/and Firewall, associate Floating IP and manage this services.  
  ![](../../../assets/images/vms/14.2.png?classes=border,shadow)  

To find additional information about Networking and Security and how to manage them through this TAB use the articles: [VM's Firewalls](https://docs.ventuscloud.eu/products/security/manage-firewalls/), [VM's Networks and Interfaces](https://docs.ventuscloud.eu/products/networking/manage-networks/).

**VOLUMES TAB** - opens the *Volumes page* where you can find all attached volumes of corresponding VM, and also attache new one and manage them.  
![](../../../assets/images/vms/15.2.png?classes=border,shadow)  

To find additional information about volumes and how to manage them through this TAB use the articles: [VM's Volumes](https://docs.ventuscloud.eu/products/storage/manage-volumes/). 

**SNAPSHOTS TAB** - opens the *Snapshots page* where you can find all available snapshots of corresponding VM, create new one and manage them.  
![](../../../assets/images/vms/16.2.png?classes=border,shadow)

To find additional information about snapshots and how to manage them through this TAB use the articles: [VM's Snapshots](https://docs.ventuscloud.eu/products/storage/manage-snapshots/).
  
**LOG TAB** - opens the *Log page* where you can find VM's logs.
![](../../../assets/images/vms/17.2.png?classes=border,shadow)

## Download RDP File

{{% notice note %}}
This option is available only for Windows VMs and is used to download RDP file for the remote connection to the Windows VMs.
{{% /notice %}}

To download RDP for the remote connection to the Windows Virtual Machine, do the following:
- identify Windows Virtual Machine, for what  you want to download RDP file on the *Virtual Machines page*;
- click on the **Actions** icon and select the **Download RDP file** in the list of available options.

After these steps, the RDP File of the selected Windows Virtual Machine will be downloaded.  
Also, you can download RDP file from *Virtual Machine details page*, by clicking on the appropriative **quick actions** icon there.

## Associate/Disassociate Floating IP

{{% notice note %}}
This option is available only for VMs created in the internal network with an configured external Router.
{{% /notice %}}

To associate Floating IP with the Virtual Machine, do the following:
- ensure that you have configured Router with enabled external gateway, which is attached to your internal Network.
  To find information about how to create and configure Router use the article [Routers](https://docs.ventuscloud.eu/products/networking/routers/);
- ensure that you have created Floating IP and it isn't already associated with other cloud Resources;
  To find information about how to create Floating IP use the article [Floating IPs](https://docs.ventuscloud.eu/products/networking/floating-ips/);
- identify Virtual Machine created in the internal network, that you want to make publicly available from the Internet on the *Virtual Machines page*;
- click on the **Actions** icon and select the **Associate Floating IP** in the list of available options;
![](../../../assets/images/vms/18.png?classes=border,shadow)
- choose one of the available internal interfaces of your VM and one of the previously created Floating IP that you want to attach to the selected interface on the opened *Associate floating IP* and click on the ASSOCIATE icon:  

![](../../../assets/images/vms/20.png?width=35pc&classes=border,shadow)

After these steps, the selected Virtual Machine will be publicly available:  
![](../../../assets/images/vms/21.png?classes=border,shadow)

Now, if you want to close the access from Internet to this VM again, do the following:  
- click on the **Actions** icon and select the **Disassociate Floating IP**;
- confirm your action on the next opened *Confirmation window* by clicking on the DISASSOCIATE icon. 

After these steps, the selected Virtual Machine will be again publicly unavailable.

To find additional information about Floating IPs and VM's Interfaces use the articles: [Floating IPs](https://docs.ventuscloud.eu/products/networking/floating-ips/), [VM's Networks and Interfaces](https://docs.ventuscloud.eu/products/networking/manage-networks/).

Associate/disassociate Floating IPs you can also from the *NETWORKS & SECURITY TAB* on the *Virtual Machine details page*, how to do this, please, see the article - [VM's Networks and Interfaces](https://docs.ventuscloud.eu/products/networking/manage-networks/).

## Edit Virtual Machine
To edit the Virtual Machine, do the following:
- identify Virtual Machine, that you want to edit, on the *Virtual Machines page*;
- click on the **Actions** icon  and select the **Edit** in the list of available options;
- update the Virtual Machine Name on the opened *Edit Virtual Machines window*  and click on the SAVE icon.

After these steps, the selected Virtual Machine will be updated.

Edit Virtual Machine you can also from *Virtual Machine details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/vms/22.png?width=10pc&classes=border,shadow)

## Resize Virtual Machine
To resize the Virtual Machine, do the following:
- identify Virtual Machine, that you want to resize, on the *Virtual Machines page*;
- click on the **Actions** icon and select the **Resize** in the list of available options;
- choose new flavor for the Virtual Machine on the next opened *Resize Virtual Machines window* and click on the SAVE icon;
- verify resize by clicking again on the **Actions** icon and select additional option - **Confirm resize**

When the VM's status changes from RESIZE to VERIFY_RESIZE, you can confirm or revert your action, just click again on the **Actions** icon and select one of the additional options - **Confirm resize** or **Revert resize**:
![](../../../assets/images/vms/9-vm.png?classes=border,shadow)

If you confirm resizing, the selected virtual machine will be resized after a few minutes and its status will be ACTIVE. 

Resize Virtual Machine you can also from *Virtual Machine details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/vms/23.png?width=10pc&classes=border,shadow)

## Delete Virtual Machine
To delete the Virtual Machine, do the following:
- identify this unnecessary Virtual Machine on the *Virtual Machines page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Virtual Machine deletion on the next opened *Confirmation window*.

After these steps, the selected Virtual Machine will be deleted.  

Delete Virtual Machine you can also from *Virtual Machine details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/vms/24.png?width=10pc&classes=border,shadow)







