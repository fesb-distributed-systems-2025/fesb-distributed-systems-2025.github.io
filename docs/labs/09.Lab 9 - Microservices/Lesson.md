# Lesson
# Lab 9: Microservices

## **Table of Contents**

- [Lesson](#lesson)
- [Lab 9: Microservices](#lab-9-microservices)
  - [**Table of Contents**](#table-of-contents)
  - [**Dependency Injection**](#dependency-injection)
  - [**Microservices**](#microservices)
    - [**Entity Framework**](#entity-framework)
    - [**Entity Framework**](#entity-framework)

## **Dependency Injection**

Dependency Injection (DI) is a software design pattern used to make programs more flexible, maintainable, and easier to test. In modern software development, especially in large applications, classes often depend on other classes to perform their work. These dependent objects are called dependencies.

Instead of creating these dependencies inside the class, Dependency Injection provides them from the outside. This simple idea improves code quality and follows good programming principles.

A dependency is any object that a class needs to function.

Example:
```csharp
class StudentService
{
    private Database db;

    public StudentService()
    {
        db = new Database();
    }
}
```
StudentService depends on Database. Database is a dependency.
The problem is that StudentService creates its own Database.
This creates tight coupling.

:::caution **IMPORTANT**

Dependency Injection means: Dependencies are provided to a class instead of being created inside the class.

:::

So instead of this:
```csharp
db = new Database();
```
We do this:
```csharp
public StudentService(Database db)
{
    this.db = db;
}
```
Now the object is injected.

DI is achieved using interfaces. Injecting interface we inject dependency.
A DI Container manages object creation. It: creates objects, resolves dependencies and manages lifetimes.

Example:
```csharp
builder.Services.AddScoped<IEngine, ElectricEngine>();
```

**ASP.NET** framework provides developer built-in DI container in which developer can define custom services with one of three lifetime scopes:

- **Singleton:** lifetime of service is through lifetime of application
- **Scoped:** lifetime of service is scope of one request, so for each request new service will be created
- **Transient:** each time service is requested, new instance is created

## **Microservices**

Microservice architecture represents application divided into small functional parts. Each controller represents aggregate of CRUD methods (APIs) specific for each domain class. One API is divided into layers through Clean architecture. In controller API has route and do data transfer with user interface (frontend part of application) on top side and do data transfer with service on bottom side.
Next stop to database is service. Service do business logic validation and do data transfer with repository. Repository is key layer in communication with database. It do data saving or fetching data from database. Respository has DbContext as dependency. Service has repository as dependency. And controller has service as dependency.
Repository Pattern is a design pattern used to separate data access logic from business logic. It acts as a middle layer between Application and Database.

### **Entity Framework**

Entity Framework (EF) is an Object Relational Mapping (ORM) tool provided by Microsoft.
It allows developers to work with databases using C# classes instead of writing SQL queries.

In simple words: EF lets you communicate to the database using C# code.
DbContext is used as reference to database. In DbContext we have DbSet propeeties with main classes. So that each DbSet property represents database table. So in C# EF syntax we use context.{TableName}.{OperationName}.

Example:
```csharp
context.Students.Add(student);
context.SaveChanges();

var students = context.Students.ToList();
```

EF works with extension methods (LINQ methods). Some of them are: .Where(), .Select(), .OrderBy(), .FirstOrDefault().
Example:
```csharp
var names = students
           .Where(s => s.Marks > 50)
           .Select(s => s.Name)
           .ToList();
```

### **Business logic**

The Service Layer is responsible for: handling business logic, performing validation, coordinating between controller and repository.

Controller → Service → Repository → Database
Business logic means: Rules that define how the system should work based on real-world requirements. Each domain has its own business rules.

Examples:
- Student age must be ≥ 18
- Bank withdrawal cannot exceed balance
- Email must be unique
- Order quantity cannot be negative
