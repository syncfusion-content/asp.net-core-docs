---
layout: post
title: Searching | TreeGrid | ASP.NET Core | Syncfusion
description: Searching
platform: aspnet-core
control: TreeGrid
documentation: ug
---

## Searching

The TreeGrid control has an option to search its content using toolbar search box. The toolbar search box can be enabled by using the `ToolbarSettings.ToolbarItems` property. The following code example explains how to integrate search textbox in toolbar.

{% highlight CSHTML %}

<ej-tree-grid id="TreeGridContainer">
    <e-tree-grid-toolbar-settings show-toolbar="true" toolbar-items="ViewBag.toolbarItems">
    </e-tree-grid-toolbar-settings>
</ej-tree-grid>

{% endhighlight %}

{% highlight C# %}

public partial class TreeGridController : Controller
{
    public ActionResult Default()
    {
        ViewBag.toolbarItems = new List<String>() { "search" };
        return View();
    }
}

{% endhighlight %}

The below screenshot shows TreeGrid search with `plan` key word.
![](Searching_images/Searching_img1.png)