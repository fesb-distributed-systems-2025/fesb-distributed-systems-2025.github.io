# Lesson
# Lab 6: Web API Design

## **Table of Contents**

- [Lesson](#lesson)
- [Lab 6: Web API Design and Architecture](#lab-6-web-api-design)
  - [**Table of Contents**](#table-of-contents)
    - [**Requirements**](#requirements)
    - [**Objectives**](#objectives)
    - [**Web API**](#web-api)
    - [**SOA**](#soa)
      - [**REST API example**](#rest-api-example)
    - [**ASP.NET**](#aspnet)


### **Requirements**

- [.NET 7 SDK](https://dotnet.microsoft.com/en-us/download)
- [Postman application](https://www.postman.com/downloads/)

### **Objectives**

In this LAB you will learn about different web api designs, applications architectures and how to implement them.

### **Web API**

A **Web API** is an application programming interface for either a web server or a web browser.
It is a web development concept, usually limited to a web application's client-side (including any web frameworks being used),
and thus usually does not include web server or browser implementation details such as SAPIs or APIs unless publicly accessible by a remote web application.

### **SOA**

**SOA** or Service-Oriented Architecture is a style of software design in
to which defined services provide service to other application components over the network protocol.
**SOA** is technology, product and platform independent.

According to the definition of service-oriented architecture, a service is defined by the following properties:

- describes business logic with a specific outcome
- the service is self-contained
- the logic is isolated from the consumer, the consumer does not need to know the implementation details
- may include other services.

Common views on SOA architecture are:

- **REST**
- **GraphQL**
- **gRPC**
- **SOAP**
- **WCF**

**REST** architecture is most commonly used and easiest to implement because all modern web server frameworks support it by default.

We have worked on REST in past labs and in this lab we will focus on **GraphQL** abd **gRPC**.

### **REST API example**

| URL                                           | METHOD | Explanation                     |
| --------------------------------------------- | ------ | ------------------------------- |
| <http://mystudentsapp.com/students>           | GET    | Get All students                |
| <http://mystudentsapp.com/students?name=Mate> | GET    | Get All students with name Mate |
| <http://mystudentsapp.com/students/1>         | GET    | Get student with id 1           |
| <http://mystudentsapp.com/students/>          | POST   | Create student                  |
| <http://mystudentsapp.com/students/1>         | PUT    | Update student with id 1        |
| <http://mystudentsapp.com/students/1>         | DELETE | Delete student with id 1        |


Testing and sending requests with Postman:

![postman](postman.jpg)

## **ASP.NET**

ASP.NET is Microsoft's web server framework to handle all of hard work for us.
In **ASP.NET** applications it is common practice to utilize Inversion of Control (IoC) Container.
IoC container or in some references Dependency Injection (DI) is a pattern used commonly through many business applications
to inject necessary dependencies (usually services) into classes requiring these dependencies.

**ASP.NET** framework provides developer with build in DI container in which developer can define custom services with one of three lifetime scopes:

- **Singleton:** lifetime of service is through lifetime of application
- **Scoped:** lifetime of service is scope of one request, so for each request new service will be created
- **Transient:** each time service is requested, new instance is created

## **Clean architecture**

![clean-architecture](clean-architecture.PNG)

More find gere: https://www.milanjovanovic.tech/blog/clean-architecture-folder-structure