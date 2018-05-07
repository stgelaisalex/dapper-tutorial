# Dapper Contrib - GetAll

## Description
GET ALL entities.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();

    var invoices = connection.GetAll<Invoice>().ToList();
}
```