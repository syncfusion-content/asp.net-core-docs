---
title: Checkboxes in TreeView | TreeView | ASP.NET Core | Syncfusion
description: specify checkboxes in TreeView and its settings
platform: aspnet-core
control: TreeView
documentation: UG
---
    
# Checkboxes

TreeView consists of built-in checkbox option and it can be displayed to the left of the tree node by setting the **ShowCheckbox** property as true. It allows you to select more than one node at a time.
 
## Indeterminate Checkboxes
 
TreeView supports tristate checkboxes in addition with standard two state checkboxes. By default Treeview has been enabled with tristate in checkboxes. You can enable 2-state checkboxes by using **AutoCheckParentNode** as false. 
    
    {% highlight CSHTML %}
    
       <ej-tree-view id="treeView" show-checkbox="true" auto-check-parent-node="false"><e-tree-view-fields datasource="ViewBag.datasource" id="Id" parent-id="Parent" text="Text"></e-tree-view-fields></ej-tree-view>

    {% endhighlight %}
    
By running the above code, output will be look like below image.
![](Checkboxes_images/checkbox_images_img1.png)

## Auto Checkable

By default checkbox state of child nodes depends up on parent node checkbox state and also parent node state gets updated based on child nodes state. You can turn off this option by setting **AutoCheck** as false to make independent parent and child nodes checkboxes. 
    
    {% highlight CSHTML %}
    
        <ej-tree-view id="treeView" show-checkbox="true" auto-check="false"><e-tree-view-fields datasource="ViewBag.datasource" id="Id" parent-id="Parent" text="Text"></e-tree-view-fields></ej-tree-view>
   
    {% endhighlight %}
    
## Check or Uncheck Node

Tree node can be checked or unchecked using [checkNode](http://help.syncfusion.com/js/api/ejtreeview#methods:checknode) and [uncheckNode](http://help.syncfusion.com/js/api/ejtreeview#methods:unchecknode) methods while ‘showCheckbox’ property is enabled in TreeView. [nodeCheck](http://help.syncfusion.com/js/api/ejtreeview#events:nodecheck) and [nodeUncheck](http://help.syncfusion.com/js/api/ejtreeview#events:nodeuncheck) event occurs based on checkbox state.

    {% highlight javascript %}
    
        //create an instance from an existing TreeView.
        // only after control creation you can get treeObj otherwise it throws exception.
        treeObj = $("#treeView").ejTreeView('instance');
                
        //to check node
        treeObj.checkNode("2");
    
        //to uncheck node
        treeObj.uncheckNode("2");
    
    
    {% endhighlight %}

## Get Checked Nodes

To get checked nodes of TreeView, you can use [getCheckedNodes](http://help.syncfusion.com/js/api/ejtreeview#methods:getcheckednodes) method. It returns the collection of checked tree nodes.

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