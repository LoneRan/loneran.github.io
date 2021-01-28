---
layout: post
date: 2021-01-26 12:48
title:  "Single database with multiple schemas VS. Multiple databases with single schema"
description: ...
comments: true
category: 
- docs
- blog
tags:
- documentation
- SQL
---


**Single Database with multiple schemas**

There are couple of questions that might help us decide: ([https://www.oreilly.com/library/view/oracle-distributed-systems/1565924320/ch01s04.html#ch01-34725](https://www.oreilly.com/library/view/oracle-distributed-systems/1565924320/ch01s04.html#ch01-34725))

- Are most users in the same location or using the same access path?
- Do the applications have the same administrative support staff?
- Do the applications have compatible availability requirements?
- Do the applications have compatible database and OS version requirements and upgrade paths?
- Are the applications reasonably similar in functionality and load characteristics?
- Do the applications have the same usage level (e.g., QA, development, production, maintenance, etc.)?
- If the data is related and you want to enforce referential integrity and implement Foreign Keys
- If you could ever want a foreign key constraint between the two entities

We better consider placing different schemas in the same database if we answer &quot;Yes&quot; to all questions (or most of them).

<!--more-->

Pros:

1. Lower storage and memory overhead, every database carries a certain amount of overhead.
2. If we only have one database, and each schema is shared with each other, easily querytables across namespaces to make further data analysis. (_It is possible to query tables across different databases, but this requires setting up foreign data wrappers, which brings about additional maintenance and possible performance implications._)
3. In our case, our clients use the same template,
4. Easier disaster recovery, this allows us to backup the database and restore it

Cons:

1. Less security isolation. (_Way to resolve this: grant access at schema level_)
2. There is no distinct log files and backup for each client
3. Less scalability as it might not be easy to inspect the needs for each client
4. If the SQL server goes down (for maintenance reasons or disaster), our application is also shut down and all users cannot access their data. (_Way to resolve this: also_ _possible to take individual filegroups online/offline_)
5. It will be a big database and backup will take more time, and it might be difficult to take partial backup with schema approach (_Way to resolve this: filegroup backup_)
6. The file group per schema can be done, but it&#39;s all manual.

**Multiple Databases with single schema**

Pros:

1. High security isolation, each client have no access to other&#39;s databases when we lock down with one client per database
2. Easy to customize for each client
3. Easy for client to retrieve all of their data back to a point in time without interfere with others
4. Easy to manage backups/restores for each user
5. 3 different DBs can be placed on 3 different disks. Better IO.
6. Sql server has one transaction log per database with a limit of 32 outstanding/pending IOs. In high performance write situations multiple databases might be better.

Cons:

1. More overhead to maintain multiple databases.
2. Query across database can be done, but it&#39;s trivial and not easy to handle
3. Backup/restore requires more work to handle

**Reference:**

Great discussion to refer about this topic:

URL:[https://www.sqlservercentral.com/forums/topic/multiple-databases-or-multiple-schemas](https://www.sqlservercentral.com/forums/topic/multiple-databases-or-multiple-schemas)

Good point about schema per client: &quot;In addition to a schema per customer I would recommend that you also create a filegroup per customer, then place all the database objects for each customer into that filegroup.&quot;

URL: https://serverfault.com/a/303189
