# Phase 2 - Homework

## Table Of Contents

- [Phase 2 - Homework](#phase-2---homework)
  - [Table Of Contents](#table-of-contents)
  - [Homework Assignment](#homework-assignment)
  - [Extra Points](#extra-points)


## Homework Assignment

- Create an SQLite database with a table for storing data according to your model
- Create a repository for interfacing with SQLite - NOTE: Implement using interfaces
  - Implement CRUD - Create/Read/Update/Delete methods

## Extra Points

The students that implement any of the the following (ideally all) will be awarded with extra points:
- One model field must be an array/list e.g. An email can have multiple recepients.
  - Store that field into database using multiple tables and joins
    - One way is to create a new email (database row) for each sender-recepient pair
    - Another way is to create multiple tables and use JOINs [HINT](https://stackoverflow.com/a/17371729)
- Instead of SQLite use another database provider like MSSQL, MySQL, etc.
  