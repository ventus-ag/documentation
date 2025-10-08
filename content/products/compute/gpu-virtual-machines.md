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

{{% notice note %}}
📌 GPU services in the Cloud Console are currently accessible only for projects established in the Upper-Austria region.
{{% /notice %}} 

Currently, our GPU services are exclusively available in the Upper-Austria region. We offer a range of GPU cards, including the H100 and L40S series, each available in multiple configurations to suit various performance needs:  
- GPU-H100-1: 1 H100, 12 vCPUs, 250 GiB memory;  
- GPU-H100-2: 2 H100, 24 vCPUs, 500 GiB memory;  
- GPU-H100-4: 4 H100, 48 vCPUs, 1000 GiB memory;  
- GPU-L40S-1: 1 L40S, 12 vCPUs, 224 GiB memory;  
- GPU-L40S-2: 2 L40S, 24 vCPUs, 448 GiB memory;  
- GPU-L40S-4: 4 L40S, 48 vCPUs, 960 GiB memory.

ℹ️ By default, these flavors are provided, but if you need a custom flavor, please contact our support team for assistance.

Choosing the appropriate GPU model allows you to enhance your applications for improved performance and efficiency within our cloud environment.

## Create GPU Virtual Machine

Creating a GPU VM involves a similar process to setting up regular Ubuntu or Windows VMs, but with a few additional steps specific to GPU Flavor configurations.

**GPU VM Creation Process:**   
1) Go to the *Virtual Machines page* and click on the CREATE VM icon in the upper left corner;
2) Fill in the form on the next opened *Create Virtual Machine window*:
![](../../../assets/images/vms/gpu-1.png?width=30pc&classes=border,shadow)
  - *Name* - specify a name for the virtual machine.  
  - *Source* - choose the source for creating the VM: image, volume, or snapshot;  
    by default, "image" is pre-selected.   
  - *OS Platform* - choose the operating system platform: Linux or Windows;  
    in this example we will create the Linux VM.     
  - *Linux Distribution* -  if Linux OS is selected, choose the desired distribution (e.g. Ubuntu, CentOS, etc.).  
  - *Image Version*/*Volume name*/*Snapshot name* - based on the selected source, specify the corresponding image version, volume name, or snapshot name.      
  - *Choose Flavor Type* - select *GPU Flavor Type* if you need a VM with GPU capabilities.   
  - *Choose Flavor* - pick the type of GPU card and size for your new VM;  
    ℹ️ available GPU flavors:
    ![](../../../assets/images/vms/gpu-2.png?width=30pc&classes=border,shadow)

    ℹ️ If the list of GPU flavors is empty, your project is not currently associated with any GPU flavors.   
    🔔 Please contact support to request access:
    ![](../../../assets/images/vms/gpu-3.png?width=30pc&classes=border,shadow)

  - *Key pair* - required for Linux VMs; choose an existing SSH key (created on the *SSH Keys* page) or create a new one to connect to the VM via SSH.   
  - *Networks / Ports* — choose how the VM will connect to the network:
    - *Networks* — select one or more available networks. A new port will be created automatically for each selected network;  
      by default, "public" network is pre-selected;  
      optionally specify Fixed IPs within the subnet when using the network option.   
    - *Ports* — select an existing port to attach to the VM; the assigned firewalls will be displayed below (read-only). 
  - *Firewalls* - define which network rules control VM traffic:       
    - using *Networks*, you can select Firewalls manually;   
      by default, "default" Firewall is pre-selected;  
    - using *Ports*, Firewalls will be inherited from the selected port.     

    💡 The default Firewall allows outgoing Internet access but restricts incoming connections, except from resources in the same Firewall group.  
  - *Tags* - optional; use this field to assign tags to the VM.  
  - *Volume size (GB)* - provide the preferred disk size for the VM;  
    valid range: 10–1000 GiB;   
    minimal available size for Linux VMs - 10 GB; for Windows VMs - 50 GB;    
    by default, "50 GB" is pre-selected.  
  - *Delete Volume after VM deletion* – enable this option to automatically delete the volume when the VM is removed.  

3) Complete VM Creation: Click on the CREATE icon to finalize the creation of your GPU VM.   

After these steps, the newly created GPU VM will be added to the *Virtual Machine page* with the status ACTIVE.

## Post-Creation Management

The management actions for GPU VMs, such as Editing, Resizing, Associating/Disassociating a Floating IP, or Deleting, are identical to those for non-GPU VMs. 

💡 For additional details on these processes, refer to the **[Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/)** article.
