---
title: Groups
weight: 30
---
___
On this page, you can find an explanation of how to create and manage a new Group in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Groups page](#groups-page)
  - [Create Group](#create-group)
  - [Configure Group](#configure-group)
    - [Manage Projects in Group](#manage-projects-in-group)
    - [Manage Users in Group](#manage-users-in-group)
  - [Edit Group](#edit-group)
  - [Delete Group](#delete-group)

## Groups page

{{% notice note %}}
In the Cloud Console, using Groups lets you add users to your project within your organization. As 'members' of your organization they can access specified project resources but can't add or remove users, view admin or billing details, create or edit projects within that organization.
{{% /notice %}}  

To get to the *Group page*, select the **Groups** from the *side-bar menu*:
![](../../assets/images/groups/1.png?width=15pc&classes=border,shadow) 

On this page you can find all created Groups, related to the selected Organization with the *Create button, Search bar*, and *Actions icon*, which opens a list of available management actions for the selected Group:
![](../../assets/images/groups/0.png?width=50pc&classes=border,shadow)  

**Actions** icon opens the next list of available management actions:
- *Edit* - this option is using to change the Group name;
- *Delete* - this option is using to remove the Group.

## Create Group
To create a new Group, do the following:
- go to the *Groups page* and click on the CREATE GROUP icon in the upper left corner;
- specify the **Name** of the Group on the next opened *Create Group window* and click on the CREATE icon:

![](../../assets/images/groups/2.png?width=30pc&classes=border,shadow) 

After these steps, the newly created Group will be added to the *Groups page*.  

As the next step, is recommended to configure the created Group.

## Configure Group
To set up the Group membership and permissions you can from the *Group details page.*  
To get to the *Group details page* click on the **Name** of the corresponding Group:
![](../../assets/images/groups/3.png?width=50pc&classes=border,shadow) 

On the *Group details page* you can see two blocks: the first top block displays a list of Projects, and the second one shows Users (Members) who was assigned to work with these projects:
![](../../assets/images/groups/4.png?width=50pc&classes=border,shadow) 

So, from this page you can:
- **review** which Users have access to which Projects;
- **add** more Users to the selected Projects;
- **assign** more Projects to the selected Users;
- **remove Users** from the selected Projects;
- **remove Projects** from access of selected Users;

### Manage Projects in Group

{{% notice note %}}
You can add as many Projects to the Group as you need.
{{% /notice %}}

To add the Project to the selected Group, do the following:
- go to the *Group details page* and click on the ASSIGN PROJECT icon;
- select the Project, to which you want to assign Users, from the second block, and click on the ASSIGN icon:

![](../../assets/images/groups/8.png?width=30pc&classes=border,shadow)

After these steps, the newly added Project will appear in the first block of the *Group details page* with active *Actions icon*: 
![](../../assets/images/groups/9.png?width=50pc&classes=border,shadow)

**Actions** icon after accepting invitation opens the next list of available management actions:  
- *Remove* - this option is using to delete the Project from the Group.

Users from the second block will have access to this Project and, accordingly, to all resources in this Project, but they will not be able to add new projects to this Organization, see billing Information and manage the Groups and Administrators of the Organization that owns this Project.


### Manage Users in Group

{{% notice note %}}
You can add as many Users and Projects to the Group as you need. Their organizational role will be "Member", and they will only have access to the current project.
{{% /notice %}}

{{% notice note %}}
You can add only those Users, who have already passed the registration stage in the Cloud Console.  
If you need to add a User who isn't yet registered, you can create an account in the Cloud Console for the user before adding them as a Member to the selected Group.
{{% /notice %}}   

**Add a Member to the Group (Registered User):**
To add a new User to the selected Group, do the next:
- go to the *Group details page* and click on the ADD MEMBER button;
- specify the **E-mail address** of the User, that you want to add to the group, and click on the SEND INVITATION icon:

![](../../assets/images/groups/5.png?width=30pc&classes=border,shadow) 

**Add a Member to the Group (New User):**
If the user isn't yet registered, you can create an account in the Cloud Console for the user before adding them as a Member to the selected Group. To do it, follow these steps:  
- go to the *Group details page* and click on the ADD MEMBER button;
- on  the next opened *Add Member window* check the **Register new user** checkbox:  
![](../../assets/images/groups/14.png?width=30pc&classes=border,shadow)  
- fill in the form on the next opened *Register new user window* and click on the REGISTER button:
![](../../assets/images/groups/13.png?width=30pc&classes=border,shadow)  
- after completing the registration, return to the *Add Member window*, enter the newly registered email address and click on the SEND INVITATION button: 
![](../../assets/images/groups/12.png?width=30pc&classes=border,shadow)  
 

After this, the User, whose email address you entered in the invitation, will receive an email with the *Accept invitation link*. By clicking on this link, the user will be redirected to the Cloud Console, where he need to click the *ACCEPT INVITATION* icon.      

And on the yours *Group details page* you will see the added information about your invitation with the active **Actions** icon:
![](../../assets/images/groups/6.png?width=50pc&classes=border,shadow)

**Actions** icon in this step opens the next list of available management actions:  
- *Resend invitation* - this option is using to send one more invitation with the *Accept invitation link*.
- *Delete invitation* - this option is using to block the *Accept invitation link* in the invitation.

When the invited User accepts your invitation, he will get access to the Projects, that you provided in the appropriate Group, and on your *Group details page* you will see this newly added User with active *Actions icon*:
![](../../assets/images/groups/7.png?width=50pc&classes=border,shadow) 

**Actions** icon after accepting invitation opens the next list of available management actions:  
- *Remove* - this option is using to delete the User from the Group.

After these steps, invited User becomes a Member of the current Organization and has access only to the assigned Project:
![](../../assets/images/groups/11.png?width=50pc&classes=border,shadow) 

{{% notice note %}}
Member - this role is assigned to a User who is granted access to the Organization's Project and, accordingly, to all resources within this Project. Member can't add/remove other Users in the Project, can't see information about Administrators or Billing of the Organization/Project, can't add new Projects, edit or delete current one. 
{{% /notice %}}  

## Edit Group
To edit the Group, do the following:
- identify the Group, that you want to edit, on the *Groups page*;
- click on the **Actions** icon and select the **Edit** in the list of available options;
- update the Name of the selected Group on the next opened *Edit Group window*,  and click on the SAVE icon.

After these steps, the selected Group will be updated.

## Delete Group
To delete the Group, do the following:
- identify the unnecessary Group on the *Groups page*;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Group deletion on the next opened *Confirmation window*.

After these steps, the selected Group will be deleted.


