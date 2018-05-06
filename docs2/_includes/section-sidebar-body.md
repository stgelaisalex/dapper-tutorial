@if (ViewBag.PageKind == My.PageKind.Documentation.ToString())
{
<nav class="card card-box2 card-box-light2 card-box-nav">
    <div class="card-body">
        <h3><span>Dapper</span>Getting Started</h3>
        <ul>
            <li>
                <a href="/dapper">Introduction</a>
            </li>
        </ul>

        <h3>Methods</h3>
        <ul>
            <li>
                <a href="/execute">Execute</a>
            </li>
            <li>
                <a href="/query">Query</a>
            </li>
            <li>
                <a href="/queryfirst">QueryFirst</a>
            </li>
            <li>
                <a href="/queryfirstordefault">QueryFirstOrDefault</a>
            </li>
            <li>
                <a href="/querysingle">QuerySingle</a>
            </li>
            <li>
                <a href="/querysingleordefault">QuerySingleOrDefault</a>
            </li>
            <li>
                <a href="/querymultiple">QueryMultiple</a>
            </li>
        </ul>
        <h3>Parameters</h3>
        <ul>
            <li>
                <a href="/parameter-anonymous">Anonymous</a>
            </li>
            <li>
                <a href="/parameter-dynamic">Dynamic</a>
            </li>
            <li>
                <a href="/parameter-list">List</a>
            </li>
            <li>
                <a href="/parameter-string">String</a>
            </li>
        </ul>

        <h3>Result</h3>
        <ul>
            <li>
                <a href="/result-anonymous">Anonymous</a>
            </li>
            <li>
                <a href="/result-strongly-typed">Strongly Typed</a>
            </li>
            <li>
                <a href="/result-multi-mapping">Multi-Mapping</a>
            </li>
            <li>
                <a href="/result-multi-result">Multi-Result</a>
            </li>
            <li>
                <a href="/result-multi-type">Multi-Type</a>
            </li>
        </ul>

        <h3>Utilities</h3>
        <ul>
            <li>
                <a href="/async">Async</a>
            </li>
            <li>
                <a href="/buffered">Buffered</a>
            </li>
            <li>
                <a href="/transaction">Transaction</a>
            </li>
            <li>
                <a href="/stored-procedure">Stored Procedure</a>
            </li>
        </ul>

        <h3><span>Dapper Plus</span>Getting started</h3>
        <ul>
            <li>
                <a href="/dapper-plus">Introduction</a>
            </li>
        </ul>
        <h3>Methods</h3>
        <ul>
            <li>
                <a href="/bulk-insert">Bulk Insert</a>
            </li>
            <li>
                <a href="/bulk-update">Bulk Update</a>
            </li>
            <li>
                <a href="/bulk-delete">Bulk Delete</a>
            </li>
            <li>
                <a href="/bulk-merge">Bulk Merge</a>
            </li>
        </ul>
        <h3><span>Dapper Contrib</span>Getting started</h3>
        <ul>
            <li>
                <a href="/dapper-contrib">Introduction</a>
            </li>
        </ul>
        <h3>Methods</h3>
        <ul>
            <li>
                <a href="/get">Get</a>
            </li>
            <li>
                <a href="/getall">GetAll</a>
            </li>
            <li>
                <a href="/insert">Insert</a>
            </li>
            <li>
                <a href="/update">Update</a>
            </li>
            <li>
                <a href="/delete">Delete</a>
            </li>
            <li>
                <a href="/deleteall">DeleteAll</a>
            </li>
        </ul>
        <h3>Data Annotations</h3>
        <ul>
            <li>
                <a href="/data-annotation-key">Key</a>
            </li>
            <li>
                <a href="/data-annotation-explicitkey">ExplicitKey</a>
            </li>
            <li>
                <a href="/data-annotation-table">Table</a>
            </li>
            <li>
                <a href="/data-annotation-write">Write</a>
            </li>
            <li>
                <a href="/data-annotation-computed">Computed</a>
            </li>
        </ul>
    </div>
</nav>
}
else if (ViewBag.PageKind == My.PageKind.ThirdPartyLibraries.ToString())
{
    <nav class="card card-box2 card-box-light2 card-box-nav">
        <div class="card-body">
            <h3>Methods</h3>
            <ul>
                <li>
                    <a href="/third-party-library">Overview</a>
                </li>
                <li>
                    <a href="/dapper-plus-third-party-library">Dapper.Plus</a>
                </li>
                <li>
                    <a href="/dapper-async">Dapper-Async</a>
                </li>
                <li>
                    <a href="/dapper-contrib-third-party-library">Dapper.Contrib</a>
                </li>
                <li>
                    <a href="/dapper-extensions">DapperExtensions</a>
                </li>
                <li>
                    <a href="/dapper-fastcrud">Dapper.FastCrud</a>
                </li>
                <li>
                    <a href="/dapper-fluentmap">Dapper.FluentMap</a>
                </li>
                <li>
                    <a href="/dapper-mapper">Dapper.Mapper</a>
                </li>
                <li>
                    <a href="/dapper-rainbow">Dapper.Rainbow</a>
                </li>
                <li>
                    <a href="/dapper-simplecrud">Dapper.SimpleCRUD</a>
                </li>
                <li>
                    <a href="/dapper-simplesave">Dapper.SimpleSave</a>
                </li>
            </ul>
        </div>
    </nav>
}