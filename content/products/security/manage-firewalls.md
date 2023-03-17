---
title: VM's Firewalls
weight: 22
---
___
On this page, you can find an explanation of how to manage Firewalls, related to the selected Virtual Machine, from the *Virtual Machine details page* in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [VM's NETWORKS \& SECURITY TAB](#vms-networks--security-tab)
  - [Change Firewall set](#change-firewall-set)

## VM's NETWORKS & SECURITY TAB
To find all Firewalls, related to the selected Virtual Machine, you need:
- open the *Virtual Machines page* - for this select the **Virtual Machines** from the VIRTUAL DATACENTER block in the *side-bar menu*:

![](../../../assets/images/conn-lin/7.png?width=15pc&classes=border,shadow)

- open the *Virtual Machine details page* - for this click on the **Name** of the corresponding Virtual Machine:  

![](../../../assets/images/fw/0.png?classes=border,shadow)

- open the *NETWORKS & SECURITY page of this VM*:

![](../../../assets/images/net/16.png?width=25pc&classes=border,shadow)

On the opened  *NETWORKS & SECURITY page of this VM* you can find information about all Networks, Subnets, Floating IPs and also information about all Firewalls related to this VM.

In this article, we are interested in the block of information, where you can find all Firewalls related to the corresponding VM with their *Actions icon*, which opens a list of available management actions:
![](../../../assets/images/fw/9.png?classes=border,shadow)

Information how to manage Networks, Subnets and Floating IPs from this page, you can find in the article [VM's Networks and Interfaces](https://docs.ventuscloud.eu/products/networking/manage-networks/).

## Change Firewall set
To add additional Firewall or delete unnecessary one from the selected VM, do the following:
- click on the *Actions icon* and select the **Edit Firewalls** in the list of available options;
- remove an unnecessary firewall or select an additional one from the list of previously added firewalls and click on the SAVE icon:  

![](../../../assets/images/fw/23.png?width=35pc&classes=border,shadow) 

After these steps, the newly added Firewall will be added to the selected VM:  
![](../../../assets/images/fw/14.png?classes=border,shadow)  

{{% notice note %}}
You can add and remove rules of the selected Firewall at any time from the *Firewall Rules page* and your changes will automatically applied to the VMs, that are associated with the corresponding Firewall.
{{% /notice %}}
 
For more information about Firewalls and their Rules, please, see the next articles: [Firewalls](https://docs.ventuscloud.eu/products/security/firewalls/), [Firewall Rules](https://docs.ventuscloud.eu/products/security/firewall-rules/).

Also, you can create new VM and immediately associate it with desired Firewall, during it's creation.   
To find information about how to create Virtual Machine use the article [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/).
![](../../../assets/images/networks/net-22.png?width=30pc&classes=border,shadow)
![](../../../assets/images/fw/22.png?width=30pc&classes=border,shadow)


