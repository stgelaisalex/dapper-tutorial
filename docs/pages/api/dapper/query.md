---
layout: default
title: Dapper - Query 
permalink: query
---

{% include template-h1.html %}

## Description
Query method is an extension method which can be called from any object of type IDbConnection. It can execute a query and map the result.

The result can be mapped to:

- [Anonymous](#example---query-anonymous)
- [Strongly Typed](#example---query-strongly-typed)
- [Multi-Mapping (One to One)](#example---query-multi-mapping-one-to-one)
- [Multi-Mapping (One to Many)](#example---query-multi-mapping-one-to-many)
- [Multi-Type](#example---query-multi-type)

### Parameters
The following table shows different parameter of an Query method.

| Name | Description |
| :--- | :---------- |
| sql         | The query to execute. |
| param       | The query parameters (default = null). |
| transaction | The transaction to use (default = null). |
| buffered    | True to buffer readeing the results of the query (default = true). |
| commandTimeout | The command timeout (default = null) |
| commandType    | The command type (default = null) |

## Example - Query Anonymous
Raw SQL query can be executed using Query method and map the result to a dynamic list.

{% highlight csharp %}
string sql = "SELECT * FROM OrderDetails";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
	connection.Open();
	
	var orderDetails = connection.Query(sql).ToList();

	Console.WriteLine(orderDetails.Count);
}
{% endhighlight %}

Click [here](https://dotnetfiddle.net/qTvEME) to run this example.

## Example - Query Strongly Typed
Raw SQL query can be executed using Query method and map the result to a strongly typed list.

{% highlight csharp %}
string sql = "SELECT * FROM OrderDetails";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
	connection.Open();
	
	var orderDetails = connection.Query<OrderDetail>(sql).ToList();

	Console.WriteLine(orderDetails.Count);
}
{% endhighlight %}

Click [here](https://dotnetfiddle.net/dXZc0s) to run this example.

## Example - Query Multi-Mapping (One to One)
Raw SQL query can be executed using Query method and map the result to a strongly typed list with a one to one relation.

{% highlight csharp %}
string sql = "SELECT * FROM Orders AS A INNER JOIN OrderDetails AS B ON A.OrderID = B.OrderID;";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
	connection.Open();

	var list = connection.Query<Order, OrderDetail, Order>(
     	sql,
     	(order, orderDetail) =>
     	{
         	order.OrderDetail = orderDetail;
         	return order;
     	},
     	splitOn: "OrderID")
 	.Distinct()
 	.ToList();

	Console.WriteLine(list.Count);
}
{% endhighlight %}

Click [here](https://dotnetfiddle.net/9HbQ0L) to run this example.

## Example - Query Multi-Mapping (One to Many)
Raw SQL query can be executed using Query method and map the result to a strongly typed list with a one to many relations.

{% highlight csharp %}
string sql = "SELECT * FROM Categories AS A INNER JOIN Products AS B ON A.CategoryID = B.CategoryID;";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
	connection.Open();
	
	var categoryDictionary = new Dictionary<int, Category>();
	
	
	var list = connection.Query<Category, Product, Category>(
     	sql,
     	(category, product) =>
     	{
         	Category categoryEntry;
         
         	if (!categoryDictionary.TryGetValue(category.CategoryID, out categoryEntry))
         	{
             	categoryEntry = category;
             	categoryEntry.Products = new List<Product>();
             	categoryDictionary.Add(categoryEntry.CategoryID, categoryEntry);
         	}

         	categoryEntry.Products.Add(product);
         	return categoryEntry;
     	},
     	splitOn: "CategoryID")
 	.Distinct()
 	.ToList();

	Console.WriteLine(list.Count);
}
{% endhighlight %}

Click [here](https://dotnetfiddle.net/Mn708g) to run this example.

## Example - Query Multi-Type
Raw SQL query can be executed using Query method and map the result to a list of different types.

{% highlight csharp %}
string sql = "SELECT * FROM Invoice;";

using (var connection = My.ConnectionFactory())
{
    connection.Open();

    var invoices = new List<Invoice>();

    using (var reader = connection.ExecuteReader(sql))
    {
        var storeInvoiceParser = reader.GetRowParser<StoreInvoice>();
        var webInvoiceParser = reader.GetRowParser<WebInvoice>();

        while (reader.Read())
        {
            Invoice invoice;

            switch ((InvoiceKind) reader.GetInt32(reader.GetOrdinal("Kind")))
            {
                case InvoiceKind.StoreInvoice:
                    invoice = storeInvoiceParser(reader);
                    break;
                case InvoiceKind.WebInvoice:
                    invoice = webInvoiceParser(reader);
                    break;
                default:
                    throw new Exception(ExceptionMessage.GeneralException);
            }

            invoices.Add(invoice);
        }
    }
    
    My.Result.Show(invoices);
}
{% endhighlight %}

