@using Z.Websites.Web.Models
@{
    var model = (IndexModel)ViewBag.Model;
}


<div style="font-size: 14px; width: 100%" class="test-aside">
    <br />
    @if (model != null)
    {
        foreach (var menuItem in model.MenuPrimary)
        {
            if (menuItem.isDowload)
            {
                <a class="btn btn-lg btn-z accent w-100 download" href="@menuItem.Url">
                    <i class="fa fa-cloud-download" aria-hidden="true"></i>
                    <span>@Html.Raw(menuItem.Content)</span>
                    <i class="fa fa-angle-right"></i>
                </a>
            }
            else
            {
                <a class="nav-link" href="@menuItem.Url">
                    @Html.Raw(menuItem.Content)
                </a>
            }
        }
    }
</div>
<!--
<div class="card card-box">
    <div class="card-header">Info</div>
    <div class="card-body">
        <ul class="list-unstyled">
            <li><a href="https://github.com/zzzprojects/EntityFramework-Plus" target="_blank">GitHub</a></li>
            <li><a href="https://stackoverflow.com/questions/tagged/entity-framework-plus" target="_blank">Stack Overflow</a></li>
            <li><a href="https://github.com/zzzprojects/EntityFramework-Plus/issues" target="_blank">Issue Tracker</a></li>
        </ul>
    </div>
</div>
</div>-->
