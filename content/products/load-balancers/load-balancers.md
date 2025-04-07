---
title: Load Balancers
weight: 1
---
___
On this page, you can find an explanation of how to create, edit, delete Load Balancer and instructions for other steps to manage it in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Load Balancers page](#load-balancers-page)
  - [Create Load Balancer](#create-load-balancer)
  - [Load Balancer details page](#load-balancer-details-page)
  - [Edit Load Balancer](#edit-load-balancer)
  - [Associate/Disassociate Floating IP](#associatedisassociate-floating-ip)
  - [Delete Load Balancer](#delete-load-balancer)

## Introduction
A Load Balancer (LB) helps distribute incoming traffic across multiple backend servers to ensure high availability and better performance. It provides a single access point to your application and automatically reroutes traffic if a server becomes unavailable. 

A Load Balancer is a layered, multi-component entity. It always works in combination with **listeners** *(which define how incoming traffic is accepted)* and **pools** *(which group backend servers)*. Each pool can have multiple **members** (instances) and an associated **health monitor** that ensures traffic is only sent to healthy servers. These components work together to provide a flexible and reliable traffic distribution system.

In the Cloud Console, you can easily create a Load Balancer, add backend members, set up health checks, and assign a floating IP for external access.

## Load Balancers page
To get to the *Load Balancers page*, select the **Load Balancers** from the VIRTUAL DATACENTER block in the *side-bar menu*:
![](../../../assets/images/lb/1.png?width=15pc&classes=border,shadow) 

On this page you can find all created Load Balancers in the current Project, with the *Create button, Search bar* and *Actions icon*, which opens a list of available management actions for the selected LB:
![](../../../assets/images/lb/2.png?classes=border,shadow)

**Actions** icon opens the next list of available management actions:  
- *Associate Floating IP* - assign a public (floating) IP address to the LB to make it accessible from the internet;   
- *Edit* - update the LB’s name, description, or administrative state (enable/disable);  
- *Delete* - permanently remove the LB from the project.

Additionally, from this page, you can navigate to the detail page of each created Load Balancer by clicking on its **name**. There, you will find detailed information about its listeners and pools and allows you to manage pool members and perform other actions related to the selected Load Balancer. More information about the *Load Balancer details page* will be provided in the following sections.   
![](../../../assets/images/lb/4.png?classes=border,shadow)

## Create Load Balancer

{{% notice note %}}
As part of the Load Balancer creation process, you will also set up its listener, pool, and health monitor.
{{% /notice %}}

To create new Load Balancer, do the following:
- open the *Load Balancers page* and click on the CREATE LOAD BALANCER icon in the upper left corner;
- fill in the form on the next opened *Create Load Balancer window*:

![](../../../assets/images/lb/3.png?width=30pc&classes=border,shadow)
  - *Name* - set a name for the Load Balancer; 
  - *Subnet* - select the subnet where the Load Balancer will be created (this defines its internal IP address);   
  **Listener Configuration:**  
  - *Listener Protocol* - choose the protocol (e.g., HTTP, TCP) that the Load Balancer will use to listen for incoming traffic;     
  - *Listener Port* - specify the port number (from 1 to 65535) that will be used to accept traffic;    
  - *Connection Limit* - set the maximum number of simultaneous connections. Use -1 for unlimited connections;  
  **Pool Configuration:**   
  - *Pool Algorithm* - select a method for distributing traffic:  
      ROUND ROBIN – evenly distributes requests among pool members.  
      LEAST CONNECTIONS – directs requests to the member with the fewest active connections.    
      SOURCE IP – consistently routes traffic from the same IP to the same member.  

  - *Session Persistence* - define how client sessions stick to specific backend servers:  
      SOURCE IP – based on source IP address.  
      HTTP COOKIE – based on an HTTP cookie.  
      APP COOKIE – based on an application-specific cookie.  

  **Health Monitor Configuration:**  
  - *Health Monitor Type* - choose the protocol for health checks (e.g., HTTP, TCP);  
  - *Timeout* - time (in seconds) to wait for a response before marking the check as failed;    
  - *Delay* -  interval (in seconds) between consecutive health checks. Must be greater than or equal to the timeout;  
  - *Max Retries* - number of failed checks before marking the member as inactive. Must be a number from 1 to 10;  
  - *Max Retries Down* - number of failures before marking the member as in error. Must be a number from 1 to 10;  
  - *HTTP Method* - the HTTP method used for the health check (e.g., GET);  
  - *Expected Codes* - expected HTTP status codes that indicate a healthy response (can be a number, list, or range);  
  - *URL Path* - the endpoint path for the health check (e.g., /health).

After these steps, the newly created Load Balancer will be added to the *Load Balancers page* and you can click on its **name** to navigate to the *Load Balancer details page* to view all necessary information about it, including created listener, pool, and configured health monitor. More information about the *Load Balancer details page* will be provided in the following sections.  

![](../../../assets/images/lb/16.png?classes=border,shadow)

## Load Balancer details page
To open the *Load Balancer details page*, click on the **Name** of the corresponding workload on the *Load Balancers page*:
![](../../../assets/images/lb/4.png?classes=border,shadow)

This action will redirect you to the *Load Balancer details page*, where you can find:  
- **details section** showing key information about the selected Load Balancer;  
- panel with available **quick actions**: edit, delete, associate/disassociate floating IP;  
- two **tabs**: Listeners and Pools.
![](../../../assets/images/lb/6.png?width=25pc&classes=border,shadow)
  
**LISTENERS TAB** - displays all listeners associated with the Load Balancer
![](../../../assets/images/lb/7.png?classes=border,shadow)

From here, it is possible to create new listeners, manage (edit/delete/change associated pool) existing ones, and navigate to the *Listener details page* by clicking on the listener's **name**.   On the *Listener details page* you can find all necessary information about it and its associated pool and health monitor, add or remove pool members, manage the listener itself (edit, delete), as well as the related pool and health monitor. More information about this page you can find here - [Listener details page](https://docs.ventuscloud.eu/products/load-balancers/listeners/#listener-details-page).
  
**POOLS TAB** - lists all pools created under the Load Balancer:
![](../../../assets/images/lb/8.png?classes=border,shadow)

From here, it is possible to create new pools, edit or delete existing ones, and navigate to the *Pool Details page* by clicking on the pool’s **name**. On the *Pool Details page*, you can find all relevant information about the selected pool and its associated health monitor, manage the pool itself (edit, delete), add or remove pool members, and also manage related components such as the listener and health monitor. More information about this page you can find here - [Pool details page](https://docs.ventuscloud.eu/products/load-balancers/pools/#pool-details-page).

## Edit Load Balancer
To edit the Load Balancer, do the following:  
- identify Load Balancer, that you want to edit, on the *Load Balancers page*;  
- in the opened window click on the **Actions** icon and select the **Edit** in the list of available options;  
![](../../../assets/images/lb/10.1.png?classes=border,shadow)
- update desired settings, such as the name, description, and administrative state on the opened dialog: 
![](../../../assets/images/lb/10.png?width=30pc&classes=border,shadow)

After these steps, the selected Load Balancer will be updated.  

Also, you can edit the Load Balancer directly from its related detail pages:  
- on the *Load Balancer details page* - by clicking on the appropriative **quick actions** icon at the top:   
![](../../../assets/images/lb/11.png?width=25pc&classes=border,shadow)   
- on the *Listener Details page* – by clicking the **edit icon** in the Load Balancer information block:   
![](../../../assets/images/lb/11.1.png?classes=border,shadow)  
- on the *Pool Details page* - by clicking the **edit icon** in the Load Balancer information block:   
![](../../../assets/images/lb/11.2.png?classes=border,shadow)   

## Associate/Disassociate Floating IP 

{{% notice note %}}
This option is available only for Load Balancers created in the internal network with an configured external Router.
{{% /notice %}}

To associate Floating IP with the Load Balancer, do the following:  
- ensure that you have created Floating IP and it isn't already associated with other cloud Resources;  
  To find information about how to create Floating IP use the article [Floating IPs](https://docs.ventuscloud.eu/products/networking/floating-ips/);

- ensure that you have configured Router with enabled external gateway, which is attached to your internal Network;  
  To find information about how to create and configure Router use the article [Routers](https://docs.ventuscloud.eu/products/networking/routers/);  

- identify Load Balancer, that you want to make publicly available from the Internet on the *Load Balancers page*;
- click on the **Actions** icon and select the **Associate Floating IP** in the list of available options;
![](../../../assets/images/lb/13.png?classes=border,shadow)

- in the opened window choose one of the previously created Floating IP that you want to attach to the selected Load Balancer and click the ASSOCIATE icon:  

![](../../../assets/images/lb/14.png?width=30pc&classes=border,shadow)

After these steps, the selected Load Balancer will be publicly available:  
![](../../../assets/images/lb/15.png?classes=border,shadow)

Now, if you want to close the access from Internet to this Load Balancer again, do the following:  
- click on the **Actions** icon and select the **Disassociate Floating IP**;
- confirm your action on the next opened *Confirmation window* by clicking on the DISASSOCIATE icon. 

After these steps, the selected Load Balancer will be again publicly unavailable.

Associate/disassociate Floating IPs you can also from the *Floating IPs page*. To find additional information about Floating IPs use the article: [Floating IPs](https://docs.ventuscloud.eu/products/networking/floating-ips/).


## Delete Load Balancer

To delete the Load Balancer, do the following:
- identify this unnecessary Load Balancer on the *Load Balancers page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Load Balancer deletion on the next opened *Confirmation window*.  
![](../../../assets/images/lb/12.1.png?classes=border,shadow)

After these steps, the selected Load Balancer will be deleted with all its associated resources, including listeners, pools, and health monitors. 

Also, you can delete the Load Balancer from the *Load Balancer details page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/lb/12.png?width=25pc&classes=border,shadow)
