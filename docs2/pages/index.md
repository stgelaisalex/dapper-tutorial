<div class="new-hero">
    <div id="particles-js-triangles"></div>
    <div class="container">
        <div class="text-center">
            <h1>
                Dapper ORM
                <span>A NuGet library that will extend your IDbConnection interface<br/> with awesome extensions!</span>
            </h1>

        </div>
        <br>
        <div class="d-flex justify-content-center">
            <a href="https://www.nuget.org/packages/Dapper" target="_blank" class="btn-only download">
                <i class="fa fa-cloud-download" aria-hidden="true"></i>
                Download Now
            </a>
        </div>
    </div>
    <div class="nectar-shape-divider-wrap " data-front="" data-style="curve" data-position="bottom">
        <svg class="nectar-shape-divider" fill="#ffffff" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 1000 100" preserveAspectRatio="none"> <path d="M 0 0 c 0 0 200 50 500 50 s 500 -50 500 -50 v 101 h -1000 v -100 z"></path> </svg>
    </div>
    <div id="code-mirror-container">
```csharp
string sql = "SELECT * FROM Invoices";

using (var conn = My.ConnectionFactory())
{
    var invoices = conn.Query&lt;Invoice&gt;(sql);
}
```
    </div>
</div>

    

<div id="test-do" class="container faq">
    <h2 class="title-section-index text-center">Dapper FAQ</h2>
    <br>
    <div class="row">
        <div class="col-sm">
            <i class="fa fa-sitemap" aria-hidden="true"></i>
            <br>
            <br>
            <h3 class="title">Is Dapper an ORM?</h3>
            <p>Yes and no! People are still arguing about it. Dapper has earned the title of king of the C# Micro ORM but is considered by multiple people as a simple object mapper for .NET.</p>
        </div>
        <div class="col-sm middle">
            <i class="fa fa-line-chart" aria-hidden="true"></i>
            <br>
            <br>
            <h3 class="title">Is Dapper better than Entity Framework?</h3>
            <p>Yes and no! People will prefer Dapper when they want to write the SQL query themselves with optimal performance.</p>
        </div>
        <div class="col-sm">
            <i class="fa fa-exclamation-triangle" aria-hidden="true"></i>
            <br>
            <br>
            <h3 class="title">Is Dapper SQL Injections safe?</h3>
            <p>Yes, it's 100% safe if you use parametrized queries as you should always do!</p>
        </div>
    </div>
    <br>
    <br>
    <div class="row">
        <div class="col-sm">
            <i class="fa fa-caret-square-o-down" aria-hidden="true"></i>
            <br>
            <br>
            <h3 class="title">Do Dapper support Bulk Insert?</h3>
            <p>No, but a third-party library does: <a href="http://dapper-plus.net/" target="_blank">Dapper Plus</a>. It's a prime library that extend Dapper with all bulk operations.</p>
            <a href="http://dapper-plus.net/" target="_blank" class="btn btn-z">Learn More</a>
        </div>
        <div class="col-sm middle">
            <i class="fa fa-database" aria-hidden="true"></i>
            <br>
            <br>
            <h3 class="title">Do Dapper support my database provider?</h3>
            <p>Probably yes since Dapper provides extensions to the IDbConnection interface. It's your job to write the SQL compatible with your database provider.</p>
        </div>
        <div class="col-sm">
            <i class="fa fa-exchange" aria-hidden="true"></i>
            <br>
            <br>
            <h3 class="title">Do Dapper support Transaction?</h3>
            <p>Yes, Dapper support transaction and every method that can use one have an optional parameter to specify it.</p>
        </div>
    </div>
</div>

<div class="dark-section mt-5">
    <div class="container">
        <div class="example-feature">
            <h2 class="wow slideInUp" style="visibility: visible; animation-name: slideInUp;">Execute</h2>
            <div class="row">
                <div class="col-lg-5 wow slideInLeft" style="visibility: visible; animation-name: slideInLeft;">
                    <p class="feature-tagline">Execute a command one or multiple times and return the number of affected rows.</p>
                    <ul>
                        <li>Stored Procedure</li>
                        <li>INSERT statement</li>
                        <li>UPDATE statement</li>
                        <li>DELETE statement</li>
                    </ul>
                    <div class="more-info">
                        <a href="/execute" class="btn btn-lg btn-z" role="button">
                            <i class="fa fa-book"></i>&nbsp;
                            Read More
                        </a>
                    </div>
                </div>
                <div class="col-lg-7 wow slideInRight" style="visibility: visible; animation-name: slideInRight;">
                    <div class="card card-code card-code-dark">
                        <div class="card-header"><h5>Auditing Example</h5></div>
                        <div class="card-body">   
