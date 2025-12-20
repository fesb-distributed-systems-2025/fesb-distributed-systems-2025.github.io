# Homework
# Homework 4: Data Manage and Migrations

## Homework Assignment

- update you domain classes with Code first conventions. Be careful with nullable properties - set "?" on type where you expect null value from database. Implement connections between classes (tables) using (reverse) navigation properties and foreign keys (IDs). Think about it (figure out which connection you need) and research all connections (1-1, 1-N and N-N).
- implement configuration file for each domain class. In config file is not necessary to implement all rules (because some of them are already defined with conventions), but you can do it for first time because it will not cause a problem if you have more than necessary.
- implement Program.cs file with connection string map and block of code to achieve migrations.
- start migrations via Package Manager Console
- make Services and Repositores folders and empty class of each model in them

## Extra Points

The students that implement the following and meet the criteria will be awarded with extra points:
- do HW4 in defined time - this means all code is correct till next Lab date. So take care that you have as little as possible mistakes you can. Advice: do your HW earlier so pull request can be reviewed and you can fix your mistakes if have on time.
- recognize and hanlde correctly codebooks tables if you have them in your code (hrv. šifrarnici)
- your code meet the [Coding Convention criteria](/notes/Coding%20Conventions/Coding%20Convention.md)

## Further Reading

- [Value types vs Reference types](https://www.koderhq.com/tutorial/csharp/data-types/)