---
title: GPU Virtual Machines
weight: 11
---
___
On this page, you can find an explanation of how to create GPU Virtual Machine, and instructions for other steps to manage Virtual Machines in Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Create GPU Virtual Machine](#create-gpu-virtual-machine)
  - [Post-Creation Management](#post-creation-management)

## Introduction
GPU virtual machines (VMs) offer significant advantages for tasks that require intensive graphics processing or parallel computations. 

Currently, our GPU services are exclusively available in the Vienna and Upper-Austria regions. We offer a range of GPU cards, including the H100 and L40S series, each available in multiple configurations to suit various performance needs.

{{% notice note %}}
GPU services in the Cloud Console are currently accessible only for projects established in the Vienna and Upper-Austria regions.
{{% /notice %}} 

Choosing the appropriate GPU model allows you to enhance your applications for improved performance and efficiency within our cloud environment.

## Create GPU Virtual Machine

Creating a GPU VM involves a similar process to setting up regular Ubuntu or Windows VMs, but with a few additional steps specific to GPU Flavor configurations.

But, before starting to create GPU VM, please ensure that your project is located in either the Upper Austria or Vienna regions, as our GPU services are currently available only there.

**GPU VM Creation Process:**

1) Verify your project's region: GPU cards are available in the Vienna and Upper-Austria regions;  
2) Go to the *Virtual Machines page* and click on the CREATE VM icon in the upper left corner;
3) Fill in the form on the next opened *Create Virtual Machine window*:
![](../../../assets/images/vms/gpu-1.png?width=30pc&classes=border,shadow)
  - *Name* - assign a name for the VM;  
  - *Source* - choose the source which you want to use for VM creating: image, volume or snapshot;  
    by default, "Image" is pre-selected;    
  - *OS Platform* - choose between Linux or Windows (in this example we will create the Linux VM);   
    by default, "Linux" is pre-selected;   
  - *Linux Distribution* - if in the previous step, you choose the Linux OS, next you need to choose what Linux distribution to use for your VM;   
    by default, "Ubuntu" is pre-selected;   
  - *Image Version*/*Volume name*/*Snapshot name* - specify the name or ID of the previously selected Source for VM creating (Image Version, Volume name or Snapshot name);   
  - *Choose Flavor Type* - select *GPU Flavor Type* if you need a VM with GPU capabilities; 
  - *Choose Flavor* - pick the type of GPU card and size for your new VM;
    available GPU flavors:
    ![](../../../assets/images/vms/gpu-2.png?width=30pc&classes=border,shadow)

    if the list of GPU flavors is empty, this indicates that your project is not currently associated with any GPU flavors. Please contact support to request access:
    ![](../../../assets/images/vms/gpu-3.png?width=30pc&classes=border,shadow)

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

4) Complete VM Creation: Click on the CREATE icon to finalize the creation of your GPU VM.   

After these steps, the newly created GPU VM will be added to the *Virtual Machine page* with the status ACTIVE.


## Post-Creation Management

The management actions for GPU VMs, such as Editing, Resizing, Associating/Disassociating a Floating IP, or Deleting, are identical to those for non-GPU VMs. 

For additional details on these processes, refer to the  **[Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/)** article.

This structured guide should help users navigate the process of setting up a GPU VM in Cloud Console environment efficiently and effectively.
