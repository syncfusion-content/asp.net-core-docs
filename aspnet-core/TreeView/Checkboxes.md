---
title: Checkboxes in TreeView | TreeView | ASP.NET Core | Syncfusion
description: specify checkboxes in TreeView and its settings
platform: aspnet-core
control: TreeView
documentation: UG
---
    
# Checkboxes

The tree view consists of built-in checkbox option and it is displayed to the left of the tree node by setting the **ShowCheckbox** property as true. It allows you to select more than one node at a time.
 
## Indeterminate checkboxes
 
The tree view supports tri-state checkboxes in addition to the standard two-state checkboxes. By default, the tree view is enabled with tri-state in checkboxes. You can enable the two-state checkboxes by setting the **AutoCheckParentNode** as false.
    
    {% highlight CSHTML %}
    
       <ej-tree-view id="treeView" show-checkbox="true" auto-check-parent-node="false"><e-tree-view-fields datasource="ViewBag.datasource" id="Id" parent-id="Parent" text="Text"></e-tree-view-fields></ej-tree-view>

    {% endhighlight %}
    
By running the above code, you will get the output like the following image.
![](Checkboxes_images/checkbox_images_img1.png)

## Auto checkable

By default, checkbox state of child nodes depends on the parent node checkbox state and also the parent node state gets updated based on the child nodes state. You can turn off this option by setting **AutoCheck** as false to make independent parent and child nodes checkboxes.
    
    {% highlight CSHTML %}
    
        <ej-tree-view id="treeView" show-checkbox="true" auto-check="false"><e-tree-view-fields datasource="ViewBag.datasource" id="Id" parent-id="Parent" text="Text"></e-tree-view-fields></ej-tree-view>
   
    {% endhighlight %}
    
## Check or uncheck node

The tree node can be checked or unchecked by using the [checkNode](http://help.syncfusion.com/js/api/ejtreeview#methods:checknode) and [uncheckNode](http://help.syncfusion.com/js/api/ejtreeview#methods:unchecknode) methods, when the **showCheckbox** property is enabled in tree view. The [nodeCheck](http://help.syncfusion.com/js/api/ejtreeview#events:nodecheck) and [nodeUncheck](http://help.syncfusion.com/js/api/ejtreeview#events:nodeuncheck) events occurs based on the checkbox state.

    {% highlight javascript %}
    
        //create an instance from an existing TreeView.
        // only after control creation you can get treeObj otherwise it throws exception.
        treeObj = $("#treeView").ejTreeView('instance');
                
        //to check node
        treeObj.checkNode("2");
    
        //to uncheck node
        treeObj.uncheckNode("2");
    
    
    {% endhighlight %}

## Get checked nodes

To get the checked nodes of tree view, use the [getCheckedNodes](http://help.syncfusion.com/js/api/ejtreeview#methods:getcheckednodes) method. It returns the collection of checked tree nodes.

    {% highlight CSHTML %}
    
    <script type="text/javascript">
        function onClick() {
            //create an instance from an existing TreeView.
            // only after control creation you can get treeObj otherwise it throws exception.
            treeObj = $("#treeView").ejTreeView('instance');
    
            //to get checkednodes
            treeObj.getCheckedNodes();
        }        
    </script>
    
    {% endhighlight %}