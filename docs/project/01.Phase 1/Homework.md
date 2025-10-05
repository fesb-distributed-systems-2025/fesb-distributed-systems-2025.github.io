# Phase 1 - Homework

## Table Of Contents

- [Phase 1 - Homework](#phase-1---homework)
  - [Table Of Contents](#table-of-contents)
  - [Homework Assignment](#homework-assignment)
  - [Extra Points](#extra-points)


## Homework Assignment

- Create a simple WebAPI c# application for your domain.
- The web application MUST implement the CRUD interface:
  - Create an entry e.g. Add new email
  - Read all entries e.g. Get all emails
  - Update one entry e.g. Edit one email
  - Delete one entry e.g. Delete one email
- The model MUST have at least 4 fields.
- The application MUST be functional.

## Extra Points

The students that implement any of the the following (ideally all) will be awarded with extra points:
- One model field must be an array/list e.g. An email can have multiple recepients.
- One model field must be date (DateTime class in C#)
  - Note that the DateTime will be parsed to/from ISO8601 format when converting to/from JSON
    - [How to parse and generate DateTime objects in ISO 8601 format](https://stackoverflow.com/a/36314187)
    - [ISO 8601 Datetime understanding](https://stackoverflow.com/a/52545160)
  - You can also specify a custom field converter.
    - [Specifying a custom DateTime format when serializing with Json.Net](https://stackoverflow.com/a/18639829)
  - One alternative is to use UNIX Time Since Epoch or Win32 milliseconds
    - [How to get the unix timestamp in C#](https://stackoverflow.com/a/35425123)
    - [Get time in milliseconds using C#](https://stackoverflow.com/a/4016511)
- Use another way (preferably more secure) of generating object IDs
  - [GUID](https://learn.microsoft.com/en-us/dotnet/api/system.guid.newguid?view=net-9.0)
  - Sequentially incrementing number
  - Other method