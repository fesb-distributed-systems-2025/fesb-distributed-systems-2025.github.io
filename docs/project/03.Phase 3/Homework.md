# Phase 3 - Homework

## Table Of Contents

- [Phase 3 - Homework](#phase-3---homework)
  - [Table Of Contents](#table-of-contents)
  - [Homework Assignment](#homework-assignment)
  - [Extra Points](#extra-points)


## Homework Assignment

- Create a Logic class
- Implement valdiation in the logic class

## Extra Points

The students that implement any of the the following (ideally all) will be awarded with extra points:
- Use regular expressions (regex)
- Create private methods for validation of each field e.g. create a method `private bool IsSenderValid(string sender)` instead of copying the whole logic each time. For example see the code below.

:::danger

**BAD**

```csharp
class EmailLogic : IEmailLogic
{
  public IEnumerable<Email> AddEmail(Email email)
  {
    if(email is null)
    {
      // ...
    }
    else if(email.Sender.Length == 0)
    {
      // ...
    }
    else if(email.Sender.Length > 50)
    {
      // ...
    }
    // ...
  }

  public IEnumerable<Email> EditEmail(Email email)
  {
    if(email is null)
    {
      // ...
    }
    else if(email.Sender.Length == 0)
    {
      // ...
    }
    else if(email.Sender.Length > 50)
    {
      // ...
    }
    // ...
  }
}
```

:::


:::success

**GOOD**

```csharp
class EmailLogic : IEmailLogic
{

  private bool IsSenderValid(string sender)
  {
    // ... your code here ...
  }

  public IEnumerable<Email> AddEmail(Email email)
  {
    if(email is null)
    {
      // ...
    }
    else if(!IsSenderValid(email.Sender))
    {
      // ...
    }
  }

  public IEnumerable<Email> EditEmail(Email email)
  {
    if(email is null)
    {
      // ...
    }
    else if(!IsSenderValid(email.Sender))
    {
      // ...
    }
  }
}
```

:::