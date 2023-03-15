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
![](../../../assets/images/networks/1.png?classes=border,shadow) 
![](../../../assets/images/networks/0.png?classes=border,shadow) 

On this page you can find the default *public* Network, all your own Networks created in the current Project, and the Networks created during Cluster creation, with their *Headers*, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Network:
![](../../../assets/images/networks/2.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions, but isn't active for default public Network:
- *Edit* - this option is used to change the name, description of the selected Network and its administrative state;
- *Delete* - this option is for Network removing.

## Create Network
{{% notice note %}}
Currently only internal networks can be created.
{{% /notice %}}

To create new Network, do the following:
- go to the *Networks page* and click on the CREATE NETWORK icon in the upper left corner;  
- fill in the form on the next opened *Create Network window* and click on the CREATE icon:
![](../../../assets/images/networks/3.png?classes=border,shadow)  
  - *Name* - set a name for the Network; 
  - *Description* - set a description for the Network;
  - make a mark, if the Network need the *administrative* state to be up.

After these steps, the newly created Network will be added to the *Networks page* with the status ACTIVE.  

As a next step, we recommend to create Subnets in this Network.

### Create Subnet
To get to the *Subnets page*, related to this Network click on the **Name** of the corresponding Network:
![](../../../assets/images/networks/4.png?classes=border,shadow) 

On the opened *Subnets page* click on the CREATE SUBNET icon in the upper left corner, fill in the form on the next opened *Create Subnet window* and click on the CREATE icon:
![](../../../assets/images/networks/14.png?classes=border,shadow) 

After these steps, the newly created Subnet will be added to the *Subnets page* with the status ACTIVE. 

For more information about Subnets, please, see the next article - [Subnets](https://docs.ventuscloud.eu/products/networking/subnets/)  

## Edit Network
To edit the Network, do the following:
- identify the Network, that you want to edit, on the *Networks page*;
- click on the **Actions** icon  and select the **Edit** in the list of available options;
- update the Name or/and Description of the selected Network, change its administrative state on the next opened *Edit Network window* and click on the SAVE icon.

After these steps, the selected Network will be updated.  
Also, you can edit the Network from its *Subnets page*, by clicking on the appropriative **quick actions** icon there.

## Delete Network
To delete the Network, do the following:
- identify this unnecessary Network on the *Networks page*;
- click on the **Actions** icon  and select the **Delete** in the list of available options;
- confirm the Network deletion on the next opened *Confirmation window*.

After these steps, the selected Network will be deleted.  
Also, you can delete the Network from its *Subnets page*, by clicking on the appropriative **quick actions** icon there.

