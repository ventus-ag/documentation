---
title: Routers
weight: 20
---
___
On this page, you can find an explanation of how to create, edit, delete Routers and how to manage Interfaces inside them in Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Routers page](#routers-page)
  - [Create Router](#create-router)
    - [Add Interface to the Router](#add-interface-to-the-router)
    - [Add custom Route to the Router](#add-custom-route-to-the-router)
  - [Edit Router](#edit-router)
  - [Delete router](#delete-router)

## Routers page
To get to the *Routers page*, select the **Networking** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Routers TAB:**
![](../../../assets/images/networks/net-1.png?width=15pc&classes=border,shadow) 
![](../../../assets/images/routers/1.png?width=20pc&classes=border,shadow) 

On this page you can find all Routers created in the current Project, with the *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Routers:
![](../../../assets/images/routers/2.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions for the selected Router:
- *Edit* - this option is used to update name/description of the selected Router; 
- *Delete* - this option is for the Router removing.

## Create Router 

To create new Router, do the following:
- go to the *Routers page* and click on the CREATE ROUTER in the upper left corner;  
- fill in the form on the next opened *Create Router window* and click on the CREATE icon:

![](../../../assets/images/routers/3.png?width=35pc&classes=border,shadow)  
  - *Name* - set a name for the Router; 
  - *Description* - set a description for the new Router;
  - *Enable external gateway* - make a mark if you need to open access to the Internet for your VMs with this Router.

After these steps, the newly created Router will be added to the *Routers page* with the status ACTIVE.  

As a next step, is highly recommended to attach already created internal Interfaces to this Router and optionally add custom routes. 

### Add Interface to the Router 

To add Interfaces to the already created Router do the following:
- ensure that you have already created Network with associated Subnets, which Interfaces you want to add to the Router;  
  To find information about how to create internal Network and Subnet use the articles [Networks](https://docs.ventuscloud.eu/products/networking/networks/), [Subnets](https://docs.ventuscloud.eu/products/networking/subnets/);
- open the *Router details page* - for this, click on the **Name** of the corresponding Router:

![](../../../assets/images/routers/4.png?classes=border,shadow)  

- click on the ADD INTERFACE icon:

![](../../../assets/images/routers/5.png?classes=border,shadow) 

- select one of the available Subnets and click on the ADD icon:

![](../../../assets/images/routers/6.png?width=35pc&classes=border,shadow)

{{% notice note %}}
If you add more interfaces to the same Router, the VMs created on these subnets will be able to access each other.
{{% /notice %}}

After these steps, the newly added Interface will appear in the *Router details page* in the ACTIVE status with available action icon for its removing. Now, all Virtual Machines created in this Subnet will have access to the internet, as this Router was created with *Enabled external gateway*:

![](../../../assets/images/routers/7.png?classes=border,shadow) 

### Add custom Route to the Router 

This step is optional in Router configuration, but if you need to add custom Route to the created Router, do the following:
- open the *Router details page* - for this, click on the **Name** of the corresponding Router:
![](../../../assets/images/routers/4.png?classes=border,shadow) 

- click on the ADD ROUTE icon:

![](../../../assets/images/routers/10.png?classes=border,shadow) 

- fill in the form on the next opened *Add Route window* and click on the ADD icon:

![](../../../assets/images/routers/11.png?width=35pc&classes=border,shadow)  

After these steps, the newly added Route will appear on the *Router details page* with available action icon for its removing:

![](../../../assets/images/routers/12.png?classes=border,shadow) 

## Edit Router

To edit the Router, do the following:
- identify iRouter, that you want to edit, on the *Routers page*;
- click on the **Actions** icon  and select the **Edit** in the list of available options;
- update the Name or/and Description of the selected Router, on the next opened *Edit Router window* and click on the SAVE icon.

After these steps, the selected Router will be updated.  
Also, you can edit the Router from its *Details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/routers/8.png?width=25pc&classes=border,shadow)  

## Delete router

To delete Router, do the following:
- identify this unnecessary Router on the *Routers* and ensure, that this it isn't still used by other cloud resources;
- click on the **Actions** icon  and select the **Delete** in the list of available options;
- confirm the Router deletion on the next opened *Confirmation window*.

After these steps, the selected Router will be deleted.  
Also, you can delete the Router from its *details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/routers/9.png?width=25pc&classes=border,shadow)  

