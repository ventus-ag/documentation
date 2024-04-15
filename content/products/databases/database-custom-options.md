--- 
title: Database's Custom Options
weight: 15
---
___
On this page, you can find an explanation of what is database's Custom Options, how to manage them in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Introduction](#introduction) 
  - [Edit Database's Custom Options](#edit-databases-custom-options)
    - [PostgreSQL](#postgresql)
    - [MySQL](#mysql)
    - [MariaDB](#mariadb)

## Introduction
**Database's Custom Options** are a feature provided to modify options of your database. You can edit various settings such as max connections, WAL sender timeout, streaming delay, etc. depending on the database type.

## Edit Database's Custom Options 

To edit the Custom Options of the selected Database:

1. Open the selected *Database details page* by clicking on the **Name** of the corresponding Database on the *Databases page*: 
![](../../../assets/images/databases/6.png?classes=border,shadow)

2. On the *Database details page*, select the *CUSTOM OPTIONS TAB*:
![](../../../assets/images/databases/30.png?width=20pc&classes=border,shadow) 

3. On the *CUSTOM OPTIONS TAB*, select the *Edit* icon:
![](../../../assets/images/databases/31.png?width=35pc&classes=border,shadow)

4. On the *Edit Custom Option* window, you can edit your selected Custom Option:
![](../../../assets/images/databases/32.png?width=35pc&classes=border,shadow)

After these steps, the Custom Options of the selected Database will be updated.

### PostgreSQL

For PostgreSQL databases, you can configure options such as:
- max_wal_senders: Maximum number of concurrent connections from standby servers or streaming base backup clients (Default: 16)
- wal_sender_timeout: Timeout for replication connections (Default: 60000 ms) 
- max_standby_streaming_delay: Max delay before canceling queries when a hot standby server is processing streamed WAL data (Default: 30000 ms)
- track_activity_query_size: Sets the size reserved for pg_stat_activity.query, in bytes. (Default: 1024)

Refer to the PostgreSQL documentation for details on these and other available options.

### MySQL

For MySQL databases, configurable custom options include:
- innodb-lock-wait-timeout: The timeout in seconds an InnoDB transaction may wait for a row lock before giving up (Default: 50)
- innodb-buffer-pool-size: The size in bytes of the buffer pool, the memory area where InnoDB caches table and index data (Default: 134217728)
- max-connections: The maximum permitted number of simultaneous client connections (Default: 151)
- max-allowed-packet: The maximum size of one packet or any generated/intermediate string (Default: 67108864)

See the MySQL documentation for details on these and other available options.

### MariaDB

MariaDB allows tuning similar options as MySQL, such as:
- innodb-lock-wait-timeout: The timeout in seconds an InnoDB transaction may wait for a row lock before giving up (Default: 50)  
- innodb-buffer-pool-size: The size in bytes of the buffer pool, the memory area where InnoDB caches table and index data (Default: 134217728)
- max-connections: The maximum number of simultaneous client connections allowed (Default: 151)
- max-allowed-packet: The maximum size of one packet or any generated/intermediate string (Default: 67108864)

See the MariaDB documentation for details on these and other available options.


By customizing these database options, you can optimize your database's performance and resource utilization based on your specific requirements and workload characteristics.