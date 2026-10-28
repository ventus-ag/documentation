---
title: Database Management
weight: 25
---
___
On this page, you can find how to create and delete databases within your main database instance in the Cloud Console, and how to manage extensions of PostgreSQL and TimescaleDB databases.

# Table of contents
- [Table of contents](#table-of-contents)
  - [Databases tab](#databases-tab)
  - [Extensions and Settings](#extensions-and-settings)

## Databases tab
The *DATABASES TAB* of the *Database details page* lists the databases inside your instance (it is not shown for Redis, which has no named databases). Columns: *Name*; *Charset* and *Collation* (PostgreSQL, TimescaleDB, MySQL and MariaDB only); *Extensions* and *Settings* (PostgreSQL and TimescaleDB only); *Notes* - shown only when something was not applied, with the reason.

![](../../../assets/images/databases/databases-tab.png?classes=border,shadow)

**Create.** Click **CREATE DATABASE** and fill in:
- *Database Name* - starts with a Latin letter or underscore; Latin letters, digits, hyphens and underscores, up to 63 characters. Names reserved by the engine (for example `postgres`, `template0`, `mysql`, `information_schema`, `admin`) are refused.
- *Charset* and *Collation* - not asked for MongoDB. If the engine refuses the selected pair, the database is created with the server default and the notice *Charset and collation not applied (server default used)* is shown.
- *Extensions* (PostgreSQL and TimescaleDB) and their settings, see below.

**Delete.** Use *Delete* in the row **Actions** menu and type the name of the database to confirm.

{{% notice warning %}}
Deleting a database permanently removes all its contents. This action cannot be undone.
{{% /notice %}}

{{% notice note %}}
The list is read-only for a Replica (its databases follow the primary database) and for Databases whose databases and users are managed inside the engine, see [User Management](../database-user-management#users-managed-inside-the-database).
{{% /notice %}}

## Extensions and Settings
PostgreSQL and TimescaleDB databases can use extensions. The platform installs them, you only select the ones you need; extensions that cannot run on the version of your instance are not offered.

| Extension | Description | PostgreSQL | TimescaleDB |
|-----------|-------------|:----------:|:-----------:|
| vector | pgvector: vector types and nearest-neighbour search (HNSW, IVFFlat) for embeddings. PostgreSQL 13-18; enabling it restarts the database | yes | - |
| pgcrypto | cryptographic functions: hashing, password hashing, PGP encryption | yes | yes |
| uuid-ossp | UUID generation functions | yes | yes |
| pg_trgm | trigram similarity and fast LIKE/ILIKE search | yes | yes |
| hstore | key/value pairs in a single column | yes | yes |
| ltree | hierarchical tree-like labels | yes | yes |
| citext | case-insensitive text type | yes | yes |
| btree_gin, btree_gist | operator classes for scalar types | yes | yes |
| intarray | functions and indexes for arrays of integers | yes | yes |
| tablefunc | table functions including crosstab() | yes | yes |
| pg_stat_statements | statistics of every SQL statement; enabling it restarts the database | yes | yes |

TimescaleDB itself is created automatically in every database of a TimescaleDB instance.

**Choosing extensions.** Select extensions when you create the instance (they go to the initial database), when you create a database, or later with *Extensions* in the row **Actions** menu.
- Enabling an extension that needs a restart (*vector*, *pg_stat_statements*) restarts the database once; the form warns you. Until the database has restarted and the server reports the extension as installed, it is shown as *(pending)* in the table.
- An extension that could not be installed is shown as *(not applied)*, the reason is in the *Notes* column.
- Removing an extension from the list **never uninstalls it**, since that would delete the data that uses it: the platform only stops managing it and resets its settings. The notification after saving says so; nothing else is shown on the page.
- Before upgrading the version, check that the extensions in use exist on the new version; the edit form warns you about the ones that do not.

**Extension settings.** *vector*, *pg_trgm* and *pg_stat_statements* have per-database settings. Open *Settings* in the row **Actions** menu, change the values and save. They are applied without a restart. Every field shows its allowed range and default; an empty value means the extension default. A setting the engine refuses is shown as *(not applied)* with the reason in *Notes* and in the notice *Settings not applied*.
