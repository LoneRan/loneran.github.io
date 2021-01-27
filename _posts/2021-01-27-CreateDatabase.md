---
layout: post
date: 2021-01-27 06:30
title:  "Create and manage a database with multiple schema on SQL server"
description: This is a guideline showing how to create a database with multiple schemas using either SQL Server Management Studio (SSMS) or SQL queries.
comments: true
category: 
- docs
- blog
tags:
- documentation
- SQL
---

** Creating a demo database

Follow the following step to create a database on-premises:

1. Download SQL server on your local machine. [https://www.microsoft.com/en-us/sql-server/sql-server-downloads](https://www.microsoft.com/en-us/sql-server/sql-server-downloads)
2. After installation, connect to it using SQL Server Management Studo. To download SQL Server Management Studio, kindly go to this link: [https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15](https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms?view=sql-server-ver15)
3. Now you have connection to database, the default schema is &quot;dbo&quot;, if you don&#39;t specify any schema, you will automatically create for example a table under &quot;dbo&quot; schema.

The goal is we plan to create a schema for each client and only that client can access it&#39;s own schema, not any clients else. Under each schema, there should be exactly the same tables as what we have currently on cloud.

- Create authentication users:

In the Database User - New dialog box, on the General page, select one of the following user types from the User type list:

- SQL user with login
- SQL user with password
- SQL user without login
- User mapped to a certificate
- User mapped to an asymmetric key
- Windows user

For example to create a user with login and password:

_-- Creates the login AbolrousHazem with password &#39;340$Uuxwp7Mcxo7Khy&#39;._

_CREATE LOGIN AbolrousHazem_

_WITH PASSWORD = &#39;340$Uuxwp7Mcxo7Khy&#39;;_

_GO_

_-- Creates a database user for the login created above._

_CREATE USER AbolrousHazem FOR LOGIN AbolrousHazem;_

_GO_

Reference Link: [https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/create-a-database-user?view=sql-server-ver15](https://docs.microsoft.com/en-us/sql/relational-databases/security/authentication-access/create-a-database-user?view=sql-server-ver15)

[https://docs.microsoft.com/en-us/sql/t-sql/statements/create-user-transact-sql?view=sql-server-ver15](https://docs.microsoft.com/en-us/sql/t-sql/statements/create-user-transact-sql?view=sql-server-ver15)

- Create schema under certain users and grant access:

_CREATE SCHEMA Sprockets AUTHORIZATION Annik_

_CREATE TABLE NineProngs (source int, cost int, partnumber int)_

_GRANT SELECT ON SCHEMA::Sprockets TO Mandar_

_DENY SELECT ON SCHEMA::Sprockets TO Prasanna;_

_GO_

- Create tables under certain schema:

_CREATE TABLE client2.peronalInfo (_

_Name NCHAR (10) ,_

_Age NUMERIC (18,0) ,_

_Gender NCHAR(10),_

_);_

_Go_

_CREATE TABLE client2.temprature (_

_temprature VARCHAR (50),_

_personalid INT,_

_);_

_CREATE TABLE client2.infos (_

_first\_name VARCHAR (50) NOT NULL,_

_last\_name VARCHAR (50) NOT NULL,_

_phone VARCHAR(20),_

_);_
