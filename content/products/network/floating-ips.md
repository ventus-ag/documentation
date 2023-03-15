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
  - [Edit Floating IP](#edit-floating-ip)
  - [Delete Subnet](#delete-subnet)
  - [Connect Subnets](#connect-subnets)

## Floating IPs page
To get to the *Floating IPs page*, select the **Storage** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Floating IPs TAB:**
![](../../../assets/images/networks/net-1.png?classes=border,shadow?width=100px) 
![](../../../assets/images/networks/net-2.png?classes=border,shadow?width=100px) 

On this page you can find all Floating IPs created in the current Project, with their *Headers*, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Network:
![](../../../assets/images/networks/net-3.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions for the selected Floating IP:
- *Associate* - this option is used to associate selected Floating IP with one of the previously created Interfaces; 
- *Edit* - this option is used to update description of the selected Floating IP; 
- *Delete* - this option is for Floating IP removing.

## Create Floating IP
To create new Floating IP, do the following:
- go to the *Floating IPs page* and click on the CREATE FLOATING IP icon in the upper left corner;
- come up with the description on the next opened *Create Floating IP window* and click on the CREATE icon:
![](../../../assets/images/networks/net-4.png?classes=border,shadow?width=100px) 

After these steps, the newly created Floating IP will be added to the *Floating IPs page*:
![](../../../assets/images/networks/net-5.png?classes=border,shadow)

Also, when creating Floating IP, you can immediately associate it with a previously created Interface:
![](../../../assets/images/networks/net-6.png?classes=border,shadow?width=100px) 

If Floating IP is currently associated with one of the created Interfaces, it status is ACTIVE:
![](../../../assets/images/networks/net-7.png?classes=border,shadow)


## Edit Floating IP
To edit the Subnet, do the following:
- identify the Subnet, that you want to edit, on the *Subnets page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Name, Allocation pools, DNS nameservers, Gateway IP, Host routs or state of DHCP and gateway state on the next opened *Edit Subnet window*, and click on the SAVE icon:
![](../../../assets/images/networks/8.png?classes=border,shadow)

After these steps, the selected Subnet will be updated.

## Delete Subnet
To delete the Subnet, do the following:
- to identify this unnecessary Subnet on the *Subnets page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Subnet deletion on the next opened *Confirmation window*.  

After these steps, the selected Subnet will be deleted.   

## Connect Subnets 
To connect Subnets to each other or to allow them access to the internet you need to add them to the previously created Router on the *Router details page*.  

To open the *Router details page*, go to *Routers page* and click on the **Name** of the corresponding Network:
![](../../../assets/images/networks/17.png?classes=border,shadow) 

On the opened *Router details page* click on the ADD INTERFACE icon, select one of the previously created Subnets on the next opened *Add Interface window* and click on the ADD icon:
![](../../../assets/images/networks/18.png?classes=border,shadow) 

All Subnets that will be added to one Router will be connected to each other:   
![](../../../assets/images/networks/19.png?classes=border,shadow) 
{{% notice note %}}
If Router has an external gateway enabled, the Subnets added to this router will be able to access the Internet.
{{% /notice %}} 
For more information about Routers, please, see the next article - [Routers](https://docs.ventuscloud.eu/products/network/routers/)  
