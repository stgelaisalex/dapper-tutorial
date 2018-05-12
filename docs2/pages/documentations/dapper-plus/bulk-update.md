# Dapper Plus - Bulk Update

## Description
UPDATE entities using Bulk Operation.

- [Update single](#example---update-single)
- [Update many](#example---update-many)
- [Update with relation (One to One)](#example---update-with-relation-one-to-one)
- [Update with relation (One to Many)](#example---update-with-relation-one-to-many)

## Example - Update Single
UPDATE a single entity with Bulk Operation.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();
    
    connection.BulkUpdate(invoice);
}
```

## Example - Update Many
UPDATE many entities with Bulk Operation.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();

    connection.BulkUpdate(invoices);
}
```

## Example - Update with relation (One to One)
UPDATE entities with a one to one relation with Bulk Operation.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();
    
    connection.BulkUpdate(invoices, x => x.Detail);
}
```

## Example - Update with relation (One to Many)
UPDATE entities with a one to many relation with Bulk Operation.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();

    connection.BulkUpdate(invoices, x => x.Items);
}
```
