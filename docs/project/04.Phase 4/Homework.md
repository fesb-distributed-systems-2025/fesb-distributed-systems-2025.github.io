# Phase 4 - Homework

## Table Of Contents

- [Phase 4 - Homework](#phase-4---homework)
  - [Table Of Contents](#table-of-contents)
  - [Homework Assignment](#homework-assignment)
    - [Error Handling](#error-handling)
    - [DTOs](#dtos)
    - [Configuration](#configuration)
  - [Extra Points](#extra-points)
    - [Error Handling](#error-handling-1)
    - [DTOs](#dtos-1)
    - [Configuration](#configuration-1)


## Homework Assignment

### Error Handling
1. Create custom exceptions for the application
2. Implement validation and exception throwing in *Logic* class
3. Implement error handling filter.

### DTOs
1. Create specific DTOs for the application
2. Update controllers to accept and return DTOs instead of the model

### Configuration
1. Add *ConnectionString* to the `appsettings.json` file.
2. Implement configuration reading from the `appsettings.json` for the *ConnectionString*
3. Update *Repository* class to read value from the `appsettings.json` instead of hardcoding the connection string. 

## Extra Points
The students that implement any of the the following (ideally all) will be awarded with extra points:

### Error Handling
1. Currently, the *ErrorFilter* has to be registered for each controller. This leaves room for human error if a developer misses a controller, which would mean the application would break or the hacker could get internal information if an error occur in that controller. For extra points, find a way to register the *ErrorFilter* to each controller by default. HINT: This would probably require changing the code in `Program.cs`. 

### DTOs
1. Instead of manually creating model objects from DTOs in controller and vice versa, like below, in each DTO class create two public functions:
   1. `public Email ToModel()` - A function that creates a new `Email` model from the DTO
   2. `public static NewMailRequestDTO FromModel(Email model)` - A function that takes a model `Email` and copies all fields to the DTO

:::danger **Manually creating DTOs and models**
```csharp
public class EmailController : ControllerBase
{
    // ...

    [HttpGet("all")]
    public IEnumerable<MailDTO> GetEmails()
    {
        var emailList = _emailLogic.GetEmails();
        return emailList.Select(x => new MailDTO
        {
            Id = x.Id,
            Subject = x.Subject,
            Message = x.Message,
            Sender = x.Sender,
            Recepient = x.Recepient
        });
    }

    [HttpPost("new")]
    public IEnumerable<MailDTO> AddNewEmail([FromBody] NewMailRequestDTO email)
    {
        // [BAD] Manually creating model from DTO
        Email model = new Email(
             email.Sender,
             email.Recepient,
             email.Subject,
             email.Message
        );

        var emailList = _emailLogic.AddEmail(model);

        // [BAD] Manually creating DTO from model
        return emailList.Select(x => new MailDTO
        {
            Id = x.Id,
            Subject = x.Subject,
            Message = x.Message,
            Sender = x.Sender,
            Recepient = x.Recepient
        });
    }

    // ...
}
```
:::

:::tip **Creating conversion methods**
```csharp
// --------------- DTO\NewMailRequestDTO.cs - BEGIN

    public class NewMailRequestDTO
    {
        [JsonPropertyName("sender")]
        public string? Sender { get; set; }

        [JsonPropertyName("recepient")]
        public string? Recepient { get; set; }

        [JsonPropertyName("subject")]
        public string? Subject { get; set; }

        [JsonPropertyName("message")]
        public string? Message { get; set; }

        // Added two methods for converting Model <-> DTO
        public Email ToModel()
        {
            return new Email
            (
                 this.Sender,
                 this.Recepient,
                 this.Subject,
                 this.Message
            );
        }

        public static NewMailRequestDTO FromModel(Email model)
        {
            return new NewMailRequestDTO
            {
                Subject = model.Subject,
                Message = model.Message,
                Sender = model.Sender,
                Recepient = model.Recepient
            };
        }
    }

// --------------- DTO\NewMailRequestDTO.cs - END
```
```csharp
// --------------- DTO\MailDTO.cs - BEGIN

    public class NewMailRequestDTO
    {
        [JsonPropertyName("id")]
        public long Id { get; set; }

        [JsonPropertyName("sender")]
        public string? Sender { get; set; }

        [JsonPropertyName("recepient")]
        public string? Recepient { get; set; }

        [JsonPropertyName("subject")]
        public string? Subject { get; set; }

        [JsonPropertyName("message")]
        public string? Message { get; set; }

        // Added two methods for converting Model <-> DTO

        public Email ToModel()
        {
            return new Email
            (
                 this.Id,
                 this.Sender,
                 this.Recepient,
                 this.Subject,
                 this.Message
            );
        }

        public static MailDTO FromModel(Email model)
        {
            return new MailDTO
            {
                Id = model.Id,
                Subject = model.Subject,
                Message = model.Message,
                Sender = model.Sender,
                Recepient = model.Recepient
            };
        }
    }

// --------------- DTO\MailDTO.cs - END
```
```csharp
// --------------- Controllers\EmailController.cs - BEGIN
public class EmailController : ControllerBase
{
    // ...

    [HttpGet("all")]
    public IEnumerable<MailDTO> GetEmails()
    {
        var emailList = _emailLogic.GetEmails();

        // [GOOD] Better way of converting models to DTOs
        return emailList.Select( x => MailDTO.FromModel(x) );
    }

    [HttpPost("new")]
    public IEnumerable<MailDTO> AddNewEmail([FromBody] NewMailRequestDTO email)
    {
        // [GOOD] Better way of converting a DTO to model
        Email model = email.ToModel();

        var emailList = _emailLogic.AddEmail(model);

        // [GOOD] Better way of converting models to DTOs
        return emailList.Select( x => MailDTO.FromModel(x) );
    }

    // ...
}
// --------------- Controllers\EmailController.cs - END
```
:::

### Configuration
1. Create configuration values for validation parameters e.g. maximum number of characters in certain fields, and update logic class to read this configuration.

:::info **An example of appsettings.json**
```json
{
  "Logging": {
    "LogLevel": {
      "Default": "Information",
      "Microsoft.AspNetCore": "Warning"
    }
  },
  "AllowedHosts": "*",
    "Database": {
        "ConnectionString": "Data Source=S:\\PI_DIS_24_25\\pkaselj-lab-07\\bin\\Debug\\net6.0\\emails.db"
    },
    "Validation": {
        "MaxSubjectLength": 50,
        "MaxMessageLength": 1000,
        "MaxEmailLength": 50
    }
}

```
:::