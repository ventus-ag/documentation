---
title: Floating IPs
weight: 20
---
___
On this page, you can find an explanation of how to create, associate, edit and delete Floating IPs in Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Floating IPs page](#floating-ips-page)
  - [Create Subnet](#create-subnet)
  - [Edit Subnet](#edit-subnet)
  - [Delete Subnet](#delete-subnet)
  - [Connect Subnets](#connect-subnets)

## Floating IPs page
To get to the *Floating IPs page*, select the **Storage** from the VIRTUAL DATACENTER block in the *side-bar menu* and click the **Floating IPs TAB:**
![](../../../assets/images/networks/net-1.png?classes=border,shadow?width=20pc) 
![](../../../assets/images/networks/4.png?classes=border,shadow?width=20pc) 

On this page you can find:
- panel with available **quick actions** for the selected Network: 
![](../../../assets/images/networks/13.png?classes=border,shadow) 
- all created Subnets, related to the selected Network, with their *Headers*, *Create button*, *Search bar* and *Actions icon*, which opens a list of available management actions for the selected Subnet:
![](../../../assets/images/networks/7.png?classes=border,shadow) 

**Actions** icon opens the next list of available management actions for the selected Subnet:
- *Edit* - this option is used to update selected Subnet (change Name, Allocation pools, DNS nameservers, Gateway IP, Host routs, state of DHCP and gateway); 
- *Delete* - this option is for Subnet removing.

## Create Subnet
To create new Subnet, do the following:
- go to the *Subnets page* and click on the CREATE SUBNET icon in the upper left corner;
- fill in the form on the next opened *Create Subnet* *window* and click on the CREATE icon:
![](../../../assets/images/networks/6.png?classes=border,shadow)
  - *Name* - set a name for the Subnet;
  - *Enable DHCP* - enable or disable Dynamic Host Configuration Protocol for Subnet;
  - *CIDR* - shows Classless Inter-Domain Routing of Subnet;
  - *Allocation Pools* - specify IP address allocation pools; each entry is: start_ip_address-end_ip_address; one entry per line;
  - *DNS Nameservers* - specify the IP addresses of DNS Name Servers; format: comma-separated values;
  - *Gateway IP* - set the IP address of Gateway; the default value is the first IP of the network address; if you want to use the default, leave blank. If you do not want to use a gateway, please check ‘Disable Gateway’;
  - *Disable Gateway* - enable or disable using Gateway IP for Subnet;
  - *Host Routes* - specify additional routes announced to the hosts; each entry is: destination_cidr,next-hop; one entry per line.

After these steps, the newly created Subnet will be added to the *Subnets page*:
![](../../../assets/images/networks/16.png?classes=border,shadow)

{{% notice note %}}
You can connect Subnets to each other by attaching Router.
{{% /notice %}}

## Edit Subnet
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
