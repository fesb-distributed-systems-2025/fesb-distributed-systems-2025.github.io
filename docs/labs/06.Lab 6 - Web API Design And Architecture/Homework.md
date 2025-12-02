# Homework
# Homework 2: Architecture of web application

## Homework Assignment

- Create a simple WebAPI C# application for your domain - your domain is defined in [HW1](../../students/homework-assignments).
- Set application solution as shown in [Lesson](./Lesson)
- The web application must implement the CRUD operations in controller:
  - Create an entry e.g. Add new student
  - Read all entries e.g. Get all students
  - Read one entry e.g. Get one student by Id
  - Update one entry e.g. Edit one student
  - Delete one entry e.g. Delete one student
- Make at least one model that have at least 5 fields (properties).
- Make at least one DTO.
- Refer to professor's [repository](https://github.com/fesb-distributed-systems-2025/Zeljko9999-pokazni-project-Student/tree/1.0.0-HW02) and make same for your domain
- Push to github and make pull request

## Extra Points

The students that implement the following (ideally all) will be awarded with extra points:
- More doimain classes (models)
- At least one model field (property) must be an array/list e.g. An email can have multiple receivers.
- At least one model field must be bool e.g. An email can be important.
- At least one model field must be date (DateTime class in C#):
  - Note that the DateTime will be parsed to/from ISO8601 format when converting to/from JSON
    - [How to parse and generate DateTime objects in ISO 8601 format](https://stackoverflow.com/a/36314187)
    - [ISO 8601 Datetime understanding](https://stackoverflow.com/a/52545160)
  - You can also specify a custom field converter.
    - [Specifying a custom DateTime format when serializing with Json.Net](https://stackoverflow.com/a/18639829)
  - One alternative is to use UNIX Time Since Epoch or Win32 milliseconds
    - [How to get the unix timestamp in C#](https://stackoverflow.com/a/35425123)
    - [Get time in milliseconds using C#](https://stackoverflow.com/a/4016511)

## **Hints**

- Don't forget commits naming convention that we learned in [Lab04](../../labs/04.Lab 4 - Git Basics)


## Further Reading

- [Lambda Expressions in C#](https://www.c-sharpcorner.com/UploadFile/bd6c67/lambda-expressions-in-C-Sharp/)
- [IEnumerable](https://www.c-sharpcorner.com/UploadFile/0c1bb2/ienumerable-interface-in-C-Sharp/)
- [Controller Route](https://learn.microsoft.com/en-us/aspnet/web-api/overview/web-api-routing-and-actions/routing-in-aspnet-web-api)
- [DTOs](https://konstantinmb.medium.com/dtos-101-the-what-why-and-how-of-data-transfer-objects-304a03a71a2c)