# Lesson
# Lab 8: Data Manage and Migrations

## **Table of Contents**

- [Lesson](#lesson)
- [Lab 8: Data Manage and Migrations](#lab-8-data-manage-and-migrations)
  - [**Table of Contents**](#table-of-contents)
    - [**Requirements**](#requirements)
    - [**Objectives**](#objectives)
  - [**Exercise 1: Implement Code First conventions**](#implement-code-first-conventions)
    - [**Defining Relationships in Classes**](#relationships-in-classes)
    - [**Codebook tables**](#codebook-tables)
  - [**Exercise 2: Creating Migrations**](#creating-migrations)

### **Requirements**

- [SQL Server 2022 or newer](https://info.microsoft.com/ww-landing-sql-server-2022.html?culture=en-us&country=us)

In downloaded exec file choose Custom installation and install LocalDb instance (named: (localdb)\MSSQLLocalDB)

### **Objectives**

In this LAB you will learn create database via .NET DbContext using migrations, Code First approach with conventions and manage data fom database.

## **Exercise 1: Implement Code First conventions**

In this course, we use the Code-First approach when working with databases. This means that we first create entity classes (models) in .NET, and the database is generated automatically from those classes.

Each entity class represents a database table, and class properties represent table columns. Entity Framework Core uses conventions to determine table names, primary keys, relationships (foreign keys), and data types. These conventions reduce the need for manual configuration. But, in some cases we need manual configuration, so because of it we have configuration file for each domain class.

Official Microsoft documentation (in left side bar look out Built-in conventions, Custom conventions and Model conventions):
- [Find more about conventions here](https://learn.microsoft.com/en-us/ef/ef6/modeling/code-first/conventions/built-in)

### **Defining Relationships in Classes**

One-to-Many Relationship

A navigation property allows you to navigate from one entity to related entities.
A reverse navigation property allows navigation in the opposite direction.

Example:
```csharp
public class Student
{
    public int Id { get; set; }
    public string Name { get; set; }

    public ICollection<Course> Courses { get; set; }
}

public class Course
{
    public int Id { get; set; }
    public string Title { get; set; }

    public int StudentId { get; set; }
    public Student Student { get; set; }
}
```

Many-to-Many (N-N) Relationship

For many-to-many relationships, it is recommended to manually create a third entity (junction table) instead of letting EF Core create it automatically.

This gives you more control and allows you to add extra fields if needed.

Example:
```csharp
public class Student
{
    public int Id { get; set; }
    public string Name { get; set; }

    public ICollection<StudentCourse> StudentCourses { get; set; }
}

public class Course
{
    public int Id { get; set; }
    public string Title { get; set; }

    public ICollection<StudentCourse> StudentCourses { get; set; }
}

public class StudentCourse
{
    public int StudentId { get; set; }
    public Student Student { get; set; }

    public int CourseId { get; set; }
    public Course Course { get; set; }
}
```

Have on mind that all properties in domain classes must have nullability operator ("?") if it is not required (nullable); no matter if that property is value type or is reference type.

All domain classes must be implemented in DbContext!

After we built in conventions into classes + implement domain config files, implemented DbContext with all domain classes, created connection string and made changes in Program.cs file, we can start migrations.

### **Codebook tables**

Codebook tables (hrv. šifrarnici) are tables in database which change never or rarely. For those tables in most cases you dont need all CRUD operations. You probably will need get API (depends on your business logic), but other APIs are not necessary because all data in that tables are mostly changed via direct SQL operations in database. Some examples ofcodebook tables: program types, genres, classes, academic years etc.
In .NET there is possibilty to insert data in codebooks at moment of creating database via migrations. That data is defined in DB context.


## **Exercise 2: Creating Migrations**

Migrations are used to create and update the database schema based on your entity classes.

Preconditions:

- Entity classes must be created

- DbContext must be configured

- Connection string must be correct

- Entity Framework Core packages must be installed

We will use Package Manager Console to write commands. You can open it in Visual studio -> Tools -> NuGet Package Manager -> Package Manager Console

:::caution **IMPORTANT**

Set projects as shown on image below:

:::

![nuget](migrations-projects.PNG)

Commands:
```shell
Add-Migration InitialCreate
Update-Database
```
After running Add-Migration, a new folder called Migrations is created.
This folder contains auto-generated code that defines: Tables, Columns, Primary keys, Relationships and rules.

Running Update-Database applies these changes and creates the database on your SQL Server.

This process ensures that your database structure always matches your .NET code.

Next Lab:
**ASP.NET** framework provides developer with build in DI container in which developer can define custom services with one of three lifetime scopes:

- **Singleton:** lifetime of service is through lifetime of application
- **Scoped:** lifetime of service is scope of one request, so for each request new service will be created
- **Transient:** each time service is requested, new instance is created