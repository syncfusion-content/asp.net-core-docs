---
title: State Persistence  | TreeView | ASP.NET Core | Syncfusion
description: State Persistence option in TreeView
platform: aspnet-core
control: TreeView
documentation: UG
---

# State Persistence

TreeView state can be persisted by using ‘**EnablePersistence**’. In which user intractable model values only has been persisted in order to maintain performance. 

The model values of below are maintained through id basis of tree node.

* selected
* checked
* expanded/ collapsed state

N>**In "UL" "li" template state has been persisted by index.**

TreeView stores its model in local storage / cookies of browser before page refreshes and reinitialized with their stored model after refresh.

In the controller page, create a data list that contains the details about tree nodes.
    
    {% highlight c# %}
    
    public partial class TreeViewController : Controller
        {
            List<LoadData> treeData = new List<LoadData>();
            public ActionResult TreeViewFeatures()
            {
                treeData.Add(new LoadData { Id = 1, Parent = 0, Text = "Item 1" });
                treeData.Add(new LoadData { Id = 2, Parent = 0, Text = "Item 2" });
                treeData.Add(new LoadData { Id = 3, Parent = 0, Text = "Item 3" });
                treeData.Add(new LoadData { Id = 4, Parent = 0, Text = "Item 4" });
                treeData.Add(new LoadData { Id = 5, Parent = 1, Text = "Item 1.1" });
                treeData.Add(new LoadData { Id = 6, Parent = 1, Text = "Item 1.2" });
                treeData.Add(new LoadData { Id = 7, Parent = 1, Text = "Item 1.3" });
                treeData.Add(new LoadData { Id = 8, Parent = 3, Text = "Item 3.1" });
                treeData.Add(new LoadData { Id = 9, Parent = 3, Text = "Item 3.2" });
                treeData.Add(new LoadData { Id = 10, Parent = 5, Text = "Item 1.1.1" });
                ViewBag.datasource = treeData;
                return View();
            }
        }
    
    {% endhighlight %}
    
    
In the view page, add the below code with following properties.

    
    {% highlight CSHTML %}
    
        <ej-tree-view id="treeview"><e-tree-view-fields datasource="ViewBag.datasource" id="Id" parent-id="Parent" text="Text" enable-persistence="true"></e-tree-view-fields></ej-tree-view>
    
    {% endhighlight %} 