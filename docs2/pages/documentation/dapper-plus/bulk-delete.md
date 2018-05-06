---
layout: default
title: Dapper Plus - Bulk Delete
permalink: bulk-delete
---

{% include template-h1.html %}
DELETE entities using Bulk Operation.

- [Delete single](#example---delete-single)
- [Delete many](#example---delete-many)
- [Delete with relation (One to One)](#example---delete-with-relation-one-to-one)
- [Delete with relation (One to Many)](#example---delete-with-relation-one-to-many)

## Example - Delete Single
DELETE a single entity with Bulk Operation.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();

    connection.BulkDelete(invoice);
}
```

## Example - Delete Many
DELETE many entities with Bulk Operation.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();

    connection.BulkDelete(invoices);
}
```

## Example - Delete with relation (One to One)
DELETE entities with a one to one relation with Bulk Operation.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();

	connection.BulkDelete(invoices.Select(x => x.Detail))
		.BulkDelete(invoices);
}
```

## Example - Delete with relation (One to Many)
DELETE entities with a one to many relation with Bulk Operation.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();

	connection.BulkDelete(invoices.SelectMany(x => x.Items))
		.BulkDelete(invoices);
}
```
