---
title: Administrators
weight: 20
---
___
On this page, you can find an explanation of how to register new Users and to add them as a new Administrator to the Organization, how to transfer the Organization to another User and how to remove Administrator from the Organization in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Administrators page](#administrators-page)
  - [Add Administrator](#add-administrator)
    - [Resend Invitation](#resend-invitation)
    - [Delete Invitation](#delete-invitation)
  - [Transfer Organization](#transfer-organization)
  - [Remove Administrator](#remove-administrator)

## Administrators page

{{% notice note %}}
To see information about Administrators of the Organization and to manage them, you can only if your User Role in this Organization is an *Administrator* or *Owner*.   
{{% /notice %}}

To see information about Administrators of the Organization, go to the *Organizations page* and click on the **Name** of the Organization:  
![](../../assets/images/organizations/7.png?classes=border,shadow)  

It will open next additional sections on the *side-bar menu,* from which you need to select **Administrators**:
![](../../../assets/images/organizations/0.png?width=15pc&classes=border,shadow) 

This action will redirect you to the *Administrators page*, where you can find all Administrators, related to this Organization with the *Add Administrator button* and *Search bar*:  
![](../../assets/images/organizations/9.png?width=45pc&classes=border,shadow)  

## Add Administrator
{{% notice note %}}
You can add only those Users, who have already passed the registration stage in the Cloud Console and aren't members of one of the Projects of this Organization. 
{{% /notice %}}   

{{% notice note %}}
If you need to add a user who is not yet registered, you can create an account in the Cloud Console for the user before adding them as an Administrator to the selected Organization.
{{% /notice %}}   

**Add an Administrator (Registered User):**   
To add new Administrator, who is already registered in the Cloud Console, to the selected Organization, do the following:   
- go to the *Administrators page* and click the ADD ADMINISTRATOR icon in the upper left corner;      
- specify the **E-mail address** of the User that you want to add to your Organization and click on the SEND INVITATION button: 
 
![](../../assets/images/organizations/11.png?width=35pc&classes=border,shadow)   

**Add an Administrator (New User):**   
If the user is not yet registered, you can create an account in the Cloud Console for the user before adding them as an Administrator to the selected Organization. To do it, follow these steps:  
- go to the *Administrators page* and click the ADD ADMINISTRATOR icon in the upper left corner;  
- on  the next opened *Add Administrator window* check the **Register new user** checkbox: 
![](../../assets/images/organizations/17.png?width=35pc&classes=border,shadow)  
- fill in the form on the next opened *Register new user window* and click on the REGISTER button:
![](../../assets/images/organizations/18.png?width=35pc&classes=border,shadow)  
- after completing the registration, return to the *Add Administrator window*, enter the newly registered email address and click on the SEND INVITATION button: 
![](../../assets/images/organizations/19.png?width=35pc&classes=border,shadow)  
 

After this, the User, whose email address you entered in the invitation, will receive an email with the *Accept invitation link*. By clicking on this link, the user will be redirected to the Cloud Console, where he need to click the *ACCEPT INVITATION* icon.      

And on the yours *Administrators page* you will see the added information about your invitation with the active **Actions** icon:
![](../../assets/images/organizations/12.png?width=45pc&classes=border,shadow)  
**Actions** icon in this step opens the next list of available management actions:  
- *Resend invitation* - this option is using to send one more invitation with the *Accept invitation link*.
- *Delete invitation* - this option is using to block the *Accept invitation link* in the invitation.

When the invited User accepts your invitation, he will get an Administrator role in appropriate Organization and the access to all resources of it and on your *Administrators page* you will see this newly added Administrator with active *Actions icon*:
![](../../assets/images/organizations/13.png?width=45pc&classes=border,shadow)  

**Actions** icon after accepting invitation opens the next list of available management actions:  
- *Transfer an organization* - this option is using to change the Owner of the selected Organization.  
- *Remove* - this option is using to delete the Administrator from the Organization. 

### Resend Invitation 
To resend an invitation, do the next:
- click on the **Actions** icon and select the RESEND INVITATION option in the list of available;
- confirm you actions on the next opened *Confirmation window* by clicking on the RESEND icon.

After these, the User, whose email address you entered in the invitation, will receive one more email with the Accept invitation link.

### Delete Invitation 
To delete an invitation, do the next:
- click on the **Actions** icon and select the DELETE INVITATION option in the list of available;
- confirm your actions on the next opened *Confirmation window* by clicking on the DELETE icon.

After these, the *Accept invitation link* in the email, that was sent to the User whose email address you entered in the invitation, will be blocked.

## Transfer Organization
{{% notice info %}}
Transfer an organization means changing the Owner of it. 
{{% /notice %}}

{{% notice note %}}
Transferring Organization is available only if your User Role in this Organization is *Owner*. 
{{% /notice %}}

To Transfer Organization, do the following:  
- identify the Administrator, to whom you want to Transfer the Organization, on the *Administrators page*;    
- click on the **Actions** icon and select the **Transfer the Organization** in the list of available options:
![](../../assets/images/projects/6.png?classes=border,shadow)    
- confirm your actions on the next opened *Confirmation window* and click on the SEND icon. 

After confirming this action, the selected User will receive the message with the invitation to become an owner of the specifying Organization and if he accept it, his Role in the selected Organization will be changed from *Administrator* to *Owner*.    
 
## Remove Administrator
{{% notice note %}}
Removing Administrator is available only if your User Role in this Organization is *Owner* or *Administrator*.
{{% /notice %}}

To remove Administrator from the selected Organization, do the following:
- identify this unnecessary Administrator on the *Administrators page*;   
- click on the **Actions** icon and select the **Remove** in the list of available options;    
- confirm the User deletion on the next opened *Confirmation window*. 
     
After confirming this action, the selected User will be removed from the selected Organization.


