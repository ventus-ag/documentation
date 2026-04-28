---
title: Ports
weight: 21
---
___
On this page, you can find an explanation of how to create, edit, delete Port and instructions for other steps to manage Ports in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Ports page](#ports-page)
  - [Create Port](#create-port)
  - [Attach Port to the VM](#attach-port-to-the-vm)
  - [Edit Port](#edit-port)
  - [Delete Port](#delete-port)

## Ports page
To open the *Ports page*, go to *Networking page*, click on the **Name** of the corresponding Network and select the **Ports TAB**:
![](../../../assets/images/networks/4.png?classes=border,shadow) 
![](../../../assets/images/networks/26.png?width=15pc&classes=border,shadow)  

On this page you can find all created Ports, related to the selected Network, with the *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Port:

![](../../../assets/images/networks/24.png?classes=border,shadow)  

**Actions** icon opens the next list of available management actions for the selected Port:
- *Edit* - this option is used to update selected Subnet (change Name and/or Admin State); 
- *Delete* - this option is for Port removing.

## Create Port

To create new Port, do the following:
- go to the *Ports page* and click on the CREATE PORT icon in the upper left corner;
- fill in the form on the next opened *Create Port window* and click on the CREATE icon:

![](../../../assets/images/networks/27.png?width=35pc&classes=border,shadow)
  - *Name* - specify a name for the port.
  - *Subnet* - select the subnet where the port will be created;
  - *Fixes IP* - specify a fixed IP address within the selected subnet (optional);
  - *Firewalls* - assign one or more firewall groups to the port (optional).

After these steps, the newly created Port will be added to the *Ports page*:

📝 After creating a port, you can either attach it to an existing Virtual Machine or associate it during the VM creation process.  

## Attach Port to the VM

There are two ways add already created Port to the Virtual Machine:
1) from the *Virtual Machines page* on the step of creating VM:
 
![](../../../assets/images/networks/29.png?width=30pc&classes=border,shadow)

💡 To find information about how to create Virtual Machine see the article - [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/).

2) from the NETWORKS & SECURITY TAB on the *Virtual Machine details page*:

![](../../../assets/images/networks/net-23.png?classes=border,shadow)
  
💡 Detailed information how to change the current set of the VM's Interfaces from the *VM details page* you can find in article: [VM's Networks and Interfaces](https://docs.ventuscloud.eu/products/networking/manage-networks/).
 
## Edit Port

{{% notice note %}}
📌 Editing a Port allows to:
- update the Port name;
- configure assigned firewalls (security groups);
- set the port to active or inactive state;
- enable or disable Port Security.
{{% /notice %}}

To edit the Port, do the following:
- identify the Port, that you want to edit, on the *Ports page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Port Name, and/or Admin State on the next opened *Edit Port window*, and click on the SAVE icon:

![](../../../assets/images/networks/28.png?width=35pc&classes=border,shadow)

After these steps, the selected Port will be updated.

{{% notice note %}}
⚠️ Important limitations:  
- Port Security can only be disabled if no firewalls (security groups) are assigned to the Port;  
- Firewalls cannot be configured when Port Security is disabled.  
{{% /notice %}}

## Delete Port

To delete the Port, do the following:
- to identify this unnecessary Port on the *Ports page* and ensure, that this it isn't still used by other cloud resources;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Port deletion on the next opened *Confirmation window*.  

After these steps, the selected Port will be deleted.   