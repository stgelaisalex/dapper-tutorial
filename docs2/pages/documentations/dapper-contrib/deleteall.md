# Dapper Contrib - DeleteAll

## Description
DELETE ALL entities.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();

    var isSuccess = connection.DeleteAll<Invoice>();
}
```