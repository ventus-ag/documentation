---
title: User Management
weight: 30
---
___
On this page, you can find instructions on how to manage database users, including creating and deleting users, assigning permissions, and resetting passwords.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Create User](#create-user)
  - [Delete User](#delete-user)
  - [Reset User Password](#reset-user-password)
  - [Set User Permissions](#set-user-permissions)

## Create User
To create a new database user:
- Click the CREATE USER button
- In the opened window, enter the following information:
![](../../../assets/images/databases/createuser.png?classes=border,shadow)

  - Username: Enter a name for the new user
  - Database: Select the database(s) the user should have access to
  - Permissions: Choose either Read or ReadWrite permissions
- Click CREATE to confirm

![](../../../assets/images/databases/savepassword.png?classes=border,shadow)
- Note the displayed password for the new user

## Delete User
To delete a user:
- Locate the user in the table of users
![](../../../assets/images/databases/users.png?classes=border,shadow)

- Click on the DELETE option next to the user's name
- Confirm the deletion in the popup window

## Reset User Password
To reset a user's password:
- Find the user in the table of users
![](../../../assets/images/databases/users.png?classes=border,shadow)

- Click on the RESET PASSWORD option
![](../../../assets/images/databases/resetpassword.png?classes=border,shadow)

- Confirm the action in the popup window
- Note the new password displayed
![](../../../assets/images/databases/savepassword.png?classes=border,shadow)


## Set User Permissions
To modify a user's permissions:
- Locate the user in the table of users
![](../../../assets/images/databases/users.png?classes=border,shadow)

- Click on the SET PERMISSIONS option
![](../../../assets/images/databases/setperms.png?classes=border,shadow)

- In the opened window:
  - Select or deselect databases to change permissions
  - Choose between Read and ReadWrite permissions for each database
  - To remove permissions for a database, deselect it
- Click SAVE to confirm the changes

{{% notice note %}}
Changes to user permissions take effect immediately.
{{% /notice %}}