<ul class="navbar-nav">
    <li class="nav-item @(ViewBag.PageKind == My.PageKind.Home.ToString() ? "active": "")">
        <a class="nav-link" href="/">
            <i class="fa fa-home" aria-hidden="true"></i>
        </a>
    </li>
    <li class="nav-item @(ViewBag.PageKind == My.PageKind.Documentation.ToString() ? "active": "")">
        <a class="nav-link" href="/dapper">
            Documentations
        </a>
    </li>
    <li class="nav-item @(ViewBag.PageKind == My.PageKind.ThirdPartyLibraries.ToString() ? "active": "")">
        <a class="nav-link" href="/third-party-library">
            3<sup>rd</sup> Party Libraries
        </a>
    </li>
</ul>