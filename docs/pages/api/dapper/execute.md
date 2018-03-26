---
layout: default
title: Dapper - Execute 
permalink: execute
---

{% include template-h1.html %}

## Description
Execute is an extension method which can be called from any object of type IDbConnection. It can execute a command one or multiple times and return the number of affected rows. This method is usually used to execute:
- [Stored Procedure](#example---execute-stored-procedure)
- [INSERT statement](#example---execute-insert)
- [UPDATE statement](#example---execute-update)
- [DELETE statement](#example---execute-delete)

### Parameters
The following table shows different parameter of an Execute method.

| Name | Description |
| :--- | :---------- |
| sql            | The command text to execute. |
| param          | The command parameters (default = null). |
| transaction    | The transaction to use (default = null). |
| commandTimeout | The command timeout (default = null) |
| commandType    | The command type (default = null) |

## Example - Execute Stored Procedure

### Single
Execute the Stored Procedure a single time.

{% highlight csharp %}
string sql = "Invoice_Insert";

using (var connection = My.ConnectionFactory())
{
    connection.Open();

    var affectedRows = connection.Execute(sql,
        new {Kind = InvoiceKind.WebInvoice, Code = "Single_Insert_1"},
        commandType: CommandType.StoredProcedure);

    My.Result.Show(affectedRows);
}
{% endhighlight %}

<img src="images/3-anonynous-entity.png" alt="Stored Procedure Single" />

### Many
Execute the Stored Procedure multiple times. Once for every object in the array list.

{% highlight csharp %}
string sql = "Invoice_Insert";

using (var connection = My.ConnectionFactory())
{
    connection.Open();

    var affectedRows = connection.Execute(sql,
        new[]
        {
            new {Kind = InvoiceKind.WebInvoice, Code = "Many_Insert_1"},
            new {Kind = InvoiceKind.WebInvoice, Code = "Many_Insert_2"},
            new {Kind = InvoiceKind.StoreInvoice, Code = "Many_Insert_3"}
        },
        commandType: CommandType.StoredProcedure
    );

    My.Result.Show(affectedRows);
}
{% endhighlight %}

## Example - Execute INSERT

### Single
Execute the INSERT Statement a single time.

{% highlight csharp %}
string sql = "INSERT INTO Customers (CustomerName) Values (@CustomerName);";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
	connection.Open();
	var affectedRows = connection.Execute(sql, new {CustomerName = "Mark"});
}
{% endhighlight %}

Click [here](https://dotnetfiddle.net/P2uw27) to run this example.

### Many
Execute the INSERT Statement multiple times. Once for every object in the array list.

{% highlight csharp %}
string sql = "INSERT INTO Customers (CustomerName) Values (@CustomerName);";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
	connection.Open();
	
	var affectedRows = connection.Execute(sql,
 		new[]
 		{
     		new {CustomerName = "John"},
     		new {CustomerName = "Andy"},
     		new {CustomerName = "Allan"}
 		}
	);	
}
{% endhighlight %}

Click [here](https://dotnetfiddle.net/vHOVx6) to run this example.

## Example - Execute UPDATE

### Single
Execute the UPDATE Statement a single time.

{% highlight csharp %}
string sql = "Update Categories Set Description = @Description where CategoryID = @CategoryID;";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
	connection.Open();
	
	var affectedRows = connection.Execute(sql,new {CategoryID = 1, Description = "Soft drinks, coffees, teas, beers, mixed drinks, and ales"});

	Console.WriteLine(affectedRows);
}
{% endhighlight %}

Click [here](https://dotnetfiddle.net/CWdH6z) to run this example.

### Many
Execute the UPDATE Statement multiple times. Once for every object in the array list.

{% highlight csharp %}
string sql = "Update Categories Set Description = @Description where CategoryID = @CategoryID;";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
	connection.Open();
	
	var affectedRows = connection.Execute(sql,
 		new[]
 		{
     		new {CategoryID = 1, Description = "Soft drinks, coffees, teas, beers, mixed drinks, and ales"},
     		new {CategoryID = 4, Description = "Cheeses and butters etc."}
 		}
	);

	Console.WriteLine(affectedRows);
	
}
{% endhighlight %}

Click [here](https://dotnetfiddle.net/qCdKI3) to run this example.

## Example - Execute DELETE

### Single
Execute the DELETE Statement a single time.

{% highlight csharp %}
string sql = "DELETE FROM Customers WHERE CustomerID = @CustomerID";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
	connection.Open();
	
	var affectedRows = connection.Execute(sql, new {CustomerID = 1});

	Console.WriteLine(affectedRows);
}
{% endhighlight %}

Click [here](https://dotnetfiddle.net/4bFT32) to run this example.

### Many
Execute the DELETE Statement multiple times. Once for every object in the array list.

{% highlight csharp %}
string sql = "DELETE FROM OrderDetails WHERE OrderDetailID = @OrderDetailID";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
	connection.Open();
	
	var affectedRows = connection.Execute(sql, 
		new[]
 		{
     		new {OrderDetailID = 1},
     		new {OrderDetailID = 2},
     		new {OrderDetailID = 3}
 		}
	);

	Console.WriteLine(affectedRows);
}
{% endhighlight %}

Click [here](https://dotnetfiddle.net/nxP1vL) to run this example.