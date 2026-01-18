# Homework
# Homework 6: Error Handling

## Homework Assignment

- Implement error handling concepts into services and controllers.
- Implement exception logging middleware and Serilog service.
- Test your APIs and application via swagger.
- Refer to professor's [repository](https://github.com/fesb-distributed-systems-2025/Zeljko9999-pokazni-project-Student/tree/1.5.0-HW06)

## **Hints**

:::caution **IMPORTANT**

Don't forget add Nuget packages Serilog.AspNetCore (Version="8.0.3"), Serilog.Settings.Configuration (Version="8.0.4") and Serilog.Sinks.MSSqlServer (Version="9.0.2") to `Api` project.

:::

Serilog is a structured logging library for .NET that allows developers to capture rich, queryable log data in a variety of outputs.

## Extra Points

The students that implement the following and meet the criteria will be awarded with extra points:
- Implement valid error handling and exception logging to all implemented APIs (don't need to non-implemented APIs).
- Do HW5 in defined time - this means all code is correct till next Lab date. So take care that you have as little as possible mistakes you can. Advice: do your HW earlier so pull request can be reviewed and you can fix your mistakes if have on time.
- Your code meet the [Coding Convention criteria](/notes/Coding%20Conventions/Coding%20Convention.md)

## Further Reading

- [How To Replace Exceptions with Result Pattern in .NET](https://antondevtips.com/blog/how-to-replace-exceptions-with-result-pattern-in-dotnet)