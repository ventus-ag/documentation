---
title: Databases
weight: 10
---
___
On this page, you can find how to create, edit, upgrade and delete Databases in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Databases page](#databases-page)
  - [Create Database](#create-database)
  - [High Availability](#high-availability)
  - [Database details page](#database-details-page)
  - [Edit Database](#edit-database)
  - [Upgrade Database version](#upgrade-database-version)
  - [Reset Database Password](#reset-database-password)
  - [Start, Stop and Delete](#start-stop-and-delete)

{{% notice note %}}
The Database-as-a-Service feature in the Cloud Console is currently in beta. It has not been fully tested across all use cases. Customer support is available for any questions or issues you may encounter.
{{% /notice %}}

## Databases page
Select **Databases** in the VIRTUAL DATACENTER block of the *side-bar menu*. The page lists all Databases of the Project with a search bar, sorting and the **CREATE DATABASE** button. Click the name of a Database to open its [details page](#database-details-page).

![](../../../assets/images/databases/databases-list.png?classes=border,shadow)

| Column | Description |
|--------|-------------|
| Status | `ACTIVE` - ready to use; `PROVISIONING` - being created; `UPGRADING` - moving to another version; `DEGRADED` - running, but not fully healthy (for example, the High Availability standby is not ready); `STOPPED` - stopped; `FAILED` - could not reach the requested state, contact customer support; `DELETING` - being removed |
| Mode | *Standalone*; *Primary* - the Database has [Replicas](../database-replicas) in other Projects; *Replica* |
| Connection string | address and port to connect to the Database |

The **Actions** menu of a row has *Start* (only for `STOPPED` Databases), *Edit* and *Delete*.

## Create Database
Click **CREATE DATABASE**, fill in the form and click **CREATE**.

![](../../../assets/images/databases/create-database.png?width=35pc&classes=border,shadow)

| Field | Description |
|-------|-------------|
| Service name | PostgreSQL, TimescaleDB, MySQL, MariaDB, MongoDB or Redis |
| Name | up to 16 characters: Latin letters, digits and hyphens; starts with a letter, does not end with a hyphen. It is also the name of the first database inside the instance, so names reserved by the engine (for example `postgres`, `mysql`, `admin`) are refused |
| Version | only supported versions are offered; the recommended one is marked *(default)* and is used if nothing is selected |
| Extensions | PostgreSQL and TimescaleDB only: extensions created in the initial database, see [Database Management](../database-management#extensions-and-settings) |
| DB user | optional name of the main user: starts with a Latin letter, letters, digits and hyphens, up to 16 characters; names of system accounts (`root`, `postgres`, `admin`, `default`, `replication`, ...) are reserved |
| Port | the default port of the service is pre-filled |
| vCPUs, Memory | resources of the Database |
| Disk | size in MiB, the range depends on the service; pre-filled with the minimum |
| IP ACL | IPv4 networks with a prefix length that may connect to the public endpoint, one per line, for example `192.168.1.101/32`. Later it is changed on the NETWORK TAB, see [Database's Network](../database-network) |
| Provision in private network | places the Database in a private *Network* and *Subnet*, optionally with a *Private static IP*; more endpoints can be added later on the NETWORK TAB |
| Enable High Availability | adds a standby that takes over automatically, see [High Availability](#high-availability) |

After you click **CREATE** the Database appears with the `PROVISIONING` status and a window shows its password **once** - save it. The Database is ready in a few minutes, when the status becomes `ACTIVE`.

| Service | Default port | Features |
|---------|--------------|----------|
| PostgreSQL | 5432 | databases with charset and collation, extensions, custom options, Replicas |
| TimescaleDB | 5432 | the same as PostgreSQL |
| MySQL, MariaDB | 3306 | databases with charset and collation, custom options, Replicas |
| MongoDB | 27017 | databases without charset and collation, no Replicas; High Availability runs 3 members |
| Redis | 6379 | no named databases (no DATABASES TAB), users get one access level for the whole instance, backups cover the whole data set |

## High Availability
**High Availability (HA)** keeps the Database available when its server fails. The platform runs the Database as a *primary* with one *standby* copy that receives all changes. If the primary stops responding, the standby is promoted automatically and the connection address stays the same; clients only need to reconnect. MongoDB runs a replica set of three members that elects its primary by itself.

Switch HA on or off with *Enable High Availability* in the create or edit form. Switching it off removes the standby.

- For PostgreSQL, TimescaleDB, MySQL and MariaDB a change is confirmed by the standby before it is acknowledged. If the standby is unavailable, the Database keeps working with asynchronous replication instead of blocking writes.
- vCPUs, Memory and Disk are *per member*, and every member is charged: the Resources block shows **Charged: x2 (HA)** (**x3** for MongoDB).
- HA protects against a server failure. It does not replace [Backups](../database_backups) and is not the same as [Replicas](../database-replicas), which are copies in other Projects.

The General block of the details page shows *High availability*: Yes/No and, when it is on:

| Field | Description |
|-------|-------------|
| Health | `Healthy` - all members work normally; `Suspect`, `Degraded` - a member has a problem, the Database may run without a standby; `FailingOver`, `SwitchingOver` - the standby is taking over, after a failure or as a planned operation; `SplitBrainRisk` - the members cannot agree on the primary, contact customer support |
| Failover delay | how long the platform waits for the primary before promoting the standby |
| Last failover | date and time of the last failover |

## Database details page
![](../../../assets/images/databases/database-details.png?classes=border,shadow)

**Notices.** Problems and progress are shown in one box at the top. One notice shows its title and text, as in the picture below; several are merged into one box *N notices*, most severe first (errors, warnings, information). Notices: *Upgrading X → Y* (red if the upgrade failed or is blocked); *Migration* pending approval, in progress, failed or blocked (an older Database is being moved to the current platform image; when it is pending approval, contact customer support to approve or schedule the one restart); *Restore failed* and *Restore failed and was rolled back*; *Last backup failed*; *Backup in progress*; *Load balancer not applied*; *Extensions not installed*, *Settings not applied*, *Charset and collation not applied (server default used)*, *Permissions not applied* and *Extensions installing after the database restarts*; and a notice that databases and users are read-only (see [User Management](../database-user-management#users-managed-inside-the-database)). The reason is written in every notice.

![](../../../assets/images/databases/database-notices.png?classes=border,shadow)

**Quick actions** (icons next to the title): *Start*, *Stop*, *Database management* (opens the web-based management tool DbGate in a new tab), *Reset password*, *Edit* and *Delete*.

**Details area:**

| Block | Shows |
|-------|-------|
| General | ID, creation date, *Status*, *Mode*, number of Replicas, *High availability* and its health, *Connection pooler* address and mode if the pooler is on |
| Resources | *Version* (and *Running*, the version actually running, while it differs, for example during an upgrade), *vCPU*, *Memory*, *Disk* with the used percentage, *Charged* multiplier with HA |
| Backup | *Backing up* and *Restoring* states, *Restore phase*, *Last backup* result (hover it for the message), *Last run*, scheduler *Timezone* and *Next run*, S3 link state |
| Connection information | *Host* (click to copy), *S3 Endpoint* and *S3 Key* when backup storage is connected; the secret is never shown, the key is displayed as **Configured** |

The **Usage** chart shows CPU and memory load for the last hour.

**Tabs.** The selected tab is kept in the page address, so a link to it can be shared.

| Tab | Purpose | Shown for |
|-----|---------|-----------|
| DATABASES | databases and extensions inside the instance, see [Database Management](../database-management) | all except Redis |
| USERS | users and permissions, see [User Management](../database-user-management) | all |
| REPLICAS | copies in other Projects, see [Database's Replicas](../database-replicas) | all except MongoDB |
| BACKUPS | storage, schedule, backups and restore, see [Database's Backups](../database_backups) | all |
| CUSTOM OPTIONS | engine options, see [Database's Custom Options](../database-custom-options) | PostgreSQL, TimescaleDB, MySQL, MariaDB, Redis, MongoDB |
| NETWORK | public and internal endpoints, see [Database's Network](../database-network) | all |

There is no separate scheduler tab: the backup schedule is on the BACKUPS TAB, and an old link with `?tab=scheduler` opens it.

## Edit Database
Open **Edit** from the **Actions** menu on the *Databases page* or with the *Edit* icon on the details page, change the fields and click **SAVE**. The Database is updated in a few minutes.

![](../../../assets/images/databases/edit-database.png?width=30pc&classes=border,shadow)

| Field | Notes |
|-------|-------|
| Version | the list offers the versions the Database can move to, see [Upgrade Database version](#upgrade-database-version) |
| Port | the port of the Database |
| vCPUs, Memory | resources of the Database (labelled *CPU* and *RAM* in the form on the details page) |
| Disk | details page only. The size can only be **increased**: the field cannot be set below the current size, because a volume cannot shrink. The Database stays online while the disk grows, in most cases without a restart |
| Enable High Availability | see [High Availability](#high-availability) |
| Connection pooler | details page only, for PostgreSQL and TimescaleDB Databases that already use the pooler (PgBouncer on port 6432, beside each endpoint; the addresses are on the NETWORK TAB). It can be switched off, or its *Pooling mode* changed: *Transaction* - clients keep their connection through a switchover or failover, session state (SET, advisory locks, LISTEN, temporary tables) does not outlive a transaction; *Session* - full session semantics, connections are dropped on a switchover. Switching it off or changing the mode disconnects all clients of the pooler, the form warns you before you save |

{{% notice note %}}
The *IP ACL* is not in the edit form any more: edit it on the NETWORK TAB with *Edit allowed CIDRs* (see [Database's Network](../database-network)). The databases, extensions, settings and custom options of a Replica follow its primary Database and cannot be edited on the Replica.
{{% /notice %}}

## Upgrade Database version
Change the version with the *Version* field of the edit form.
- The list contains the version that is running (marked *(current)*), a pending version (marked *(requested)*) and the newer versions that are available. Moving to an older version is not possible.
- A major version is upgraded one major version at a time (for example 14 → 15 → 16). A step that skips a major version is refused.
- If an extension in use is not available on the selected version, the form warns you: the upgrade may be blocked or leave the extension uninstalled.
- During the upgrade the status is `UPGRADING`, the notice *Upgrading X → Y* shows the phase, and *Version* shows the requested version while *Running* shows the version that is running now.
- If the upgrade fails or is blocked, the notice turns red and gives the reason. To cancel an unfinished upgrade, edit the Database, select the *(current)* version and save.

{{% notice warning %}}
Create a backup before an upgrade (see [Database's Backups](../database_backups)). A major version upgrade cannot be reverted by selecting an older version.
{{% /notice %}}

## Reset Database Password
Click the *Reset password* icon on the details page and confirm. The new password of the main Database user (the *DB user* from the create form) is shown **once** - save it. The icon is active for running Databases (`ACTIVE` or `DEGRADED`) in *Standalone* or *Primary* mode. It is not available for Replicas and for Databases whose users are managed inside the engine. Passwords of other users are reset on the USERS TAB.

## Start, Stop and Delete
- **Stop** (details page) stops a running Database: it does not accept connections, its data is kept. **Start** (details page, or the row **Actions** menu) starts a `STOPPED` Database.
- **Delete** (the row **Actions** menu, or the *Delete* icon on the details page) asks you to type the name of the Database to confirm.

{{% notice warning %}}
Deleting a Database permanently removes its data. This action cannot be undone.
{{% /notice %}}
