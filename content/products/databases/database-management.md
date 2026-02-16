---
title: Database Management
weight: 25
---
___
On this page, you can find an explanation of how to create and delete databases within your main database instance in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Create Database](#create-database)
  - [Delete Database](#delete-database)

## Create Database
To create a new database within your main database instance:
- Navigate to the Database Management page
![](../../../assets/images/databases/dbs.png?classes=border,shadow)

- Click the CREATE button
- In the opened window, fill in the following parameters:
![](../../../assets/images/databases/createdb.png?classes=border,shadow)

  - Name: Enter a name for your new database
  - Charset: Select the character set for the database
  - Collation: Choose the collation for the database
- Click CREATE to confirm

## Delete Database
To delete a database:
- Locate the database you wish to delete in the table of databases
![](../../../assets/images/databases/dbs.png?classes=border,shadow)

- Click on the DELETE option next to the database name
![](../../../assets/images/databases/deletedb.png?classes=border,shadow)

- Confirm the deletion in the popup window

{{% notice warning %}}
Deleting a database will permanently remove all its contents. This action cannot be undone.
{{% /notice %}}