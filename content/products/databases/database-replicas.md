---
title: Database's Replicas
weight: 15
---
___
On this page, you can find what database's Replicas are and how to create and manage them in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Introduction](#introduction)
  - [Create and delete Replica](#create-and-delete-replica)

## Introduction
**Database's Replicas** ensure the security of your data: a Replica is a separate Database in another Project that follows the primary Database. You can create up to 5 Replicas of a Database in different Projects of the same region as the primary Database.

Replicas are available for PostgreSQL, TimescaleDB, MySQL, MariaDB and Redis. The *REPLICAS TAB* is not shown for MongoDB.

{{% notice note %}}
Replicas are not the same as [High Availability](../databases#high-availability). High Availability keeps one standby copy next to the Database in the same Project and takes over automatically when the server fails.
{{% /notice %}}

A Replica follows its primary Database: its databases, extensions, settings and custom options come from the primary and cannot be changed on the Replica, and the password of its main user cannot be reset there.

## Create and delete Replica
The *REPLICAS TAB* of the *Database details page* lists the Replicas (*Name*, *Status*, *Mode*, *Version*, *Created*); click the name of a Replica to open it in its own Project.

![](../../../assets/images/databases/replicas-tab.png?classes=border,shadow)

- **Create.** Click **CREATE REPLICA**, select the Project (only Projects of the same region are offered, the current one is marked *(Current project)*) and click **CREATE**. The button is active only while the primary Database is running (`ACTIVE` or `DEGRADED`), is not itself a Replica and has fewer than 5 Replicas. The Replica appears with the `PROVISIONING` status (then `ACTIVE`), the primary Database changes its *Mode* from *Standalone* to *Primary*, and in the selected Project the new Database is listed in the *Replica* mode.
- **Delete.** Use *Delete* in the row **Actions** menu on the *REPLICAS TAB*, or in the **Actions** menu of the Replica on the *Databases page* of its Project, and confirm.
