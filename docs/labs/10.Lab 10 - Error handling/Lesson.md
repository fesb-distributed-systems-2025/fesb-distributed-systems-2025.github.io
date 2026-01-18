# Lesson
# Lab 10: Error Handling

## **Table of Contents**

- [Lesson](#lesson)
- [Lab 10: Error Handling](#lab-10-error-handling)
  - [**Table of Contents**](#table-of-contents)
  - [**Error Handling**](#error-handling)
    - [**Result pattern**](#result-pattern)
    - [**Exceptions logging**](#exceptions-logging)


## **Error Handling**

In a typical Web API request (Controller → Service → Repository → Database), there are two big categories of problems:

1) User / client mistakes (expected problems)

These are situations where the request is valid HTTP, but the business rules say “no”. Examples:
- Sender/Receiver doesn’t exist
- Subject is missing or too long
- Message is too long
Any other validation rule you want to enforce

These are not exceptional in the programming sense — they are normal outcomes you can predict and handle. These cases user can handle if message is enough good explained.

Application handles these with Result<T> and validation lists.

2) System / server failures (unexpected problems)

These are situations where something breaks in the system. Examples:
- A bug in code (null reference, etc.)
- Database connection fails
- Repository throws KeyNotFoundException
Any unhandled exception

These are exceptions — you generally log them and return a safe generic response. These cases handle developers from database logs.

Application handles these with ExceptionLoggingMiddleware.

So application is separating:

User-caused errors → controlled response (400, validation messages)

System exceptions → logged + generic 500 response

### **Result pattern**

The Result pattern returning outcomes instead of throwing for validation.
What Result<T> means?

Result<T> is a wrapper that says:

IsSuccess == true → the operation completed successfully

IsSuccess == false → the operation failed for expected reasons, and we have a list of messages in ErrorItems

So instead of “throwing” for validation problems, you return:

Result.Failure(["Subject is required", "Sender not found"])

This is good because:
- validation failures are expected, not “crashes”
- the service can gather multiple validation problems at once (not fail on the first one)
- the controller doesn’t need to know how validation works; it just converts the result to HTTP

ValidationResult is basically a “pre-result” used for validation: IsSuccess is true when there are no messages.

ValidationItems collects problems. Then the service converts it to a Result<object>.Failure(...).

Controller stays clean by using one “translator” method.

StatusHandler.HandleResult is extension method that is acting like a small “translator” from Result<T> to HTTP:
- If success → 200 OK with value
- If failure → 400 BadRequest with error items

```csharp
var result = await _emailService.AddEmail(email);
return this.HandleResult(result);
```

:::caution **IMPORTANT**

Controller does not do validation.
Controller does not do try/catch.
Controller just delegates and translates.

:::

### **Exceptions logging**

Exceptions can be handled and unhandled.

Handled exceptions are catched by try-catch blocks and are not loggoed automatically in ExceptionLoggingMiddleware. We need log them manually.

Unhandled exceptions can be expected and unexpected. For expected exceptions we make their "throw". That is case that we can expect will happen sometime. Example:

```csharp

if (email == null)
{
    throw new KeyNotFoundException($"Cannot find email with Id: {id}");
}

```

This error means we have some bug in application. It can be on frontend or backend. There should't be non-valid IDs in system.

For unexpected exceptions is responsible ExceptionLoggingMiddleware. It log all system failures (null reference exception, EF errors, DB errors, ...) into database.

ExceptionLoggingMiddleware is the “last safety net”. It wraps the whole pipeline, catches any unhandled exception, logs it (LogError(ex, "Unhandled exception")) and returns 500 with a generic JSON message.

Why the response is generic?

Because exceptions may contain sensitive details:
- database info
- stack traces
- internal IDs
- library versions

So the middleware returns only:

{ "error": "Internal server error" }

But the important part is: the details are still saved in logs, not sent to the user.