```csharp
string sql = "Invoice_Insert";

using (var connection = My.ConnectionFactory())
{
    var affectedRows = connection.Execute(sql,
    new {Kind = InvoiceKind.WebInvoice, Code = "Single_Insert_1"},
    commandType: CommandType.StoredProcedure);

    My.Result.Show(affectedRows);
}
```
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="example-feature">
            <h2 class="wow slideInUp" style="visibility: visible; animation-name: slideInUp;">Query</h2>
            <div class="row">
                <div class="col-lg-5 wow slideInLeft" style="visibility: visible; animation-name: slideInLeft;">
                    <p class="feature-tagline">Execute a query and map the result.</p>
                    <ul>
                        <li><a href="/query">Query</a></li>
                        <li><a href="/queryfirst">QueryFirst</a></li>
                        <li><a href="/queryfirstordefault">QueryFirstOrDefault</a></li>
                        <li><a href="/querysingle">QuerySingle</a></li>
                        <li><a href="/querysingleordefault">QuerySingleOrDefault</a></li>
                        <li><a href="/querymultiple">QueryMultiple</a></li>
                    </ul>
                </div>
                <div class="col-lg-7 wow slideInRight" style="visibility: visible; animation-name: slideInRight;">
                    <div class="card card-code card-code-dark">
                        <div class="card-header"><h5>Delete Example</h5></div>
                        <div class="card-body">
```csharp
string sql = "SELECT * FROM OrderDetails";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
    var orderDetails = connection.Query(sql).ToList();

    Console.WriteLine(orderDetails.Count);
}
```
                        </div>
                    </div>
                </div>
            </div>
        </div>
        
        <div class="example-feature">
            <h2 class="wow slideInUp" style="visibility: visible; animation-name: slideInUp;">Parameters</h2>
            <div class="row">
                <div class="col-lg-5 wow slideInLeft" style="visibility: visible; animation-name: slideInLeft;">
                    <p class="feature-tagline">Use parameter in your Dapper query.</p>
                    <ul>
                        <li><a href="/parameter-anonymous">Anonymous</a></li>
                        <li><a href="/parameter-dynamic">Dynamic</a></li>
                        <li><a href="/parameter-list">List</a></li>
                        <li><a href="/parameter-string">String</a></li>
                    </ul>
                </div>
                <div class="col-lg-7 wow slideInRight" style="visibility: visible; animation-name: slideInRight;">
                    <div class="card card-code card-code-dark">
                        <div class="card-header"><h5>Delete Example</h5></div>
                        <div class="card-body">
```csharp
string sql = "INSERT INTO Customers (CustomerName) Values (@@CustomerName);";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{
    var affectedRows = connection.Execute(sql, new {CustomerName = "Mark"});

    Console.WriteLine(affectedRows);
}
```
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <div class="example-feature">
            <h2 class="wow slideInUp" style="visibility: hidden; animation-name: none;">Result</h2>
            <div class="row">
                <div class="col-lg-5 wow slideInLeft" style="visibility: hidden; animation-name: none;">
                    <p class="feature-tagline">Map the query result to different types.</p>
                    <ul>
                        <li><a href="/result-anonymous">Anonymous</a></li>
                        <li><a href="/result-strongly-typed">Strongly Typed</a></li>
                        <li><a href="/result-multi-mapping">Multi-Mapping</a></li>
                        <li><a href="/result-multi-result">Multi-Result</a></li>
                        <li><a href="/result-multi-type">Multi-Type</a></li>
                    </ul>
                </div>
                <div class="col-lg-7 wow slideInRight" style="visibility: hidden; animation-name: none;">
                    <div class="card card-code card-code-dark">
                        <div class="card-header"><h5>Update Example</h5></div>
                        <div class="card-body">
```csharp
string sql = "SELECT * FROM OrderDetails";

using (var connection = new SqlCeConnection("Data Source=SqlCe_W3Schools.sdf"))
{	
    var orderDetails = connection.Query&lt;OrderDetail&gt;(sql).ToList();

    Console.WriteLine(orderDetails.Count);
}
```
                        </div>
                    </div>
                </div>
            </div>
            </div>
        </div>
    </div>

<div class="container mt-5 mb-5 contact">
    <h2 class="title-section-index">Consulting</h2>
    <div class="row">
        <div class="text-left col-sm border-right">

            <p>
                Your company requires some custom solution to extend Dapper with more features?
            </p>
            <p>
                Contact us to learn about our consultation services:
                <br>
                <a href="mailto:info@zzzprojects.com">info@zzzprojects.com</a>
            </p>
        </div>
        <div class="text-center col-sm">
            You can also find some answers/help on:
            <br><br>
            <a href="https://stackoverflow.com/questions/tagged/dapper" target="_blank" class="btn-only">Stack Overflow</a> <a href="https://github.com/StackExchange/Dapper/issues" target="_blank" class="btn-only">Issue tracker</a>
        </div>
    </div>
</div>
