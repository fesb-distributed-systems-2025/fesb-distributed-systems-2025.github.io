# Lesson
# Lab 8: Web Sockets

## **Table of Contents**

- [Lesson](#lesson)
- [Lab 8: Web Sockets](#lab-8-web-sockets)
  - [**Table of Contents**](#table-of-contents)
    - [**Requirements**](#requirements)
    - [**Objectives**](#objectives)
  - [**Exercise 1: Installing Nuget packets**](#installing-nuget-packets)
  - [**Exercise 2: Implement Db Context and make Connection string**](#dbcontext-and-connection-string)

### **Requirements**

- [SQL Server 2022 or newer](https://info.microsoft.com/ww-landing-sql-server-2022.html?culture=en-us&country=us)

In downloaded exec file choose Custom installation and install LocalDb instance (named: (localdb)\MSSQLLocalDB)

### **Objectives**

In this LAB you will learn connect .NET application to database and manage data.

## **Exercise 1: Installing Nuget packets**

First need to install some .NET (Nuget) packages to manage DB and data.

Right click on project -> choose Manage Nuget Packages

![nuget](nuget.PNG)

On Nugett screen choose Browse and search for you package -> hen click on package and choose latest version of .NET 8 serie -> Install and accept all conditions

![nuget-install](nuget-install.PNG)

List of packages per project:

Api:
     - EntityFrameworkCore.Tools
     - AspNetCore.Swagger
     - AspNetCore.SwaggerGen
     - AspNetCore.SwaggerUI

Application:
             - EntityFrameworkCore
             - EntityFrameworkCore.SqlServer
             - EntityFrameworkCore.Tools

Domain: 
        - EntityFrameworkCore.Design

Infrastructure: 
                - EntityFrameworkCore

## **Exercise 2: Implement Db Context and make Connection string**

Db Context is main class to map .NET domain classes to tables in database. Using DbSet class we define which domain class will be mapped into db table.

Connection string is usually defined in appsettings.json file. It is string that define connection to database that we will use for our application. Usually connection string contains SQL server instance name, database name, authentication login data and connection config data.

E.g.
```shell
Server=localhost;Database=MyDB;User Id=myuser;Password=mypassword;Trusted_Connection=True;
```
