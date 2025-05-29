---
title: Firewalls
weight: 15
---
___
On this page, you can find an explanation of how to create, edit, delete Firewalls and instructions for other steps to manage Firewalls in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Firewalls page](#firewalls-page)
  - [Create Firewall](#create-firewall)
  - [Edit Firewall](#edit-firewall)
  - [Delete Firewall](#delete-firewall)
  - [Add Firewall to the VM](#add-firewall-to-the-vm)

## Firewalls page
To get to the *Firewalls page*, select the **Security** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Firewalls TAB:**
![](../../../assets/images/cli/1.png?width=15pc&classes=border,shadow) 
![](../../../assets/images/fw/1.png?width=20pc&classes=border,shadow)

On this page you can find *default* Firewall, all your own Firewalls created in the current Project, and the Firewalls created during Cluster creation, with the *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Firewall:
![](../../../assets/images/fw/2.png?classes=border,shadow)

{{% notice note %}}
ℹ️ All VMs have a default Firewall which is applied to every VM.    
📌 User cannot delete default Firewall or change its Name/Description but can change its rules.    
📝 Default Firewall Rules allow access to the Internet from the VMs, but deny almost all access on the VMs from outside, except for objects belonging to the same default Firewall.  
{{% /notice %}}

**Actions** icon opens the next list of available management actions but isn't active for default Firewall:
- *Edit* - this option is used to change the name and/or description of the selected Firewall;
- *Delete* - this option is for Firewall deletion.

## Create Firewall

To create new Firewall, do the following:
- open the *Firewalls page* and click on the CREATE FIREWALL icon in the upper left corner;
- fill in the form on the next opened *Create Firewall window*:

![](../../../assets/images/fw/3.png?width=35pc&classes=border,shadow)
  - *Name* - set a name for the Firewall; 
  - *Description* - set a description for the Firewall.

After these steps, the newly created Firewall will be added to the *Firewalls page*.  

Now you can configure this Firewall Rules.  
To open the *Firewall Rules page* click on the **Name** of the corresponding Firewall:
![](../../../assets/images/fw/5.png?classes=border,shadow)  

On this page you can find:
- panel with available **quick actions** for the selected Firewall:
   
![](../../../assets/images/fw/16.png?width=25pc&classes=border,shadow)

- all Rules, related to the selected Firewall, with the *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Rule:  

![](../../../assets/images/fw/4.png?classes=border,shadow)  

As you can see, the rules, that allow all outbound traffic, have been already created by default, but you can delete them by using **Actions** icon or add additional rule here by using CREATE FIREWALL RULE button.   

💡 For more information about Firewall Rules, please, see the article - [Firewall Rules](https://docs.ventuscloud.eu/products/security/firewall-rules/)

## Edit Firewall

To edit the Firewall, do the following:
- identify Firewall, that you want to edit, on the *Firewalls page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Firewall Name or/and Description on the next opened *Edit Firewall window*, and click on the SAVE icon.  

After these steps, the selected Firewall will be updated.  

Alternatively, you can edit the Firewall from its *Rules page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/fw/19.png?width=25pc&classes=border,shadow)

## Delete Firewall
To delete the Firewall, do the following:
- identify this unnecessary Firewall on the *Firewalls page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Firewall deletion on the next opened *Confirmation window*.

After these steps, the selected Firewall will be deleted.  

Alternatively, you can delete the Firewall from its *Rules page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/fw/21.png?width=25pc&classes=border,shadow)

## Add Firewall to the VM

{{% notice note %}}
📌 You can add and remove rules of the selected Firewall at any time from the *Firewall Rules page* and your changes will automatically applied to the VMs, that are associated with the corresponding Firewall.
{{% /notice %}}

There are two ways add already created Firewall to the Virtual Machine:
1) from the *Virtual Machines page* on the step of creating VM:
 
![](../../../assets/images/fw/22.png?width=30pc&classes=border,shadow)
💡 To find more instructions and information about how to create Virtual Machine see the article - [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/).

2) from the NETWORKS & SECURITY TAB on the *Virtual Machine details page*: 

![](../../../assets/images/conn-lin/23.1.png?classes=border,shadow)
  
💡 Detailed information how to change the current set of the VM's Firewalls from the *VM details page* you can find in article: [VM's Firewalls](https://docs.ventuscloud.eu/products/security/manage-firewalls/). 

 