---
title: Floating IPs
weight: 20
---
___
On this page, you can find an explanation of how to create, associate, edit and delete Floating IPs in Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Floating IPs page](#floating-ips-page)
  - [Create Floating IP](#create-floating-ip)
  - [Associate/Disassociate Floating IP](#associatedisassociate-floating-ip)
  - [Edit Floating IP](#edit-floating-ip)
  - [Delete Floating IP](#delete-floating-ip)

## Floating IPs page
To get to the *Floating IPs page*, select the **Storage** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Floating IPs TAB:**
![](../../../assets/images/networks/net-1.png?width=15pc&classes=border,shadow) 
![](../../../assets/images/networks/net-2.png?width=20pc&classes=border,shadow) 

On this page you can find all Floating IPs created in the current Project, with their *Headers*, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Network:
![](../../../assets/images/networks/net-3.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions for the selected Floating IP:
- *Associate* - this option is used to associate selected Floating IP with one of the previously created VM's internal Interfaces;
- *Disassociate* - this option is available only for Floating IPs that are already associated with one of the previously created Interfaces; 
- *Edit* - this option is used to update description of the selected Floating IP; 
- *Delete* - this option is for Floating IP removing.

## Create Floating IP
To create new Floating IP, do the following:
- go to the *Floating IPs page* and click on the CREATE FLOATING IP icon in the upper left corner;
- come up with the description on the next opened *Create Floating IP window* and click on the CREATE icon:   
![](../../../assets/images/networks/net-4.png?width=35pc&classes=border,shadow) 

After these steps, the newly created Floating IP will be added to the *Floating IPs page*:
![](../../../assets/images/networks/net-5.png?classes=border,shadow)

Also, when creating Floating IP, you can immediately associate it with a previously created Interface:
![](../../../assets/images/networks/net-6.png?width=35pc&classes=border,shadow) 

If Floating IP is currently associated with one of the created Interfaces, it status is ACTIVE:
![](../../../assets/images/networks/net-7.png?classes=border,shadow)

## Associate/Disassociate Floating IP

There are two ways associate/disassociate already created Floating IP with the VM's internal Interfaces:
- from the *Floating IPs page*;
- from the NETWORKS & SECURITY TAB on the *Virtual Machine details page*.

In this article we will explain the first way - how to associate/disassociate Floating IP from the *Floating IPs page*.  
Information about the second one you can find in the article - [VM's Networks and Interfaces](https://docs.ventuscloud.eu/products/networking/manage-networks/).

Also, as you know from the previous chapter, you can immediately associate Floating IP when you create it.

{{% notice note %}}
Successfully Associate Floating IP with VM's internal Interface you can only in case if you have configured Router with enabled external gateway and attached to your internal Network.
{{% /notice %}}

To associate already created Floating IP with the VM's internal Interfaces, do the following:
- ensure that you have created VM in internal Network, which Interface you want to associate with the Floating IP.  
  To find information about how to create internal Network use the article [Networks](https://docs.ventuscloud.eu/products/networking/networks/) and how to create VM - article [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/);
- ensure that you have configured Router with enabled external gateway, which is attached to your internal Network.
  To find information about how to create and configure Router use the article [Routers](https://docs.ventuscloud.eu/products/networking/routers/);
- identify the Floating IP, that you want to associate, on the *Floating IPs page*;
- click on the **Actions** icon and select the **Associate** in the list of available options;
- select one of the available VM's internal Interfaces on the next opened window, and click on ASSOCIATE:
![](../../../assets/images/networks/net-9.png?width=35pc&classes=border,shadow) 

After these steps, the selected Floating IP will have ACTIVE status and the associated with it VM will be publicly available:
![](../../../assets/images/networks/net-11.png?classes=border,shadow) 

If you need to disassociate Floating IP and to make your VM again publicly unavailable, do the following:
- identify the associated Floating IP, that you want to disassociate, on the *Floating IPs page*;
- click on the **Actions** icon and select the **Disassociate** in the list of available options:
![](../../../assets/images/networks/net-12.png?classes=border,shadow) 

After confirmation your action on the next opened window the selected Virtual Machine will be again publicly unavailable and Floating IP has status DOWN.

## Edit Floating IP

To edit the Floating IP, do the following:
- identify the Floating IP, that you want to edit, on the *Floating IPs page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Description on the next opened *Edit Floating IP window*, and click on the SAVE icon:
![](../../../assets/images/networks/net-8.png?width=40pc&classes=border,shadow) 

After these steps, the selected Subnet will be updated.

## Delete Floating IP

To delete the Floating IP, do the following:
- to identify this unnecessary Floating IP on the *Floating IPs page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Floating IP deletion on the next opened *Confirmation window*.  

After these steps, the selected Floating IP will be deleted.   

