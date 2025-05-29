---
title: Routers
weight: 20
---
___
On this page, you can find an explanation of how to create, edit, delete Routers and how to manage Interfaces inside them in Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Routers](#routers)
  - [Routers page](#routers-page)
  - [Create Router](#create-router)
    - [Add Interface to the Router](#add-interface-to-the-router)
    - [Add custom Route to the Router](#add-custom-route-to-the-router)
  - [Edit Router](#edit-router)
  - [Delete Router](#delete-router)

## Routers
Router is an important infrastructure component that can come in handy when you need to:  
- Provide access to the internet for instances provisioned in a private network;  
- Interconnect two or more networks;  
- Manage routes for traffic in advanced network scenarios;  

## Routers page
To get to the *Routers page*, select the **Networking** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Routers TAB:**
![](../../../assets/images/networks/net-1.png?width=15pc&classes=border,shadow) 
![](../../../assets/images/routers/1.png?width=25pc&classes=border,shadow) 

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
  - *Enable external gateway* - select it if you want to use the router as a gateway for instances created in private network. In other words, it will let instances from private network access to internet. 

After these steps, the newly created Router will be added to the *Routers page* with the status ACTIVE.  

### Add Interface to the Router 

{{% notice note %}}
Router can be connected to one or more private networks by adding it's interface to network.  
{{% /notice %}}

To add Interfaces to the already created Router do the following:
- ensure that you have already created Network with associated Subnets;  
  💡 To find information about how to create internal Network and Subnet use the articles [Networks](https://docs.ventuscloud.eu/products/networking/networks/), [Subnets](https://docs.ventuscloud.eu/products/networking/subnets/);
- open the *Router details page* - for this, click on the **Name** of the corresponding Router:

![](../../../assets/images/routers/4.png?classes=border,shadow)  

- click on the ADD INTERFACE icon:

![](../../../assets/images/routers/5.png?classes=border,shadow) 

- select one of the available Subnets and click on the ADD icon:

![](../../../assets/images/routers/6.png?width=35pc&classes=border,shadow)

{{% notice note %}}
📌 If Router was created with *Enabled external gateway* all Virtual Machines created in this Subnet will have access to the internet.
{{% /notice %}}


After these steps, the newly added Interface will appear in the *Router details page* in the ACTIVE status with available *action icon* for its removing. Now, all Virtual Machines created in this Subnet will have access to the internet, as this Router was created with *Enabled external gateway*:

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
- identify Router, that you want to edit, on the *Routers page*;
- click on the **Actions** icon  and select the **Edit** in the list of available options;
- update the Name or/and Description of the selected Router, on the next opened *Edit Router window* and click on the SAVE icon.

After these steps, the selected Router will be updated.  
Alternatively, you can edit Router from its *Details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/routers/8.png?width=13pc&classes=border,shadow)  

## Delete Router

To delete Router, do the following:
- identify this unnecessary Router on the *Routers page* and ensure, that it has no attached interfaces to networks, delete them if any;
- click on the **Actions** icon  and select the **Delete** in the list of available options;
- confirm the Router deletion on the next opened *Confirmation window*.

After these steps, the selected Router will be deleted.  
Alternatively, you can delete Router from its *Details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/routers/9.png?width=13pc&classes=border,shadow)  

