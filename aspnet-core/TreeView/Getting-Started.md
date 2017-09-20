---
layout: post
title: Getting Started with TreeView | TreeView | ASP.NET Core | Syncfusion
description:  To get start with TreeView by adding references
platform: aspnet-core
control: TreeView
documentation: ug
---

# Getting started	

This section explains briefly about how to create a TreeView in ASP.NET Core platform.

## Create your first TreeView in ASP.NET Core

Create an ASP.NET Core Project and add Syncfusion assembly packages, CSS and scripts with the help of the given [ASP.NET Core-Getting Started](https://help.syncfusion.com/aspnet-core/getting-started) documentation. After creating this project, you can create a TreeView in following ways.

## TreeView using Helper element

You can create a tree using “Items” API of TreeView control. Here there is no necessary to use a data source for rendering TreeView. 

In the view page, add TreeView helper as shown below. It will render the TreeView with specified items.
    
  {% highlight CSHTML %}

           <ej-tree-view id="tree">
            <e-tree-view-items>
                <e-tree-view-item text="Item 1">
                    <e-tree-view-child-items>
                        <e-tree-view-child-item text="Item 1.1">
                            <e-tree-view-child-items>
                                <e-tree-view-child-item text="Item 1.1.1">
                                </e-tree-view-child-item>
                            </e-tree-view-child-items>
                        </e-tree-view-child-item>               
                    </e-tree-view-child-items>
                </e-tree-view-item>
                <e-tree-view-item text="Item 2">
                    <e-tree-view-child-items>
                        <e-tree-view-child-item text="Item 2.1"></e-tree-view-child-item>
                        <e-tree-view-child-item text="Item 2.2"></e-tree-view-child-item>                
                    </e-tree-view-child-items>
                </e-tree-view-item>
                <e-tree-view-item text="Item 3">
                    <e-tree-view-child-items>
                        <e-tree-view-child-item text="Item 3.1"></e-tree-view-child-item>               
                    </e-tree-view-child-items>
                </e-tree-view-item>       
            </e-tree-view-items>
        </ej-tree-view>
                
  {% endhighlight %}    

By running the above code, output will like below image,
![](Getting_started_images/getting_started_img1.png)

## Render TreeView using Razor Syntax   

You can create a tree using “Items” API of TreeView control. Here there is no necessary to use a data source for rendering TreeView.

In the view page, add TreeView as shown below. It will render the TreeView with specified items.

{% highlight CSHTML %}

    @{Html.EJ().TreeView("tree").Items(items =>
        {
            items.Add().Text("File").Children(child =>
            {
                child.Add().Text("New");
                child.Add().Text("Open");
                child.Add().Text("Save");
                child.Add().Text("Save As");
                child.Add().Text("Print Preview");
                child.Add().Text("Print");
                child.Add().Text("Close");
            });
            items.Add().Text("Edit").Children(child =>
            {
                child.Add().Text("Undo");
                child.Add().Text("Redo");
                child.Add().Text("Cut");
                child.Add().Text("Copy");
                child.Add().Text("Paste");
            });
            items.Add().Text("Insert").Children(child =>
            {
                child.Add().Text("Page Numbers");
                child.Add().Text("Table");
                child.Add().Text("Picture");
                child.Add().Text("Comment");
                child.Add().Text("Links");
                child.Add().Text("Symbols");
                child.Add().Text("Diagram");
                child.Add().Text("TextBox");
                child.Add().Text("Data Time");
            });
            items.Add().Text("Format").Expanded(true).Children(child =>
            {
                child.Add().Text("Font").Children(childs =>
                {
                    childs.Add().Text("Arial");
                    childs.Add().Text("Arial Black");
                    childs.Add().Text("Arial Narrow");
                    childs.Add().Text("Courier");
                    childs.Add().Text("Gaurand");
                    childs.Add().Text("Times New Roman");
                    childs.Add().Text("Vrendra");
                    childs.Add().Text("Helvatica");
                    childs.Add().Text("Impact");
                });
                child.Add().Text("Paragraph");
                child.Add().Text("Bullets and Numbering");
                child.Add().Text("Borders and Shading");
                child.Add().Text("Columns");
                child.Add().Text("Tabs");
                child.Add().Text("Change Case");
            });
            items.Add().Text("View").Children(child =>
            {
                child.Add().Text("Normal");
                child.Add().Text("Web Layout");
                child.Add().Text("Print Layout");
                child.Add().Text("Task Pane");
            });
            items.Add().Text("Tools").Children(child =>
            {
                child.Add().Text("Spelling and Grammar");
                child.Add().Text("Research");
                child.Add().Text("Language");
                child.Add().Text("Word Count");
                child.Add().Text("Track Changes");
                child.Add().Text("Merge Documents");
            });
        }).Render();}

{% endhighlight %}    

By running the above code, output will like below image,
![](Getting_started_images/getting_started_img2.png)

## TreeView using Data Binding

Another way of creating TreeView is binding with the data source, you can bind local data source to create a TreeView. 

Render TreeView with local data source.

In the model page, specify the TreeView node properties as shown below.
    
    

  {% highlight c# %}

    public class LoadData
    {
        public int Id { get; set; }
        public int Parent { get; set; }
        public string Text { get; set; }
    }
    
   {% endhighlight %}
    
    
    
In the controller page, create a data list which contains the details about tree nodes.
    
    
    
   {% highlight c# %}

    public partial class TreeViewController : Controller
    {
        List<LoadData> load = new List<LoadData>();
        public ActionResult TreeViewFeatures()
        {
            load.Add(new LoadData { Id = 1, Parent = 0, Text = "Item 1" });
            load.Add(new LoadData { Id = 2, Parent = 0, Text = "Item 2" });
            load.Add(new LoadData { Id = 3, Parent = 0, Text = "Item 3" });
            load.Add(new LoadData { Id = 4, Parent = 1, Text = "Item 1.1" });
            load.Add(new LoadData { Id = 5, Parent = 1, Text = "Item 1.2" });
            load.Add(new LoadData { Id = 6, Parent = 3, Text = "Item 3.1" });
            ViewBag.datasource = load;
            return View();
        }
    }
    
   {% endhighlight %}
    
    
    
Above data can be directly assigned to DataSource property and mapping data fields with respect to the mapper field in order to form TreeView.
    
    
    
  {% highlight CSHTML %}
    
    <ej-tree-view id="tree1">
        <e-tree-view-fields datasource="@ViewBag.datasource" id="Id" parent-id="Parent" text="Text"></e-tree-view-fields>
    </ej-tree-view>
    
  {% endhighlight %}
    
By running the above code, result will like below image,
![](Getting_started_images/getting_started_img3.png)


## Create Instance for TreeView

You can create an instance for existing TreeView in following ways. Once a reference has been established, you can use the [API’s](http://help.syncfusion.com/js/api/ejtreeview) of TreeView to control its behavior.
    
        
   {% highlight javascript %}
    
    <script type="text/javascript">
        //Specify this after your TreeView creation
        //create instance for TreeView
        var treeObj = $("#treeView").ejTreeView('instance');
        //or
        var treeObj1 = $("#treeView").data("ejTreeView");
    </script>
    
   {% endhighlight %}
    
    
    
N>**To configure the API settings after TreeView creation, please refer [API configuration](http://help.syncfusion.com/js/api-configuration), [Invoking Methods](http://help.syncfusion.com/js/invoking-methods)**.
 
## TreeView events

ASP.NET Core TreeView supports all the [events](http://help.syncfusion.com/js/api/ejtreeview#events) which is available in EJ TreeView. Refer the following code example to specify an event using Tag helper of TreeView.
    
   
   {% highlight CSHTML %}
    
    <ej-tree-view id="tree1" node-expand="onNodeExpanded" node-collapse="onNodeCollapsed" node-select="onNodeSelected">
        <e-tree-view-fields datasource="@ViewBag.datasource" id="Id" parent-id="Parent" text="Text"></e-tree-view-fields>
    </ej-tree-view>
    
    <script type="text/javascript">
        function onNodeCollapsed(args) {
            //Handle the node collapse event
        }
    
        function onNodeExpanded(args) {
            //Handle the node expand event
        }
    
        function onNodeSelected(args) {
            //Handle the node select event
        }
    </script>
    
   {% endhighlight %}
    
    
 