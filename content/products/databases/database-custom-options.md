---
title: Database's Custom Options
weight: 15
---
___
On this page, you can find what database's Custom Options are and how to manage them in the Cloud Console.

# Table of contents
- [Table of contents](#table-of-contents)
- [Introduction](#introduction) 
- [Edit Database's Custom Options](#edit-databases-custom-options)
  - [PostgreSQL and TimescaleDB](#postgresql-and-timescaledb)
  - [MySQL](#mysql)
  - [MariaDB](#mariadb)
  - [Redis](#redis)
  - [MongoDB](#mongodb)

## Introduction
**Database's Custom Options** are a feature provided to modify options of your database. You can edit settings such as connection limits, timeouts, logging and SQL behaviour, depending on the database type. Memory, storage, replication and high-availability settings are sized and managed by the platform for your plan and are not listed.

The *CUSTOM OPTIONS TAB* is available for PostgreSQL, TimescaleDB, MySQL, MariaDB, Redis and MongoDB Databases.

The options and their values are checked before they are applied: only options from the offered list can be set, each with its own allowed range. The list depends on the service and on the version of the Database: options your database version does not support are not shown. A change that cannot be applied safely, for example lowering *max_connections* on a high-availability PostgreSQL Database, is refused when you save it. Every change is applied to all members of a high-availability Database.

## Edit Database's Custom Options 
![](../../../assets/images/databases/custom-options.png?classes=border,shadow)

The *CUSTOM OPTIONS TAB* of the *Database details page* lists the options with these columns:

| Column | Description |
|--------|-------------|
| Name | the title and the name of the option |
| Unit, Min value, Max value | the unit and the allowed range |
| Default value | the value used when the option is not changed |
| Custom value | the value you have set (empty if the option was never changed) |
| Effective value | the value the database uses now |
| State | `default` - not changed; `applied` - your value is in use; `pending` - saved and waiting to be applied, for example until the database restarts; `rejected` - the engine did not accept the value, or it could not be applied within 15 minutes and the previous value was restored (edit or unset the option to try again). Point at the custom value to see the reason of a `pending` or `rejected` state |

Use the row **Actions** menu:
- **Edit** - change the value and save. The field depends on the type of the option: a number (with the allowed range), a size (bytes or a value with a unit, for example `512MB`), a drop-down list for on/off and fixed sets of values, or a text for lists and flags (for example the comma-separated SQL modes). The text under the field shows the allowed range, the default, the other accepted values and, for options that need it, **Changing this value restarts the database.** A value must not contain spaces, quotes or control characters; an empty value is accepted only by options that allow it. If the option has no custom value yet, the field is pre-filled with the default, and saving it unchanged sets no override.
- **Unset override** - returns the option to its default value.

*Edit* and *Unset override* are not available for read-only options and for Replicas, which follow their primary Database.

### PostgreSQL and TimescaleDB

For PostgreSQL and TimescaleDB databases, you can configure:
- statement_timeout, lock_timeout, idle_in_transaction_session_timeout: abort long statements, lock waits and idle open transactions, in ms (Default: 0, disabled)
- idle_session_timeout (version 14 and later): ends idle connections, in ms (Default: 0, disabled)
- transaction_timeout (version 17 and later): ends transactions that run longer than the time, in ms (Default: 0, disabled)
- log_min_duration_statement, log_statement, log_temp_files, log_lock_waits, log_autovacuum_min_duration, log_connections: what the database logs
- autovacuum_vacuum_scale_factor, autovacuum_analyze_scale_factor, autovacuum_vacuum_insert_scale_factor: when tables are vacuumed and analyzed
- max_connections: maximum number of concurrent connections (Default: 100, requires a restart)
- max_locks_per_transaction: lock slots per transaction, raise it for many partitions or hypertable chunks (Default: 64, TimescaleDB 128, requires a restart)
- track_activity_query_size, track_io_timing: query text length and I/O timing in the statistics views
- jit: just-in-time compilation of queries (Default: on, TimescaleDB off)
- timezone: the time zone of the database sessions

Memory settings such as work_mem can still be set for your own roles and databases with `ALTER ROLE ... SET` or `ALTER DATABASE ... SET`.

### MySQL

For MySQL databases, you can configure:
- max-connections: maximum number of simultaneous client connections (Default: 151)
- max-allowed-packet: maximum size of one packet or row (Default: 64MB, 5.7: 4MB)
- wait-timeout, interactive-timeout: idle connection timeouts, in seconds (Default: 28800)
- innodb-lock-wait-timeout: how long a transaction waits for a row lock, in seconds (Default: 50)
- tmp-table-size, max-heap-table-size, sort-buffer-size, group-concat-max-len: per-query limits
- sql-mode, transaction-isolation, default-time-zone: SQL behaviour of the server
- sql-require-primary-key (8.0.13 and later): refuses tables without a primary key
- log-bin-trust-function-creators, event-scheduler, activate-all-roles-on-login, information-schema-stats-expiry

### MariaDB

For MariaDB databases, you can configure:
- max-connections, max-allowed-packet, wait-timeout, interactive-timeout, innodb-lock-wait-timeout: as for MySQL (max-allowed-packet Default: 16MB)
- max-statement-time: aborts statements that run longer than the time, in seconds (Default: 0, disabled). Set it back to 0 before a major version upgrade; the upgrade is refused while it is set
- idle-transaction-timeout: closes connections idle inside an open transaction, in seconds (Default: 0, disabled)
- tmp-table-size, max-heap-table-size, group-concat-max-len: per-query limits
- sql-mode, transaction-isolation, default-time-zone: SQL behaviour of the server
- innodb-snapshot-isolation (10.6.18 and later): conflict detection under REPEATABLE READ (Default: off, 11.8 and later: on)
- log-bin-trust-function-creators, event-scheduler

### Redis

For Redis databases, you can configure:
- maxmemory-policy: what Redis does when the memory limit is reached (Default: noeviction, which refuses writes; an eviction policy removes keys instead). The platform sets the memory limit from your plan's memory, leaving room for snapshots.
- notify-keyspace-events: keyspace notifications (Default: empty, disabled)
- timeout: closes the connection of a client that is idle for the given number of seconds (Default: 0, disabled)
- appendfsync: how often the append-only file is synced to the disk (Default: everysec)
- lazyfree-lazy-user-del: DEL frees memory in the background like UNLINK (Default: no)
- lfu-log-factor, lfu-decay-time: tuning of the LFU eviction policies

### MongoDB

For MongoDB databases, you can configure:
- operationProfiling.mode, operationProfiling.slowOpThresholdMs: the database profiler and the slow operation threshold in ms (Default: off, 100)
- setParameter.cursorTimeoutMillis: idle cursors are closed after the time, in ms (Default: 600000)
- setParameter.transactionLifetimeLimitSeconds: aborts multi-document transactions older than the time, in seconds (Default: 60)
- security.javascriptEnabled: server-side JavaScript execution (Default: on, requires a restart)

By customizing these database options, you can optimize your database's performance and resource utilization based on your specific requirements and workload characteristics.
