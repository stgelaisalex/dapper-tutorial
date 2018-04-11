---
layout: default
title: Dapper Contrib - Get
permalink: get
---

{% include template-h1.html %}

## Description
Get a single entity by ID.

{% include template-example.html %} {% highlight csharp %}
using (var connection = My.ConnectionFactory())
{
    connection.Open();

    var invoice = connection.Get<Invoice>(1);
}
{% endhighlight %}
