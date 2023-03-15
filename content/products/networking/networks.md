---
title: Networks
weight: 15
---
___
On this page, you can find an explanation of how to create, edit and delete Networks in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Networks page](#networks-page)
  - [Create Network](#create-network)
    - [Create Subnet](#create-subnet)
  - [Edit Network](#edit-network)
  - [Delete Network](#delete-network)

## Networks page
To get to the *Networks page*, select the **Networking**  from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Networks TAB:**:
![](../../../assets/images/networks/net-1.png?width=15pc&classes=border,shadow) 
![](../../../assets/images/networks/net-13.png?width=20pc&classes=border,shadow) 

On this page you can find the default *public* Network, all your own Networks created in the current Project, and the Networks created during Cluster creation, with the *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Network:
![](../../../assets/images/networks/2.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions, but isn't active for default public Network:
- *Edit* - this option is used to change the name and/or description of the selected Network;
- *Delete* - this option is for Network removing.

## Create Network
{{% notice note %}}
Currently, in Cloud Console can be created only internal networks.
{{% /notice %}}

To create new Network, do the following:
- go to the *Networks page* and click on the CREATE NETWORK icon in the upper left corner;  
- fill in the form on the next opened *Create Network window* and click on the CREATE icon:
![](../../../assets/images/networks/3.png?width=35pc&classes=border,shadow)  
  - *Name* - set a name for the Network; 
  - *Description* - set a description for the Network.

After these steps, the newly created Network will be added to the *Networks page* with the status ACTIVE.  

As a next step, recommended to create Subnets in this Network.

### Create Subnet
To get to the *Subnets page*, related to this Network click on the **Name** of the corresponding Network:
![](../../../assets/images/networks/4.png?classes=border,shadow) 

On the opened *Subnets page* click on the CREATE SUBNET icon in the upper left corner, fill in the form on the next opened *Create Subnet window* and click on the CREATE icon:
![](../../../assets/images/networks/6.png?width=35pc&classes=border,shadow)  

After these steps, the newly created Subnet will be added to the *Subnets page* with the status ACTIVE and you are available to create Virtual Machines in this Subnet or add it's Interface to the already created VMs.  

To find information how to create Virtual Machine in Cloud Console, please see the article - [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/).  
Instructions how to add Subnet Interface to the already created VM you can find in article - [VM's Networks and Interfaces](https://docs.ventuscloud.eu/products/networking/manage-networks/).

{{% notice note %}}
If you need that Virtual Machines created in this Subnet have access to the Internet, please, ensure that you attach Router interface to this Subnet.
{{% /notice %}}

For more information about Subnets and Routers, please, see the articles - [Subnets](https://docs.ventuscloud.eu/products/networking/subnets/), [Routers](https://docs.ventuscloud.eu/products/networking/routers/). 

## Edit Network

{{% notice note %}}
In Cloud Console default public Network can't be edited by User.
{{% /notice %}}

To edit the internal Network, do the following:
- identify internal Network, that you want to edit, on the *Networks page*;
- click on the **Actions** icon  and select the **Edit** in the list of available options;
- update the Name or/and Description of the selected Network, on the next opened *Edit Network window* and click on the SAVE icon.

After these steps, the selected Network will be updated.  
Also, you can edit the Network from its *Subnets page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/networks/net-14.png?width=25pc&classes=border,shadow)  

## Delete Network

{{% notice note %}}
In Cloud Console default public Network can't be deleted by User.
{{% /notice %}}

To delete the internal Network, do the following:
- identify this unnecessary Network on the *Networks page*;
- click on the **Actions** icon  and select the **Delete** in the list of available options;
- confirm the Network deletion on the next opened *Confirmation window*.

After these steps, the selected Network will be deleted.  
Also, you can delete the Network from its *Subnets page*, by clicking on the appropriative **quick actions** icon there.
![](../../../assets/images/networks/net-15.png?width=25pc&classes=border,shadow)  




