---
title: Database's Replicas
weight: 15
---
___
On this page, you can find an explanation of what is database's Replica, how to create and manage them in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Make Database's Replica](#make-databases-replica)
  - [Delete Database's Replica](#delete-databases-replica)

## Introduction
**Database's Replicas** are a feature provided to ensure the security of your databases. In the Cloud Console, you can create up to 5 replicas of your database in different projects, across one or multiple regions.

To find information about all created replicas of corresponding database, and to manage them - open the *REPLICAS TAB* on the *Database details page*, for this do the following:
- open the selected *Database details page* - for this click on the **Name** of the corresponding Database on the *Databases page*:    
![](../../../assets/images/databases/6.png?classes=border,shadow)
- select the *REPLICAS TAB*:  
![](../../../assets/images/databases/9.png?width=15pc&classes=border,shadow) 

## Make Database's Replica
To make the Replica of the selected Database do the following:  
- open the selected *Database details page* (click on the **Name** of the corresponding Database);  
- select the *REPLICAS TAB* and click the *CREATE REPLICA* icon:   
![](../../../assets/images/databases/14.png?width=40pc&classes=border,shadow) 

- select the project where you want to create the replica on the next opened *Create Replica window* and click on the CREATE icon:  
![](../../../assets/images/databases/15.png?width=30pc&classes=border,shadow) 

After these steps, the newly created Replica of the current database will be added to the *REPLICAS TAB* with a PROVISIONING status (will changed to ACTIVE shortly) and in the Database **details area** you'll find updated information: the database mode will have switched from *standalone* to *primary* (indicating that this database is now the primary one within the current project), and amount of created Replicas:
![](../../../assets/images/databases/16.png?width=40pc&classes=border,shadow)

When you navigate to the *Databases page* of the project you designated for the replica, you'll find the identical database, however, it will be in *replica* mode:
![](../../../assets/images/databases/17.png?classes=border,shadow)

## Delete Database's Replica
To delete the Replica of the selected Database do the following:  
- open the selected *Database details page* - for this click on the **Name** of the corresponding Database;
- identify this unnecessary Database Replica on the *REPLICAS TAB*;
- confirm the Database Replica deletion on the next opened *Confirmation window*.   
![](../../../assets/images/databases/10.png?width=40pc&classes=border,shadow) 

After these steps, the selected Database Replica will be deleted and disappeared from the *REPLICAS TAB* in the selected *Database details page* and from the *Databases page* of the project you designated for the replica.

Also, you can delete the Database Replica from the *Databases page* of the project you designated for the replica, for this do the following:
- identify this unnecessary Database in *replica* mode on the *Databases page* of the appropriate project;
- click on the **Actions** icon and select the **Delete** in the list of available options;
- confirm the Database deletion on the next opened *Confirmation window* and the selected Database Replica will be deleted shortly.

![](../../../assets/images/databases/18.png?classes=border,shadow)
