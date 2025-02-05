---
title: Organizations
weight: 15
---
___
On this page, you can find an explanation of how to create a new Organization and how to manage it in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Users within Organization](#users-within-organization)
  - [Organizations page](#organizations-page)
  - [Create Organization](#create-organization)
  - [Edit Organization](#edit-organization)
  - [Delete Organization](#delete-organization)
  - [Leave Organization](#leave-organization)
  - [Add Administrators](#add-administrators)
  - [Transfer an Organization](#transfer-an-organization)

## Users within Organization

In the Cloud Console Organizations User can have next Roles:  
- **Owner** - this role is assigned to a User, who created this Organization (this User will also be considered the *Administrator* of this Organization) and opens access to all resources of the Organization including the management of Groups, Projects and their all Users;  
- **Administrator** - this role can be assigned to a User by another Administrator of the Organization. Administrators have access to all resources of the Organization, including the management of Groups, Projects and their Users, but they can't edit or delete Organization;  
- **Member** - this role is assigned to a User who is granted access to the Organization's Project and, accordingly, to all resources within this Project. Member can't add/remove other Users in the Project, can't see information about Administrators or Billing of the Organization, can't add new Projects, edit or delete current one.  

As a *Owner* or *Administrator* you can add additional Admins to the Organization, which will also have access to all resources of the Organization.  
Detailed instructions, how to add new Administrators to the Organization you can find in article - [Administrators](https://docs.ventuscloud.eu/identity-management/administrators/).

Also you can create a Group and open access only to specified Projects of the Organizations. Users, who you invite to the Group will be just an Organization Members, with very limited management actions within Organization.  
How to create and configure Group, please see the article - [Groups](https://docs.ventuscloud.eu/identity-management/groups/)

## Organizations page

If you are a new user and have just created new account, you will be automatically redirected to the *Organizations page*, where you can create your first Organization or find a list of Organizations, to which Projects your User has access as a *Member* or *Administrator*:  
![](../../../assets/images/organizations/10.png?classes=border,shadow)  

If you aren't a new User, but want to see information about created Organizations or find information about Organizations to which Projects your User has access, you need to select the **Organizations** from the *side-bar menu:* 
![](../../../assets/images/organizations/2.png?width=15pc&classes=border,shadow)  

This action will redirect you to the *Organizations page*, where you can find all created Organizations and Organizations, to which Projects your User has access, with the *Add Organization button, Search bar* and *Actions icon* which opens a list of available management actions for the selected Organization.

**Actions** icon opens the list of available management actions, which differ depending on the user's role in the Organization: 
  * **for Owners:**
    - *Edit* - this option is using to change the name of the selected Organization.  
    - *Delete* - this option is using to delete the Organization.
  * **for Administrators and Members**  
    - *Leave* - this option can be used to leave the Organization.  

Additionally, from this page, you can navigate to the *Projects page* or *Administrators page* of each created Organization by clicking on its **name**. More information about this pages you can find here - [Projects page](https://docs.ventuscloud.eu/getting-started/projects/#projects-page), [Administrators page](https://docs.ventuscloud.eu/identity-management/administrators/#administrators-page).

![](../../assets/images/organizations/3.png?classes=border,shadow)  

## Create Organization 
To create a new Organization, do the following:  
- go to the *Organizations page* and click the CREATE ORGANIZATION icon in the upper left corner;    
- specify the **Name** of the Organization and click on the CREATE icon:  

![](../../assets/images/organizations/4.png?width=35pc&classes=border,shadow)  

After these steps the newly created Organization will be added to the *Organizations page* with User Role *Owner* and you can navigate to its *Projects page* by clicking on Organization **name**. More information about this page you can find here - [Projects page](https://docs.ventuscloud.eu/getting-started/projects/#projects-page).  
![](../../assets/images/organizations/5.png?classes=border,shadow)

## Edit Organization
{{% notice note %}}
This action is available only if User Role in this Organization is *Owner*.
{{% /notice %}}

To edit the Organization, do the following:
- identify, what Organization you want to edit, on the *Organizations page*;   
- click on the **Actions** icon and select the EDIT in the list of available options;    
- update the name of the Organization on the next opened *Edit Organization window* and click on the SAVE icon.     

After these steps, the selected Organization will be updated.

Also, you can edit the Organization from its *Projects page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/organizations/14.png?width=25pc&classes=border,shadow)

## Delete Organization

{{% notice note %}}
This action is available if User Role in this Organization is *Owner* and all Projects inside, were previously deleted.
{{% /notice %}}

To delete the Organization, do the following:
- identify this unnecessary Organization on the *Organizations page*;   
- click on the **Actions** icon and select the DELETE in the list of available options;    
- confirm the Organization deletion on the next opened *Confirmation window*. 
      
After confirming this action, the selected Organization will be deleted.

Also, you can delete the Organization from its *Projects page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/organizations/15.png?width=25pc&classes=border,shadow)

## Leave Organization
{{% notice note %}}
This action is available if User Role in this Organization is *Administrator* or *Member*.
{{% /notice %}}

To leave the Organization, do the following:
- identify Organization on the *Organizations page* that you want to leave;   
- click on the **Actions** icon and select the LEAVE option;    
- confirm your action on the next opened *Confirmation window*. 
      
After these steps, your User will not have access to the selected Organization.

Also, you can leave the Organization from its *Projects page*, by clicking on the appropriative **quick actions** icon there:
![](../../../assets/images/organizations/16.png?width=25pc&classes=border,shadow)

## Add Administrators

{{% notice note %}}
To see information about Administrators of the Organization and to manage them, you can only if your User Role in this Organization is an *Administrator* or *Owner*.   
{{% /notice %}}

To see information about Administrators of the Organization, go to the *Organizations page* and click on the **Name** of the Organization:  
![](../../assets/images/organizations/7.png?classes=border,shadow)  

It will open next additional sections on the *side-bar menu,* from which you need to select **Administrators**:
![](../../../assets/images/organizations/0.png?width=15pc&classes=border,shadow) 

This action will redirect you to the *Administrators page*, where you can find all Administrators, related to this Organization:  
![](../../assets/images/organizations/9.png?width=35pc&classes=border,shadow)  

From this page you can: 
- Add Administrators to the Organization (already registered users);
- Register new users and add them as an Administrators to the Organization;
- Remove Administrators;
- Transfer an Organization;

To see detailed instructions about each action, please see the next article:  
[Administrators](https://docs.ventuscloud.eu/getting-started/administrators/).  

## Transfer an Organization
{{% notice note %}}
Transferring Organization is available only if your User Role in this Organization is *Owner*. 
{{% /notice %}}

As a Owner of the organization you can transfer the ownership to another Administrator of this Organization 

For this, do the following:  
- open the *Administrators page*:

![](../../../assets/images/organizations/0.png?width=15pc&classes=border,shadow) 
- identify the Administrator, to whom you want to Transfer the Organization;    
- click on the **Actions** icon and select the **Transfer the Organization** in the list of available options:

![](../../assets/images/projects/6.png?classes=border,shadow)    
- confirm your actions on the next opened *Confirmation window* and click on the SEND icon. 

After confirming this action, the selected User will receive the message with the invitation to become an owner of the specifying Organization and if he accept it, his Role in the selected Organization will be changed from *Administrator* to *Owner*. 