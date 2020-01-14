# SqsPoller

A small library that helps ASP.NET Core applications easily consume messages from a SQS queue

# Example

Register SqsPoller with `IServiceCollection`
```
  services.AddSqsPoller(...);
```

Create a message object and consumer that consumes the message

```
  public class UserCreated
  {
      public long Id { get; set; }
      public string FirstName {get; set; }
      public string LastName {get; set; }
      public string Email {get; set; }
  }
  
  public class SendConfirmationMessageConsumer: IConsumer<UserCreated>
  {
      public Task Consume(UserCreated message, CancellationToken cancellationToken)
      {
          // Some code
      }
  }
```

# Constraint

Each message should have a `MessageType` header and value should the name of the type that you are going to consume (i.e. `UserCreated`). 
