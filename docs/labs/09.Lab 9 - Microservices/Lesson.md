# Lesson
# Lab 9: Microservices

## **Table of Contents**

- [Lesson](#lesson)
- [Lab 9: Microservices](#lab-9-microservices)
  - [**Table of Contents**](#table-of-contents)
    - [**Requirements**](#requirements)
    - [**Objectives**](#objectives)
  - [**Microservices**](#microservices)
    - [**Defining Relationships in Classes**](#defining-relationships-in-classes)
    - [**Codebook tables**](#codebook-tables)


## **Microservices**

**ASP.NET** framework provides developer with build in DI container in which developer can define custom services with one of three lifetime scopes:

- **Singleton:** lifetime of service is through lifetime of application
- **Scoped:** lifetime of service is scope of one request, so for each request new service will be created
- **Transient:** each time service is requested, new instance is created