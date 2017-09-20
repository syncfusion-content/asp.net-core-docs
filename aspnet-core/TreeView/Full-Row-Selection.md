---
layout: post
title: TreeView with Full Row Selection | TreeView | ASP.NET Core | Syncfusion
description: specify full row selection option in TreeView and its settings
platform: aspnet-core
control: TreeView
documentation: ug
---

# Full Row Selection

The TreeView control provides the option to highlight a full row of tree view nodes. When **FullRowSelect** is **true**, a selection highlights the entire width of the tree view, display instead of the width of just the tree node text. It makes selection easier.

In the controller page, create a data list that contains the details about tree nodes.

{% highlight c# %}

public partial class TreeViewController : Controller
{
    // GET: MultiSelection
    List<loadondemand> fullRowData = new List<loadondemand>();
    public ActionResult FullRowSelection()
    {
        fullRowData.Add(new loadondemand { id = 1, name = "Discover Music", hasChild = true, expanded = true });
        fullRowData.Add(new loadondemand { id = 2, pid = 1, name = "Hot Singles", selected = true });
        fullRowData.Add(new loadondemand { id = 3, pid = 1, name = "Rising Artists" });
        fullRowData.Add(new loadondemand { id = 4, pid = 1, name = "Live Music" });
        fullRowData.Add(new loadondemand { id = 6, pid = 1, name = "Best of 2013 So Far" });
        fullRowData.Add(new loadondemand { id = 7, name = "Sales and Events", hasChild = true, expanded = true });
        fullRowData.Add(new loadondemand { id = 8, pid = 7, name = "100 Albums - $5 Each" });
        fullRowData.Add(new loadondemand { id = 9, pid = 7, name = "Hip-Hop and R&B Sale" });
        fullRowData.Add(new loadondemand { id = 10, pid = 7, name = "CD Deals" });
        fullRowData.Add(new loadondemand { id = 11, name = "Categories", hasChild = true });
        fullRowData.Add(new loadondemand { id = 12, pid = 11, name = "Songs" });
        fullRowData.Add(new loadondemand { id = 13, pid = 11, name = "Bestselling Albums" });
        fullRowData.Add(new loadondemand { id = 14, pid = 11, name = "New Releases" });
        fullRowData.Add(new loadondemand { id = 15, pid = 11, name = "Bestselling Songs" });
        fullRowData.Add(new loadondemand { id = 16, name = "MP3 Albums", hasChild = true });
        fullRowData.Add(new loadondemand { id = 17, pid = 16, name = "Rock" });
        fullRowData.Add(new loadondemand { id = 18, pid = 16, name = "Gospel" });
        fullRowData.Add(new loadondemand { id = 19, pid = 16, name = "Latin Music" });
        fullRowData.Add(new loadondemand { id = 20, pid = 16, name = "Jazz" });
        fullRowData.Add(new loadondemand { id = 21, name = "More in Music", hasChild = true });
        fullRowData.Add(new loadondemand { id = 22, pid = 21, name = "Music Trade-In" });
        fullRowData.Add(new loadondemand { id = 23, pid = 21, name = "Redeem a Gift Card" });
        fullRowData.Add(new loadondemand { id = 24, pid = 21, name = "Band T-Shirts" });
        fullRowData.Add(new loadondemand { id = 25, pid = 21, name = "Mobile MVC" });

        ViewBag.datasource = fullRowData;
        return View();
    }
}

public class loadondemand
{
    public int id { get; set; }
    public int? pid { get; set; }
    public string name { get; set; }
    public bool? hasChild { get; set; }
    public bool? expanded { get; set; }
    public bool? selected { get; set; }
}

{% endhighlight %}

In the view page, add the below code and map the properties defined in to the corresponding fields in data source and specify the **FullRowSelect** property.

{% highlight CSHTML %}

    <ej-tree-view id="treeView" full-row-select="true"><e-tree-view-fields datasource="ViewBag.datasource" id="id" parent-id="pid" text="name" has-child="hasChild" expanded="expanded"></e-tree-view-fields></ej-tree-view>

{% endhighlight %}

By running the above code, output will look like below.
![](Fullrowselection_images/selection1.png)

## Customization

You can customize the TreeView full row selection for template support by using **CssClass** property. Based on this custom class, you can customize the height of the highlighting TreeView node.

In the controller page, create a data list that contains the details about tree nodes.

{% highlight c# %}

public partial class TreeViewController : Controller
{
    // GET: MultiSelection
    List<loadondemand> fullRowData = new List<loadondemand>();
    public ActionResult FullRowSelection()
    {
        fullRowData.Add(new loadondemand { id = 1, name = "Browsers", cls = "browser", hasChild = true, expanded = true });
        fullRowData.Add(new loadondemand { id = 2, pid = 1, name = "Internet Explorer", cls = "ieb", selected = true });
        fullRowData.Add(new loadondemand { id = 3, pid = 1, name = "Chrome", cls = "chromeb" });
        fullRowData.Add(new loadondemand { id = 4, pid = 1, name = "Firefox", cls = "firefoxb" });
        fullRowData.Add(new loadondemand { id = 6, pid = 1, name = "Bitty", cls = "bittyb" });
        fullRowData.Add(new loadondemand { id = 7, pid = 1, name = "Opera", cls = "operab" });
        ViewBag.datasource = fullRowData;
        return View();
    }
}

public class loadondemand
{
        public int id { get; set; }
        public int? pid { get; set; }
        public string name { get; set; }
        public bool? hasChild { get; set; }
        public bool? expanded { get; set; }
        public bool? selected { get; set; }
        public string cls { get; set; }
}

{% endhighlight %}

In the view page, add the below code and map the properties defined in to the corresponding fields in data source and specify the **CssClass** property.

{% highlight CSHTML %}

    <ej-tree-view id="treeView" full-row-select="true" css-class="custom" template="#treeTemplate"><e-tree-view-fields datasource="ViewBag.datasource" id="id" parent-id="pid" text="name" has-child="hasChild" expanded="expanded"></e-tree-view-fields></ej-tree-view>

<script id="treeTemplate" type="text/x-jsrender">

    {{if !hasChild}}
    <span class="con-img {{>cls}}"></span>
    {{/if}}
    {{>name}}

</script>
	
{% endhighlight %}

{% highlight css %}

<style>
	.custom .con-img {
        background-image: url("http://mvc.syncfusion.com/demos/web/images/toolbar/browserl.png");
        background-repeat: no-repeat;
        height: 32px;
        width: 32px;
        display: inline-block;
        overflow: hidden;
        background-repeat: no-repeat;
        text-align: center;
        vertical-align: middle;
    }
    
    .custom .e-li-active > .e-text-wrap .con-img {
        background-image: url("http://mvc.syncfusion.com/demos/web/images/toolbar/browserh.png");
    }
    
    .custom .e-li-hover > .e-text-wrap .con-img, .e-fullrow-wrap .e-li-focus > .e-text-wrap .con-img {
        background-image: url("http://mvc.syncfusion.com/demos/web/images/toolbar/browserl.png");
    }
    
    .custom .ieb {
        background-position: -84px 0px;
    }
    
    .custom .chromeb {
        background-position: -42px 0px;
    }
    
    .custom .firefoxb {
        background-position: 0px 0px;
    }
    
    .custom .bittyb {
        background-position: -126px 0px;
    }
    
    .custom .operab {
        background-position: -168px 0px;
    }
    
    /*customize the height of highlighting TreeView node*/
    .custom.e-fullrow-wrap .e-item ul .e-fullrow {
        margin-top: -36px;
        height: 36px;
    }

</style>

{% endhighlight %}

By running the above code, output will be below.
![](Fullrowselection_images/custom.png)