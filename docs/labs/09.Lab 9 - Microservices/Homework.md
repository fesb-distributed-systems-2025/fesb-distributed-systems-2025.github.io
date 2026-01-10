# Homework
# Homework 5: Microservices

## Homework Assignment

- Implement repositories, services, controllers and all other necessary classes to achieve functional application.
- Test your APIs and application via swagger.
- Refer to professor's [repository](https://github.com/fesb-distributed-systems-2025/Zeljko9999-pokazni-project-Student/tree/1.4.0-HW05)

## **Hints**

:::caution **IMPORTANT**

Don't forget add Nuget package MediatR (Version="14.0.0") to Application project.

:::

MediatR is a .NET library that implements the Mediator design pattern. It helps you: decouple components, send commands/queries/events and avoid direct dependencies between classes

## Extra Points

The students that implement the following and meet the criteria will be awarded with extra points:
- Implement as more as you can controllers with basic and more complex (adjusted to your domain) APIs.
- Create private methods for validation of each field e.g. create a method private bool IsSenderValid(string sender) instead of copying the whole logic each time. Make sense validatadion logic adjusted to your domain.
- Do HW5 in defined time - this means all code is correct till next Lab date. So take care that you have as little as possible mistakes you can. Advice: do your HW earlier so pull request can be reviewed and you can fix your mistakes if have on time.
- Your code meet the [Coding Convention criteria](/notes/Coding%20Conventions/Coding%20Convention.md)

## Further Reading

- [How to select items from IEnumerable?](https://stackoverflow.com/questions/25510430/how-to-select-items-from-ienumerable)
- [A Beginner’s Guide to Entity Framework Core](https://medium.com/@ravipatel.it/a-beginners-guide-to-entity-framework-core-ef-core-5cde48fc7f7a)
- [Common LINQ Methods](https://dev.to/sapanapal6/common-linq-methods-with-examples-in-net-core-2m2p)