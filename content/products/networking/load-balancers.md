---
title: Load Balancers
weight: 21
draft: true
---
___
On this page, you can find an explanation of how to create, edit, delete Load Balancer and instructions for other steps to manage it in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Load Balancers page](#load-balancers-page)
  - [Create Load Balancer](#create-load-balancer)
  - [Load Balancer details page](#load-balancer-details-page)
    - [Listeners](#listeners)
      - [Create Listener](#create-listener)
      - [Listener details page](#listener-details-page)
      - [Edit Listener](#edit-listener)
      - [Delete Listener](#delete-listener)
    - [Pools](#pools)
      - [Create Pool](#create-pool)
      - [Pool details page](#pool-details-page)
      - [Edit Pool](#edit-pool)
      - [Delete Pool](#delete-pool)
    - [Pool Members](#pool-members)
      - [Add Pool Member](#add-pool-member)
      - [Edit Pool Member](#edit-pool-member)
      - [Delete Pool Member](#delete-pool-member)
    - [Health Monitors](#health-monitors)
      - [Create Health Monitor](#create-health-monitor)
      - [Edit Health Monitor](#edit-health-monitor)
      - [Delete Health Monitor](#delete-health-monitor)
  - [Edit Load Balancer](#edit-load-balancer)
  - [Associate/Disassociate Floating IP](#associatedisassociate-floating-ip)
  - [Delete Load Balancer](#delete-load-balancer)

## Introduction
**Load Balancer (LB)** helps distribute incoming traffic across multiple backend servers to ensure high availability and better performance. It provides a single access point to your application and automatically reroutes traffic if a server becomes unavailable. 

Load Balancer is a layered, multi-component entity. It always works in combination with:
- **Listeners** – define how incoming traffic is accepted (by protocol and port).  
  Load Balancer can have multiple listeners, but each must use a unique port.
- **Pools** – group backend servers (members) to which traffic is distributed.  
  Each listener can be associated with one pool, and the pool’s protocol must be identical or compatible with the listener’s protocol.  
- **Pool Members** – individual virtual machines that handle the actual traffic.  
  Each pool can contain multiple members. 
- **Health Monitor** – checks the status of each pool member to ensure traffic is only sent to healthy servers.  
  Each pool can have only one health monitor assigned.

These components work together to provide a flexible and reliable traffic distribution system.

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

Additionally, you can access the details of any created Load Balancer by clicking on its **name**. This will take you to the *Load Balancer Details page*, where you’ll find comprehensive information about its listeners and pools. From there, you can manage pools and listeners, and perform other actions related to the selected Load Balancer.  
More information about the *Load Balancer details page* will be provided in the following sections.   
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
  - *Pool Algorithm* - select how traffic should be distributed among pool members:   
      ROUND ROBIN – evenly distributes traffic across all members.  
      LEAST CONNECTIONS – sends traffic to the member with the fewest active connections.     
      SOURCE IP – keeps traffic from the same source IP directed to the same member.  
  - *Session Persistence* - define how user sessions stay connected to the same backend servers:  
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

After these steps, the newly created Load Balancer will be added to the *Load Balancers page* and you can click on its **name** to navigate to the *Load Balancer details page* to view all necessary information about it, including created listener, pool, and configured health monitor.  
![](../../../assets/images/lb/16.png?classes=border,shadow)
More information about the *Load Balancer details page* will be provided in the following sections.  

## Load Balancer details page
To open the *Load Balancer details page*, click on the **name** of the corresponding LB on the *Load Balancers page*:
![](../../../assets/images/lb/4.png?classes=border,shadow)

This action will redirect you to the *Load Balancer details page*, where you can find:  
- **details section** showing key information about the selected Load Balancer;  
- **quick actions panel**: edit, delete, associate/disassociate floating IP;  
- **two tabs**: Listeners and Pools.
![](../../../assets/images/lb/6.png?width=30pc&classes=border,shadow)
  
### Listeners 
**Listeners** define how the Load Balancer receives and handles incoming traffic based on protocol and port. Load Balancer may have multiple listeners, each independently configured to handle incoming connections on a specific port and protocol.  
All listeners associated with the same Load Balancer must use distinct ports to avoid conflicts.

**LISTENERS TAB** on the *Load Balancer details page* - displays all listeners associated with the selected Load Balancer.   
From here, it is possible to:  
- create new listeners;  
- manage (edit/delete/change associated pool) existing ones; 
- navigate to the *Listener details page* by clicking on the listener's **name**.   
![](../../../assets/images/lb/7.png?classes=border,shadow)  

On the *Listener details page* you can:
- view detailed information about the listener and its related components, including the Load Balancer it belongs to, the associated pool, and the health monitor;
- manage the listener itself (edit, delete);
- manage related components such as the pool and health monitor;  
- add or remove pool members from the associated pool;  
![](../../../assets/images/lb/17.png?classes=border,shadow)  

More information about the *Listener details page* will be provided in the following sections. 

#### Create Listener
{{% notice note %}}
Multiple listeners can be associated with the same Load Balancer but each must use a unique port.
{{% /notice %}}

To create new Listener that will be tied to the current LB, do the following:
- open the LISTENERS TAB on the *Load Balancer details page* and click on the CREATE LISTENER icon in the upper left corner;
- fill in the form on the next opened *Create Listener window*:

![](../../../assets/images/lb/19.png?width=30pc&classes=border,shadow)
  - *Name* - set a name for the listener; 
  - *Listener Protocol* - choose the protocol the listener will use to accept incoming traffic (e.g., HTTP, TCP);       
  - *Listener Port* - enter a port number between 1 and 65535. Each listener on the same Load Balancer must use a unique port;  
  - *Connection Limit* - set the maximum number of simultaneous client connections. Use -1 for unlimited connections;  
  - *Client Data Timeout* - time (in milliseconds) the listener will wait for client activity before closing the connection. Default: 50000;  
  - *Member Connect Timeout* - time (in milliseconds) to wait while establishing a connection to a backend member. Default: 5000;  
  - *Member Data Timeout* - time (in milliseconds) the listener will wait for data from a backend member before timing out. Default: 50000;  
  - *Default Pool* - select or create a pool to be used by this listener. Only unassigned pools with a compatible protocol can be selected. This field is optional, you can attach a pool later by using the Edit Listener action.

After these steps, the newly created Listener will be added to the LISTENERS TAB on the *Load Balancer details page* and you can click on its **name** to navigate to the *Listener details page*:
![](../../../assets/images/lb/20.png?classes=border,shadow)

More information about the *Listener details page* will be provided in the following sections.  

#### Listener details page
To open the *Listener details page*, click on the **name** of the corresponding Listener on the *LISTENERS TAB* in the *Load Balancer details page*:
![](../../../assets/images/lb/28.png?classes=border,shadow)

This action will redirect you to the *Listener details page*, where you can find:  
- **listener details section**, showing key information about the selected Listener, with available **quick actions panel**: edit, delete;   
![](../../../assets/images/lb/29.png?width=35pc&classes=border,shadow)

- **information block** that displays details about the listener's related components — including the Load Balancer it belongs to, the assigned pool, and the configured health monitor. Each component has its own quick actions panel for easy management:  
![](../../../assets/images/lb/30.png?classes=border,shadow)  

- **pool members section**, listing all backend members of the associated pool. This section includes a *Create button*, *Search bar*, and an *actions icon* for each member, which opens a menu with available management actions for the selected member: 
![](../../../assets/images/lb/31.png?classes=border,shadow)  

#### Edit Listener
{{% notice note %}}
Using the Edit Listener action, you can not only update the general information of the listener, but also change its assigned pool.
{{% /notice %}}

To edit the Listener, do the following:
- identify Listener, that you want to edit, on the the LISTENERS TAB on the *Load Balancer details page*;  
- click on the **Actions** icon and select the **Edit** in the list of available options;   
![](../../../assets/images/lb/21.png?classes=border,shadow)
- update desired settings on the next opened *Edit Listener window*:  
![](../../../assets/images/lb/22.png?width=30pc&classes=border,shadow)

After these steps, the selected Listener will be updated.   

Also, you can edit the Listener from:  
- the *Listener Details page* – by clicking on the appropriative **quick actions** icon at the top:   
![](../../../assets/images/lb/23.png?width=35pc&classes=border,shadow)  

- the *Pool Details page* - by clicking the **edit icon** in the Listener information block:   
![](../../../assets/images/lb/24.png?classes=border,shadow)   

#### Delete Listener

To delete the Listener, do the following:
- identify this unnecessary Listener on the on the LISTENERS TAB on the *Load Balancer details page*;  
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Listener deletion on the next opened *Confirmation window*.  
![](../../../assets/images/lb/26.png?classes=border,shadow)

After these steps, the selected Listener will be deleted. 

Also, you can delete the Listener from:  
- the *Listener Details page* – by clicking on the appropriate **quick actions** icon at the top:   
![](../../../assets/images/lb/25.png?width=35pc&classes=border,shadow)  


### Pools  
**Pool** is a group of backend servers (members) that receive traffic distributed by the Load Balancer.  
Each pool can be attached to one listener, but only if the pool and listener use the same or compatible protocol.  

**POOLS TAB** on the *Load Balancer details page* lists all pools created under the selected Load Balancer.  
From here, it is possible to:  
- create new pools;  
- edit or delete existing ones;  
- navigate to the *Pool Details page* by clicking on the pool’s **name**.  
![](../../../assets/images/lb/8.png?classes=border,shadow)  

On the *Pool Details page*, you can: 
- find all relevant information about the selected pool and its related components, including the Load Balancer  and Listener it belongs to, and the configured health monitor;;  
- manage the pool itself (edit, delete);   
- manage related components such as the listener and health monitor;  
- add or remove pool members;  
![](../../../assets/images/lb/18.png?classes=border,shadow)  

More information about the *Pool details page* will be provided in the following sections.  


#### Create Pool

To create new Pool associated to the current load balancer, do the following:
- open POOLS TAB on the *Load Balancer details page* and click on the CREATE POOL icon in the upper left corner;
- fill in the form on the next opened *Create Pool window*:

![](../../../assets/images/lb/32.png?width=30pc&classes=border,shadow)
  - *Name* - set a name for the pool; 
  - *Pool Protocol* - choose the protocol that this pool and its members will use to receive traffic (e.g., HTTP, TCP);  
  - *Pool Algorithm* - select how traffic should be distributed among pool members:   
      ROUND ROBIN – evenly distributes traffic across all members.  
      LEAST CONNECTIONS – sends traffic to the member with the fewest active connections.     
      SOURCE IP – keeps traffic from the same source IP directed to the same member.  
  - *Session Persistence* - define how user sessions stay connected to the same backend servers:  
      SOURCE IP – based on source IP address.  
      HTTP COOKIE – based on an HTTP cookie.  
      APP COOKIE – based on an application-specific cookie.  
  - *Default Listener* - optionally, you can select a listener to associate this pool with. Only listeners without a pool and using a compatible protocol will be listed. If you skip this step, you can attach the pool to a listener later using the *Edit Listener action*.

After these steps, the newly created Pool will be added to POOLS TAB on the *Load Balancer details page* and you can click on its **name** to navigate to the *Pool details page*:
![](../../../assets/images/lb/33.png?classes=border,shadow)

More information about the *Pool details page* will be provided in the following sections.  

#### Pool details page
To open the *Pool details page*, click on the **name** of the corresponding Pool on the *POOL TAB* in the *Load Balancer details page*:
![](../../../assets/images/lb/34.png?classes=border,shadow)

This action will redirect you to the *Pool details page*, where you can find:  
- **pool details section**, showing key information about the selected Pool, with available **quick actions panel**: edit, delete;   
![](../../../assets/images/lb/35.png?width=30pc&classes=border,shadow)

- **information block** that displays details about the pool's related components — including the Load Balancer and Listener it belongs to, and the configured health monitor. Each component has its own quick actions panel for easy management:  
![](../../../assets/images/lb/36.png?classes=border,shadow)  

- **pool members section**, listing all backend members of the associated pool. This section includes a *Create button*, *Search bar*, and an *actions icon* for each member, which opens a menu with available management actions for the selected member: 
![](../../../assets/images/lb/31.png?classes=border,shadow)  


#### Edit Pool

To edit the Pool, do the following:
- identify Pool, that you want to edit, on POOLS TAB on the *Load Balancer details page*;  
- click on the **Actions** icon and select the **Edit** in the list of available options;   
![](../../../assets/images/lb/37.png?classes=border,shadow)
- update desired settings on the next opened *Edit Pool window*:  
![](../../../assets/images/lb/38.png?width=30pc&classes=border,shadow)

After these steps, the selected Pool will be updated.   

Also, you can edit the Pool from:  
- the *Pool Details page* – by clicking on the appropriate **quick actions** icon at the top:   
![](../../../assets/images/lb/39.png?width=30pc&classes=border,shadow)  

- the *Listener Details page* - by clicking the **edit icon** in the Pool information block:   
![](../../../assets/images/lb/40.png?classes=border,shadow)   

#### Delete Pool

To delete the Pool, do the following:
- identify this unnecessary Pool on the on POOLS TAB on the *Load Balancer details page*;  
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Pool deletion on the next opened *Confirmation window*.  
![](../../../assets/images/lb/41.png?classes=border,shadow)

After these steps, the selected Pool will be deleted. 

Also, you can delete the Pool from:  
- the *Pool Details page* – by clicking on the appropriate **quick actions** icon at the top:   
![](../../../assets/images/lb/43.png?width=30pc&classes=border,shadow)  

- the *Listener Details page* - by clicking the **remove icon** and selecting *Delete* in the Pool information block:   
![](../../../assets/images/lb/42.png?classes=border,shadow)   

### Pool Members 
**Pool Members** are the actual Virtual Machines that handle traffic forwarded by the Load Balancer.

You can view and manage Pool Members from the *Listener Details page* or from the *Pool Details page* — both pages include a **pool Members section**, listing all backend members of the associated pool:
![](../../../assets/images/lb/31.png?classes=border,shadow)  

#### Add Pool Member

To add a Pool Member, do the following:  
- navigate to the **pool Members section** on either the *Pool details page* or *Listener details page* and click on the ADD POOL MEMBER button:  
![](../../../assets/images/lb/51.png?classes=border,shadow)
- fill in the form on the next opened *Add Pool Member window*:  
![](../../../assets/images/lb/52.png?width=30pc&classes=border,shadow)
  - *Virtual Machine* - select the virtual machine that should receive traffic from the Load Balancer;  
  - *IP Address* - choose the network interface (IP address) of the selected VM that will be used for traffic;   
  - *Subnet* - optionally specify the subnet from which the member's service is accessible.  If omitted, parent lb's subnet will be used;  
  - *Protocol Port* -  set the port on which the member will receive traffic (e.g., 80, 443).;  
  - *Weight* - define how much traffic this member should handle relative to others. Range: 1–256;  
  - *Backup Member* - enable this option if the member should only receive traffic when all primary members are unavailable.  
  
After these steps, the Pool Member will be added and linked to the selected Load Balancer.

#### Edit Pool Member
To edit the Pool Member, do the following:  
- identify Pool Member, that you want to edit, on the *Pool details page* or *Listener details page*;  
- click on the **Actions** icon and select the **Edit** in the list of available options;  
![](../../../assets/images/lb/53.png?classes=border,shadow)
- update desired settings on the next opened *Edit Pool Member window*: 
![](../../../assets/images/lb/54.png?width=30pc&classes=border,shadow)

After these steps, the selected Pool Member will be updated.  

#### Delete Pool Member

To delete the Pool Member from the Load Balancer's pool, do the following:
- identify this unnecessary Pool Member on the *Pool details page* or *Listener details page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Pool Member deletion on the next opened *Confirmation window*.  
![](../../../assets/images/lb/55.png?classes=border,shadow)

After these steps, the selected Pool Member will be removed from the Load Balancer's pool — but the underlying virtual machine will not be deleted from the project.

### Health Monitors 
**Health Monitor** is used to check the status of each member in the pool. It regularly performs health checks, and only members that pass these checks will continue to receive new traffic from the Load Balancer.

{{% notice note %}}
Each Pool can only have one Health Monitor assigned to it.
{{% /notice %}}

You can access to the details and manage the configured Health Monitor from:  
- *Listener Details page*, if the Listener has a Pool assigned:  
![](../../../assets/images/lb/44.png?classes=border,shadow)  
- *Pool Details page*, where the Health Monitor is always visible and manageable:  
![](../../../assets/images/lb/45.png?classes=border,shadow)  

#### Create Health Monitor
{{% notice note %}}
Each Pool can only have one Health Monitor assigned to it.
{{% /notice %}}

To create the Health Monitor, do the following:  
- identify the Pool, where you want to add a Health Monitor and navigate to its *Pool details page*;   
- click on the CREATE HEALTH MONITOR in the *Health Monitor section*:     
![](../../../assets/images/lb/49.png?classes=border,shadow)
- fill in the form on the next opened *Create Health Monitor window*:  
![](../../../assets/images/lb/50.png?width=30pc&classes=border,shadow)
  - *Name* - set a name for the health monitor; 
  - *Health Monitor Type* - choose the protocol for health checks (e.g., HTTP, TCP);  
  - *Timeout* - time (in seconds) to wait for a response before marking the check as failed;    
  - *Delay* -  interval (in seconds) between consecutive health checks. Must be greater than or equal to the timeout;  
  - *Max Retries* - number of failed checks before marking the member as inactive. Must be a number from 1 to 10;  
  - *Max Retries Down* - number of failures before marking the member as in error. Must be a number from 1 to 10;  
  - *HTTP Method* - the HTTP method used for the health check (e.g., GET);  
  - *Expected Codes* - expected HTTP status codes that indicate a healthy response (can be a number, list, or range);  
  - *URL Path* - the endpoint path for the health check (e.g., /health).

After these steps, the Health Monitor will be created and attached to the selected Pool.

Also you can create a Health Monitor from the *Listener Details page* — if the Listener is linked to a Pool that doesn't yet have a Health Monitor assigned.

#### Edit Health Monitor
To edit the Health Monitor, do the following:  
- identify Pool, which Health Monitor you want to edit and navigate to this *Pool details page*;   
- click on the **edit icon** in the Health Monitor information block:     
![](../../../assets/images/lb/46.png?classes=border,shadow)
- update desired settings on the next opened *Edit Health Monitor window*:  
![](../../../assets/images/lb/47.png?width=30pc&classes=border,shadow)

After these steps, the selected Health Monitor will be updated.   

Also you can access and edit the Health Monitor from the *Listener Details page* — if the Listener is associated with Pool that has a Health Monitor configured.

#### Delete Health Monitor

To delete the Health Monitor, do the following:
- identify Pool, which Health Monitor you want to delete and navigate to this *Pool details page*;   
- click on the **delete icon** in the Health Monitor information block:     
- confirm the Health Monitor deletion on the next opened *Confirmation window*.  
![](../../../assets/images/lb/48.png?classes=border,shadow)

After these steps, the selected Health Monitor will be deleted. 

Also you can access and delete the Health Monitor from the *Listener Details page* — if the Listener is associated with Pool that has a Health Monitor configured.

## Edit Load Balancer
To edit the Load Balancer, do the following:  
- identify Load Balancer, that you want to edit, on the *Load Balancers page*;  
- click on the **Actions** icon and select the **Edit** in the list of available options;  
![](../../../assets/images/lb/10.1.png?classes=border,shadow)
- update desired settings, such as the name, description, and administrative state on the opened dialog: 
![](../../../assets/images/lb/10.png?width=30pc&classes=border,shadow)

After these steps, the selected Load Balancer will be updated.  

Also, you can edit the Load Balancer directly from its related detail pages:  
- on the *Load Balancer details page* - by clicking on the appropriate **quick actions** icon at the top:   
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

Also, you can delete the Load Balancer from the *Load Balancer details page*, by clicking on the appropriate **quick actions** icon there:
![](../../../assets/images/lb/12.png?width=25pc&classes=border,shadow)


