---
layout: post
title: TreeView with Multiple Selection | TreeView | ASP.NET Core | Syncfusion
description: specify multiple selection option in TreeView and its settings
platform: aspnet-core
control: TreeView
documentation: ug
---

# Multiple Selection

TreeView supports to select the multiple nodes by specifying [allowMultiSelection](http://help.syncfusion.com/js/api/ejtreeview#members:allowmultiselection) as true. It allows you to select more than one nodes in TreeView.

In the controller page, create a data list that contains the details about tree nodes.

{% highlight c# %}

	public partial class TreeViewController : Controller
	{
		// GET: Custom
		List<LoadData> tree1 = new List<LoadData>();
		public ActionResult Index()
		{
			tree1.Add(new LoadData { Id = 1, Parent = 0, Text = "Item 1",selected=true });
			tree1.Add(new LoadData { Id = 2, Parent = 0, Text = "Item 2" });
			tree1.Add(new LoadData { Id = 3, Parent = 0, Text = "Item 3" });
			tree1.Add(new LoadData { Id = 4, Parent = 0, Text = "Item 4" });
			tree1.Add(new LoadData { Id = 5, Parent = 1, Text = "Item 1.1", ,selected=true });
			tree1.Add(new LoadData { Id = 6, Parent = 1, Text = "Item 1.2" });
			tree1.Add(new LoadData { Id = 7, Parent = 1, Text = "Item 1.3" });
			tree1.Add(new LoadData { Id = 8, Parent = 3, Text = "Item 3.1" });
			tree1.Add(new LoadData { Id = 9, Parent = 3, Text = "Item 3.2" });
			tree1.Add(new LoadData { Id = 10, Parent = 5, Text = "Item 1.1.1" });
			ViewBag.datasource = tree1;
			return View();
		}
	}
	
	public class LoadData
	{
	        public int Id;
            public int Parent;
            public string Text;
	}


{% endhighlight %}

In the view page, add the below code and map the properties defined in to the corresponding fields in data source and specify the **AllowMultiSelection** property.

{% highlight CSHTML %}

    <ej-tree-view id="treeView" allow-multi-selection="true"><e-tree-view-fields datasource="ViewBag.datasource" id="Id" parent-id="Parent" text="Text"></e-tree-view-fields></ej-tree-view>
	
{% endhighlight %}

By running the above code, output will be below.
![](Fullrowselection_images/multiselect.png)


## Select Nodes

To select more than one nodes of TreeView, you can use [selectedNodes](http://help.syncfusion.com/js/api/ejtreeview#members:selectednodes) property. It will select the TreeView nodes from the given indexes.

In the view page, add the below code and map the properties defined in to the corresponding fields in data source and we you can select the specific nodes in TreeView by using **selectedNodes** property.

{% highlight CSHTML %}

    <ej-tree-view id="treeView" allow-multi-selection="true"><e-tree-view-fields datasource="ViewBag.datasource" id="Id" parent-id="Parent" text="Text"></e-tree-view-fields></ej-tree-view>
	
{% endhighlight %}

{% highlight js %}

	$(function () {
        // create instance for TreeView
        var treeObj = $("#treeView").data("ejTreeView");

        treeObj.option("selectedNodes", [0, 5, 6]); //select the TreeView nodes from the given indexes
    });
	
{% endhighlight %}

## Get Selected Nodes

To get the selected Nodes of TreeView, you can use [getSelectedNodes](http://help.syncfusion.com/js/api/ejtreeview#methods:getselectednodes) method. It returns the collections of TreeView selected nodes.

In the view page, add the below code and map the properties defined in to the corresponding fields in data source and we you can get selected nodes from TreeView by using **getSelectedNodes** method.

{% highlight CSHTML %}

    <ej-tree-view id="treeView" allow-multi-selection="true"><e-tree-view-fields datasource="ViewBag.datasource" id="Id" parent-id="Parent" text="Text"></e-tree-view-fields></ej-tree-view>

{% endhighlight %}

{% highlight js %}

	$(function () {
        // create instance for TreeView
        var treeObj = $("#treeView").data("ejTreeView");

        treeObj.getSelectedNodes(); //returns the collections of TreeView selected nodes
    });
	
{% endhighlight %}