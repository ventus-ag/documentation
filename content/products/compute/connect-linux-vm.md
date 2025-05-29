---
title: Access Linux VM
weight: 15
---
___
On this page, you can find an explanation of how to connect to the Linux Virtual Machine created in the Cloud Console using the SSH Protocol

# Table of contents
- [Table of contents](#table-of-contents)
  - [Prerequisites](#prerequisites)
  - [Configuring Firewalls](#configuring-firewalls)
    - [Create New Firewall with required rule](#create-new-firewall-with-required-rule)
    - [Add required rule to the existing Firewall](#add-required-rule-to-the-existing-firewall)
  - [Connect using SSH](#connect-using-ssh)

## Prerequisites
In this article we will assume, that we have already created the following resources, that refer to the Project named *Test-Project* that was created in the Organization named *Test-Organization*:
- **SSH Key,** that was created with the next parameters:
  - *Name*: main;
  - *Public key* is placed on the Linux VM during its creation;
  - *Private Key* was copied to the clipboard and saved on the local system in the next text file (for example: ~/.ssh/id_rsa).
- **Linux Virtual Machine** - that was created with the next parameters and has IP: 185.226.41.42:
  - *Name*: test-1;
  - *Flavor*: VC-2;
  - *Image*: ubuntu-server-18.04-LTS-20201111;
  - *Key pair*: main;
  - *Networks*: public;
  - *Firewalls*: default;
  - *Volume size*: 50.

💡 For more information about creating and configuring these resources, see the following articles: [SSH Keys](https://docs.ventuscloud.eu/products/security/ssh-keys/), [Virtual Machines](https://docs.ventuscloud.eu/products/compute/virtual-machines/).  

## Configuring Firewalls
By default, all created Virtual Machines belong to the *default* Firewall, which allows access to the Internet from the VM, but denies almost all access on the VM from outside, except for objects belonging to the same default Firewall. Thus, using only the default Firewall, we cannot connect to the selected Virtual Machine remotely via SSH.

{{% notice note %}}
*Default* *Firewall* allows all outbound traffic and controls the inbound traffic that's allowed to reach the VMs that are associated with the *default* *Firewall* too.
{{% /notice %}} 
There are two ways how to resolve this:
1) to add an additional Firewall with a rule that will allow incoming traffic to TCP port 22 on the Virtual Machines and assign this Firewall to the VM too;
2) to add the required rule to the Firewall (can be default Firewall) that is already assigned to the Virtual Machine. 

### Create New Firewall with required rule
**To create new Firewall do the following:**
- open the *Firewalls page* - for this select the **Security** from the VIRTUAL DATACENTER block and click on the FIREWALL TAB:

![](../../../assets/images/cli/1.png?width=15pc&classes=border,shadow) 
![](../../../assets/images/fw/1.png?width=20pc&classes=border,shadow)

- on the *Firewalls page* click on the CREATE FIREWALL icon in the upper left corner;
- fill in the form on the next opened *Create Firewall window* and click on the CREATE icon:

![](../../../assets/images/fw/25.png?width=35pc&classes=border,shadow)

After these steps, the newly created Firewall will be added to the *Firewalls page*.  
📌 As a next step, we need to add an additional Firewall with a rule that will allow incoming traffic to TCP port 22 on the Virtual Machines.  
**To add the described above rule to the newly created Firewall do the following:** 
- open the *Firewall Rules page* - for this click on the **Name** of the corresponding Firewall:

![](../../../assets/images/fw/28.png?classes=border,shadow) 

- on the *Firewall Rules page* you can see that rules, that allow all outbound traffic, have been already created by default, but can be deleted if needed. To add additional rule here click on the CREATE FIREWALL RULE icon in the upper left corner:

![](../../../assets/images/fw/29.png?classes=border,shadow) 

- fill in the form on the next opened *Create Firewall Rule window* as shown below and click on the CREATE icon:

![](../../../assets/images/fw/17.png?width=35pc&classes=border,shadow) 

📝 This newly added rule will allow access to the TCP port 22 on the all VMs in the created Firewall over the public Internet, but if you want to allow access only on the one selected VM, you need to specify *IP of this VM / 32* in the field named *Remote IP prefix* - example is shown below:

![](../../../assets/images/conn-lin/6.png?width=35pc&classes=border,shadow)

After this wee need to add this configured Firewall to our Virtual Machine.   
**To add this newly created Firewall to our Virtual Machine, do the following:**
- open the *Virtual Machines page* - for this select the **Virtual Machines** from the VIRTUAL DATACENTER block:

![](../../../assets/images/conn-lin/7.png?width=15pc&classes=border,shadow)

- open the *Virtual Machine details page* - click on the **Name** of the corresponding Virtual Machine:

![](../../../assets/images/fw/0.png?classes=border,shadow)

- open the NETWORKS & SECURITY TAB, click on the *Actions icon* and select the **Edit Firewalls** in the list of available options:

![](../../../assets/images/conn-lin/23.1.png?classes=border,shadow)

- select our newly created firewall from the list on the opened window and click on SAVE:

![](../../../assets/images/fw/23.png?width=35pc&classes=border,shadow)

After these steps, the newly added Firewall will be added to the selected VM:  
![](../../../assets/images/fw/14.png?classes=border,shadow)  

This is the first option, how we can configure the Firewall for SSH access - by creating a new one with the required rule.    
📝 Alternatively, we can just add this rule to the *default* Firewall, that is already assigned to our VM, and these changes will automatically be applied to the VMs.

### Add required rule to the existing Firewall
{{% notice note %}}
📌 You can add and remove rules at any time. Your changes are automatically applied to the VMs that are associated with the corresponding Firewall.
{{% /notice %}}  

To add required rule to the default Firewall you need to do next:  
- open the *Firewalls page* - for this select the **Security** from the VIRTUAL DATACENTER block and click on the FIREWALL TAB:
![](../../../assets/images/cli/1.png?width=15pc&classes=border,shadow) 
![](../../../assets/images/fw/1.png?width=20pc&classes=border,shadow)

- open the *Firewall Rules page* of the default Firewall- for this click on the **Name** of the corresponding Firewall:
![](../../../assets/images/fw/5.1.png?classes=border,shadow) 

- on the *Firewall Rules page* click on the CREATE FIREWALL RULE icon in the upper left corner;
- fill in the form on the next opened *Create Firewall Rule window* as shown below  and click on the CREATE icon:
![](../../../assets/images/fw/17.png?width=35pc&classes=border,shadow) 

After this, this newly created Firewall Rule will be automatically applied to all Virtual Machine that were attached with this default Firewall.

## Connect using SSH
Since we have the public key deployed on our Linux VM, the private key on our local system (for example ~/.ssh/id_rsa) and a Firewall configured to allow incoming traffic on port 22, we can connect to this Virtual Machine remotely from our local server via SSH, just use the next command: 
`ssh -i ~/.ssh/id_rsa username@10.111.22.333`

{{% notice note %}}
The default usernames for various Linux distributions are as follows:  
  ☑️ Debian - "debian";  
  ☑️ Fedora - "fedora";  
  ☑️ Fedora CoreOS - "core";  
  ☑️ CentOS 7, CentOS 8 - "centos";  
  ☑️ CentOS 9 and later versions - "cloud-user".  

🪄 In the case of Windows, the default username is set as "ventus".
{{% /notice %}} 

Replace *username* and *10.11.22.333* in the command with your data and specify the appropriate path to your private key. In our example, the command will look like this:
`sudo ssh -i ~/.ssh/id_rsa ubuntu@185.226.41.42`
![](../../../assets/images/conn-lin/13.png?classes=border,shadow)

After successfully connecting, you can check your internet access and try pinging [google.com](http://google.com/):
![](../../../assets/images/conn-lin/14.png?classes=border,shadow)
