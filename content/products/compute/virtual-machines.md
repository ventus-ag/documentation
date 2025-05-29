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
  - [Shutoff Virtual Machine](#shutoff-virtual-machine)
  - [Shelve Virtual Machine](#shelve-virtual-machine)
  - [Start Virtual Machine](#start-virtual-machine)
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
- *Associate Floating IP* - assigns a public IP address to the VM, making it accessible from the internet (useful if the VM is in a private network).  
- *Start* - boots the VM if it is currently shut off or shelved.   
- *Resize* - changes the VM's flavor.  
- *Edit* - allows to rename the VM anr set tags fot it.  
- *Soft reboot* - gracefully restarts the VM, similar to a standard operating system reboot.  
- *Shutoff* - stops the VM while keeping its resources (CPU, RAM) reserved on the hypervisor.
- *Shelve* - deallocates the VM and releases its resources (CPU, RAM) from the hypervisor.  
- *Delete* - permanently removes the VM.  
- *Remote console* - opens a web-based remote console to access the VM directly.  
- *Download RDP file* - available only for Windows VMs; downloads a Remote Desktop Protocol file to enable remote connection.  

## Create Linux Virtual Machine
To create new Linux VM, do the following:
- go to the *Virtual Machines page* and click on the CREATE VM icon in the upper left corner;
- fill in the form on the next opened *Create Virtual Machine window* and click on the CREATE icon:
![](../../../assets/images/vms/3.png?width=30pc&classes=border,shadow)
  - *Name* - specify a name for the virtual machine.  
  - *Source* - choose the source for creating the VM: image, volume, or snapshot;  
    by default, "image" is pre-selected.   
  - *OS Platform* - choose the operating system platform: Linux or Windows;  
    in this example we will create the Linux VM.     
  - *Linux Distribution* -  if Linux OS is selected, choose the desired distribution (e.g. Ubuntu, CentOS, etc.).  
  - *Image Version*/*Volume name*/*Snapshot name* - based on the selected source, specify the corresponding image version, volume name, or snapshot name.  
  - *Flavor* - select the size of the VM (number of vCPUs and RAM);  
    by default, "VC-4 (2 vCPUs, 4 GiB memory)" is pre-selected.     
  - *Key pair* - required for Linux VMs; choose an existing SSH key (created on the *SSH Keys* page) or create a new one to connect to the VM via SSH.   
  - *Networks* - select one or more networks to connect the VM to;  
    by default, "public" network is pre-selected.     
  - *Firewalls* -  choose what collection of network access rules will control the traffic to this VM;     
    by default, "default" Firewall is pre-selected;   
    💡 Default Firewall allows access to the Internet from the VMs, but denies almost all access on the VMs from outside, except for objects belonging to the same default Firewall.   
  - *Tags* - optional; use this field to assign tags to the VM.  
  - *Volume size (GB)* - provide the preferred disk size for the VM;  
    valid range: 10–1000 GiB;   
    minimal available size for Linux VMs - 10 GB; for Windows VMs - 50 GB;    
    by default, "50 GB" is pre-selected.  
  - *Delete Volume after VM deletion* – enable this option to automatically delete the volume when the VM is removed.  

After these steps, the newly created Linux VM will be added to the *Virtual Machine page* with the status ACTIVE:
![](../../../assets/images/vms/6.png?classes=border,shadow)

💡 To connect to the selected **Linux Virtual Machine** remotely via SSH, you need to add an additional Firewall with a rule, that will allow incoming traffic to TCP port 22 (like shown below) - to find additional instructions and information about this, please see the article **[Access Linux VM](https://docs.ventuscloud.eu/products/compute/connect-linux-vm/)**.
  
  ![](../../../assets/images/vms/35.png?width=35pc&classes=border,shadow) 

## Create Windows Virtual Machine
To create new Windows VM, do the following:
- go to the *Virtual Machines page* and click on the CREATE VM icon in the upper left corner;
- fill in the form on the next opened *Create Virtual Machine window* and click on the CREATE icon:
![](../../../assets/images/vms/7.png?width=30pc&classes=border,shadow)
  - *Name* - specify a name for the virtual machine.  
  - *Source* - choose the source for creating the VM: image, volume, or snapshot;  
    by default, "image" is pre-selected.   
  - *OS Platform* - choose the operating system platform: Linux or Windows;  
    in this example we will create the Linux VM.     
  - *Linux Distribution* -  if Linux OS is selected, choose the desired distribution (e.g. Ubuntu, CentOS, etc.).  
  - *Image Version*/*Volume name*/*Snapshot name* - based on the selected source, specify the corresponding image version, volume name, or snapshot name.  
  - *Flavor* - select the size of the VM (number of vCPUs and RAM);  
    by default, "VC-4 (2 vCPUs, 4 GiB memory)" is pre-selected.  
  - *Password* - required for Windows VMs; come up with the root password (it must contain at least one Latin letter in upper case, one Latin letter in lower case, digit, special character, and must be at least 8 characters long);  
  - *Confirm password;*  
  - *Networks* - select one or more networks to connect the VM to;  
    by default, "public" network is pre-selected.   
  - *Firewalls* - choose what collection of network access rules will control the traffic to this VM;   
    by default, "default" Firewall is pre-selected;  
    💡 Default Firewall allows access to the Internet from the VMs, but denies almost all access on the VMs from outside, except for objects belonging to the same default Firewall. 
  - *Tags* - optional; use this field to assign tags to the VM.  
  - *Volume size (GB)* - provide the preferred disk size for the VM;  
    valid range: 10–1000 GiB;   
    minimal available size for Linux VMs - 10 GB; for Windows VMs - 50 GB;    
    by default, "50 GB" is pre-selected.  
  - *Delete Volume after VM deletion* – enable this option to automatically delete the volume when the VM is removed.  

After these steps, the newly created Windows VM will be added to the *Virtual Machine page* with the status ACTIVE:
![](../../../assets/images/vms/8.png?classes=border,shadow)

💡 To connect to the selected **Windows Virtual Machine** remotely via RDP you need to add an additional Firewall with a rule that will allow incoming traffic to TCP port 54000 like shown below - to find additional instructions and information about this, please see the article **[Access Windows VM](https://docs.ventuscloud.eu/products/compute/connect-windows-vm/)**;
  
![](../../../assets/images/vms/36.png?width=35pc&classes=border,shadow)

## Virtual Machine details page
To open the *Virtual Machine details page*, click on the **Name** of the corresponding Virtual Machine:
![](../../../assets/images/vms/10.png?classes=border,shadow)

This action will redirect you to the *Virtual Machine details page*, where you can find:
- VM **details area** with actual information about it - name, ID, public IP, region, status, memory and image that was used for VM's creation:

![](../../../assets/images/vms/13.png?width=30pc&classes=border,shadow)

- panel with available **quick actions**:
![](../../../assets/images/vms/11.png?width=15pc&classes=border,shadow)
  - *Start* - boots the VM if it is currently shut off or shelved;   
  - *Reboot* - reboots power cycles the VM;  
  - *Shutoff* - stops the VM while keeping its resources (CPU, RAM) reserved on the hypervisor;  
  - *Shelve* - deallocates the VM and releases its resources (CPU, RAM) from the hypervisor;  
  - *Edit* - allows to rename the VM anr set tags fot it;  
  - *Remote console* - opens a web-based remote console to access the VM directly;  
  - **Additional Actions:**
    - *Resize* - changes the VM's flavor;
    - *Download RDP File* - available only for Windows VMs; downloads a Remote Desktop Protocol file to enable remote connection;  
    - *Delete* - permanently removes the VM.  

- transition to the NETWORKS & SECURITY, VOLUMES, SNAPSHOTS and LOG pages related to this VM:
![](../../../assets/images/networks/net-16.png?width=35pc&classes=border,shadow) 

**NETWORKS & SECURITY TAB** - opens the *Networks & Security page* where you can find all available Interfaces and Security Groups (Firewalls) of corresponding VM, add new Interface or/and Firewall, associate Floating IP and manage this services.  
  ![](../../../assets/images/vms/14.2.png?classes=border,shadow)  

💡 To find additional information about Networking and Security and how to manage them through this TAB use the articles: [VM's Firewalls](https://docs.ventuscloud.eu/products/security/manage-firewalls/), [VM's Networks and Interfaces](https://docs.ventuscloud.eu/products/networking/manage-networks/).

**VOLUMES TAB** - opens the *Volumes page* where you can find all attached volumes of corresponding VM, and also attache new one and manage them.  
![](../../../assets/images/vms/15.2.png?classes=border,shadow)  

💡 To find additional information about volumes and how to manage them through this TAB use the articles: [VM's Volumes](https://docs.ventuscloud.eu/products/storage/manage-volumes/). 

**SNAPSHOTS TAB** - opens the *Snapshots page* where you can find all available snapshots of corresponding VM, create new one and manage them.  
![](../../../assets/images/vms/16.2.png?classes=border,shadow)

💡 To find additional information about snapshots and how to manage them through this TAB use the articles: [VM's Snapshots](https://docs.ventuscloud.eu/products/storage/manage-snapshots/).
  
**LOG TAB** - opens the *Log page* where you can find VM's logs.
![](../../../assets/images/vms/17.2.png?classes=border,shadow)

**ACTION LOG TAB** - opens the *Action Log page*, which shows the history of actions performed on this VM.
![](../../../assets/images/vms/18.2.png?classes=border,shadow)

## Download RDP File

{{% notice note %}}
📌 This option is available only for Windows VMs and is used to download RDP file for the remote connection to the Windows VMs.
{{% /notice %}}

To download RDP for the remote connection to the Windows Virtual Machine, do the following:
- identify Windows Virtual Machine, for what  you want to download RDP file on the *Virtual Machines page*;
- click on the **Actions** icon and select the **Download RDP file** in the list of available options.

After these steps, the RDP File of the selected Windows Virtual Machine will be downloaded.  
Alternatively, you can download RDP file from *Virtual Machine details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/vms/30.png?width=15pc&classes=border,shadow)

## Associate/Disassociate Floating IP

{{% notice note %}}
📌 This option is available only for VMs created in the internal network with an configured external Router.
{{% /notice %}}

To associate Floating IP with the Virtual Machine, do the following:
- ensure that you have configured Router with enabled external gateway, which is attached to your internal Network.
  💡 To find information about how to create and configure Router use the article [Routers](https://docs.ventuscloud.eu/products/networking/routers/);
- ensure that you have created Floating IP and it isn't already associated with other cloud Resources;
  💡 To find information about how to create Floating IP use the article [Floating IPs](https://docs.ventuscloud.eu/products/networking/floating-ips/);
- identify Virtual Machine created in the internal network, that you want to make publicly available from the Internet on the *Virtual Machines page*;
- click on the **Actions** icon and select the **Associate Floating IP** in the list of available options;  
- choose one of the available internal interfaces of your VM and one of the previously created Floating IP that you want to attach to the selected interface on the opened *Associate floating IP* and click on the ASSOCIATE icon:  

After these steps, the selected virtual machine will be publicly available:  
![](../../../assets/images/vms/21.png?classes=border,shadow)

Now, if you want to close the access from Internet to this VM again, do the following:  
- click on the **Actions** icon and select the **Disassociate Floating IP**;
- confirm your action on the next opened *Confirmation window* by clicking on the DISASSOCIATE icon. 

After these steps, the selected Virtual Machine will be again publicly unavailable.

Alternatively, you can associate/disassociate floating IPs from the *NETWORKS & SECURITY TAB* on the *Virtual Machine details page*:  
![](../../../assets/images/vms/31.png?classes=border,shadow)

💡 To find additional instructions and information about Floating IPs and VM's Interfaces use the articles: [Floating IPs](https://docs.ventuscloud.eu/products/networking/floating-ips/), [VM's Networks and Interfaces](https://docs.ventuscloud.eu/products/networking/manage-networks/).

## Edit Virtual Machine
To edit the Virtual Machine, do the following:
- identify Virtual Machine, that you want to edit, on the *Virtual Machines page*;
- click on the **Actions** icon  and select the **Edit** in the list of available options;
- update the Virtual Machine Name aor/and add tags to the selected VM on the opened *Edit Virtual Machines window* and click on the SAVE icon.

After these steps, the selected Virtual Machine will be updated.

Alternatively, you can edit virtual machine from its *Details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/vms/22.png?width=15pc&classes=border,shadow)

## Resize Virtual Machine
To resize the Virtual Machine, do the following:
- identify Virtual Machine, that you want to resize, on the *Virtual Machines page*;
- click on the **Actions** icon and select the **Resize** in the list of available options;
- choose new flavor for the Virtual Machine on the next opened *Resize Virtual Machines window* and click on the SAVE icon;
- verify resize by clicking again on the **Actions** icon and select additional option - **Confirm resize**

When the VM's status changes from RESIZE to VERIFY_RESIZE, you can confirm or revert your action, just click again on the **Actions** icon and select one of the additional options - **Confirm resize** or **Revert resize**:
![](../../../assets/images/vms/9-vm.png?classes=border,shadow)

If you confirm resizing, the selected virtual machine will be resized after a few minutes and its status will be ACTIVE. 

Alternatively, you can resize virtual machine from its *Details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/vms/23.png?width=15pc&classes=border,shadow)

## Shutoff Virtual Machine
{{% notice note %}}
ℹ️ Shutoff keeps VM resources (CPU, RAM) reserved on the hypervisor.  
🔔 You'll still be charged, but the VM can be restarted faster.
{{% /notice %}}

To shutoff the Virtual Machine, do the following:
- identify Virtual Machine, that you want to shutoff, on the *Virtual Machines page*;
- click on the **Actions** icon and select the **Shutoff** in the list of available options;
- confirm your action on the next opened *Confirmation window*.
![](../../../assets/images/vms/25.png?width=30pc&classes=border,shadow)

After these steps, the virtual machine status will change to SHUTOFF:
![](../../../assets/images/vms/27.png?classes=border,shadow)

Alternatively, you can shutoff virtual machine from its *Details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/vms/26.png?width=15pc&classes=border,shadow)

To start again Virtual Machine click on the **Actions** icon and select the **Start** in the list of available options.

## Shelve Virtual Machine
{{% notice note %}}
ℹ️ Shelving will release all VM resources (CPU, RAM) on the hypervisor.  
🟢 You won’t be charged, but restarting the VM may take longer.
{{% /notice %}}

To shelve the Virtual Machine, do the following:
- identify Virtual Machine, that you want to shelve, on the *Virtual Machines page*;
- click on the **Actions** icon and select the **Shelve** in the list of available options;
- confirm your action on the next opened *Confirmation window*.
![](../../../assets/images/vms/32.png?width=30pc&classes=border,shadow)

After these steps, the virtual machine status will change to SHELVED:
![](../../../assets/images/vms/33.png?classes=border,shadow)

Alternatively, you can shelve virtual machine from its *Details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/vms/34.png?width=15pc&classes=border,shadow)

To start again Virtual Machine click on the **Actions** icon and select the **Start** in the list of available options.

## Start Virtual Machine

To start the Virtual Machine which is in SHUTOFF or SHELVED status, do the following:
- identify Virtual Machine, that you want to start, on the *Virtual Machines page*;
- click on the **Actions** icon and select the **Start** in the list of available options:  

![](../../../assets/images/vms/28.png?classes=border,shadow)

After these steps, the virtual machine status will change to ACTIVE.

Alternatively, you can start virtual machine from its *Details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/vms/29.png?width=15pc&classes=border,shadow)

## Delete Virtual Machine
To delete the Virtual Machine, do the following:
- identify this unnecessary Virtual Machine on the *Virtual Machines page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Virtual Machine deletion on the next opened *Confirmation window*.

After these steps, the selected Virtual Machine will be deleted.  

Alternatively, you can delete virtual machine from its *Details page*,, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/vms/24.png?width=15pc&classes=border,shadow)


