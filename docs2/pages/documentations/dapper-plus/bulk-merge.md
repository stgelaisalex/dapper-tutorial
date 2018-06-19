# Dapper Plus - Bulk Merge

## Description
MERGE entities using Bulk Operation.

- [Merge single](#example---merge-single)
- [Merge many](#example---merge-many)
- [Merge with relation (One to One)](#example---merge-with-relation-one-to-one)
- [Merge with relation (One to Many)](#example---merge-with-relation-one-to-many)

## Example - Merge Single
MERGE a single entity with Bulk Operation.

```csharp
DapperPlusManager.Entity<Customer>().Table("Customers"); 

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
	connection.BulkMerge(new List<Customer>() { new Customer() { CustomerName = "ExampleBulkInsert", ContactName = "Example Name :" +  1}});
}		
```
{% include component-try-it.html href='https://dotnetfiddle.net/T3R43T' %}

## Example - Merge Many
MERGE many entities with Bulk Operation.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();

    connection.BulkMerge(invoices);
}
```
{% include component-try-it.html href='https://dotnetfiddle.net/T3R43T' %}

## Example - Merge with relation (One to One)
MERGE entities with a one to one relation with Bulk Operation.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();

	connection.BulkMerge(invoices)
		.ThenForEach(x => x.Detail.InvoiceID = x.InvoiceID)
		.ThenBulkMerge(x => x.Detail);
}
```

## Example - Merge with relation (One to Many)
MERGE entities with a one to many relation with Bulk Operation.

```csharp
using (var connection = My.ConnectionFactory())
{
    connection.Open();

	connection.BulkMerge(invoices)
		.ThenForEach(x => x.Items.ForEach(y => y.InvoiceID = x.InvoiceID))
		.ThenBulkMerge(x => x.Items);
}
```
