---
title: Tree Node manipulation | TreeView | ASP.NET Core | Syncfusion
description: handling operations in tree Node
platform: aspnet-core
control: TreeView
documentation: UG
---

# Tree Node

The tree view node is structured with expand/collapse arrow, checkbox, image and text as shown in the following.

![](Tree-Node_images/Tree-Node_img1.jpeg)

Also the tree view node object holds the following properties.

<table>
<tr>
<td>
    {{'**Properties**'| markdownify }}
</td>
<td>
    {{'**Data Type**'| markdownify }}
</td>
<td>
    {{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
    checked
</td>
<td>
    Boolean
</td>
<td>
    Checked state of the node
</td>
</tr>
<tr>
<td>
    count
</td>
<td>
    Number
</td>
<td>
    Number of child
</td>
</tr>
<tr>
<td>
    expanded
</td>
<td>
    Boolean
</td>
<td>
    Expanded state of the node
</td>
</tr>
<tr>
<td>
    index
</td>
<td>
    Number
</td>
<td>
    Index of the node 
</td>
</tr>
<tr>
<td>
    level
</td>
<td>
    Number
</td>
<td>
    Level of the node
</td>
</tr>
<tr>
<td>
    id
</td>
<td>
    String
</td>
<td>
    Node id
</td>
</tr>
<tr>
<td>
    parentId
</td>
<td>
    String
</td>
<td>
    Parent id of the node
</td>
</tr>
<tr>
<td>
    selected
</td>
<td>
    Boolean
</td>
<td>
    Selected state of the node
</td>
</tr>
</table>

## Get/Set node value

The tree view provides a set of options to configure all its properties by setting and getting values at initialization or dynamically.

To get the node value, you can use the [getNode](http://help.syncfusion.com/js/api/ejtreeview#methods:getnode) method as shown in the following code example. Here, the node value is retrieved by button click action.

In the controller page, create a data list that contains the details about the tree nodes.
    
        
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
    
    
    
In the view page, add the following code and map the properties defined to the corresponding fields in data source.
     
    {% highlight CSHTML %}
    
      <ej-tree-view id="treeView">
	   <e-tree-view-fields datasource="ViewBag.datasource" id="Id" parent-id="Parent" text="Text">
	   </e-tree-view-fields>
	  </ej-tree-view>

    {% endhighlight %}  
    
    
In the view page, specify the following method in script tag to get the node value.
    
    {% highlight CSHTML %}
    
    <script type="text/javascript">
            //bind below onClick action to button to get node at button click or else in any action
            function onClick() {
                //create an instance from an existing TreeView.
                // only after control creation you can get treeObj otherwise it throws exception.
                treeObj = $("#treeView").ejTreeView('instance');
    
                //get node object using getNode method
                var node = treeObj.getNode("1");            
            }
            
     </script>
    
    {% endhighlight %}
    
N>**Existing tree view instance can be created by [jQuery.data()](http://api.jquery.com/jQuery.data/#) and you can control the APIs of tree view behavior**.

To edit the node text, use the [updateText](http://help.syncfusion.com/js/api/ejtreeview#methods:updatetext) method as shown in the following code example:
        
    {% highlight CSHTML %}
    
    <script type="text/javascript">
    
        //create an instance from an existing TreeView.
        // only after control creation you can get treeObj otherwise it throws exception.
        treeObj = $("#treeView").ejTreeView('instance');
    
        //get node object using getNode method
        var node = treeObj.getNode("2");
    
        //sets text to existing node 
        treeObj.updateText(node.id, "updated Item");          
        
    </script>
    
    {% endhighlight %}
    
    
## Get parent node

To get current parent node of a particular node, use the [getParent](http://help.syncfusion.com/js/api/ejtreeview#methods:getparent) method as shown in the following code example:
    
    {% highlight CSHTML %}
    
    <script type="text/javascript">
    
        //create an instance from an existing TreeView.
        // only after control creation you can get treeObj otherwise it throws exception.
        treeObj = $("#treeView").ejTreeView('instance');
    
        //get parent node using getParent method
        var node = treeObj.getParent("4");  
        
    </script>
    
    {% endhighlight %}
    
    
## Get node index

To get node index, use the [getNodeIndex](http://help.syncfusion.com/js/api/ejtreeview#methods:getnodeindex) as shown in the following code example:
           
    {% highlight javascript %}
    
    <script type="text/javascript">
    
        //create an instance from an existing TreeView.
        // only after control creation you can get treeObj otherwise it throws exception.
        treeObj = $("#treeView").ejTreeView('instance');
    
        //get node object using getNode method
        var node = treeObj.getNode("4");
    
        //gets the index of node 
        treeObj.getNodeIndex(node.id);         
        
    </script>
    
    {% endhighlight %}    
    
## Node manipulations

Perform the following operation in tree nodes and you can save the modified node values in the database.

### Add or remove nodes

To add/remove nodes programmatically, use the [addNode](http://help.syncfusion.com/js/api/ejtreeview#methods:addnode) and [removeNode](http://help.syncfusion.com/js/api/ejtreeview#methods:removenode) methods of the tree view.

    {% highlight javascript %}
    
        //create an instance from an existing TreeView.
        // only after control creation you can get treeObj otherwise it throws exception.
        treeObj = $("#treeView").ejTreeView('instance');
        var newNode = { Id: 11, Text: "Item 2.1" };
        //to add tree node
        treeObj.addNode(newNode, "2");
        
        //to remove node
        treeObj.removeNode("4");
    
    {% endhighlight %}

Add a new node after or before some tree view node by using the [insertAfter](http://help.syncfusion.com/js/api/ejtreeview#methods:insertafter) and [insertBefore](http://help.syncfusion.com/js/api/ejtreeview#methods:insertbefore) methods.

    {% highlight javascript %}
    
        //create an instance from an existing TreeView.
        // only after control creation you can get treeObj otherwise it throws exception.
        treeObj = $("#treeView").ejTreeView('instance');
        var newNode = { Id: 12, Text: "Item 2.2" };

        //to add tree node after some element, which having id 2
        treeObj.{{'**insertAfter(newNode, "2");**'| markdownify }}
    
        var newNode = { Id: 13, Text: "Item 2.3" };
        //to add tree node before some element, which having id 2
        treeObj.{{'**insertBefore(newNode, "2");**'| markdownify }}
        
    {% endhighlight %}


### Move node

You can also achieve cut and paste operation by using the [moveNode](http://help.syncfusion.com/js/api/ejtreeview#methods:movenode) method.

    {% highlight javascript %}
    
        //create an instance from an existing TreeView.
        // only after control creation you can get treeObj otherwise it throws exception.
        treeObj = $("#treeView").ejTreeView('instance');
        
        //to move tree node which having id 5, to child of node which having id 2.   
        treeObj.moveNode("5", "2");
            
    {% endhighlight %}

### Expand or collapse node

The tree nodes can be expanded or collapsed by clicking the expand/collapse icon of the node or in code behind by using the following methods.

<table>
<tr>
<td>
    {{'**Methods**'| markdownify }}
</td>
<td>
    {{'**Description**'| markdownify }}
</td>
</tr>
<tr>
<td>
    {{'[expandNode](http://help.syncfusion.com/js/api/ejtreeview#methods:expandnode)'| markdownify }}
</td>
<td>
Expands the node with specified id.
</td>
</tr>
<tr>
<td>
    {{'[collapseNode](http://help.syncfusion.com/js/api/ejtreeview#methods:collapsenode)'| markdownify }}
</td>
<td>
Collapses the node with specified id.
</td>
</tr>
<tr>
<td>
    {{'[expandAll](http://help.syncfusion.com/js/api/ejtreeview#methods:expandall)'| markdownify }}
</td>
<td>
Expands all the node.
</td>
</tr>
<tr>
<td>
    {{'[collapseAll](http://help.syncfusion.com/js/api/ejtreeview#methods:collapseall)'| markdownify }}
</td>
<td>
Collapses all the node.
</td>
</tr>
</table>

Also you can get all the expanded nodes index in tree by using the [getExpandedNodesIndex](http://help.syncfusion.com/js/api/ejtreeview#methods:getexpandednodesindex) method that returns the array of expanded node indices.

### Prevent multiple node expand

You can be able to prevent the multiple expand of tree view nodes by specifying [enableMultipleExpand](http://help.syncfusion.com/js/api/ejtreeview#members:enablemultipleexpand) as false.

For example, if you want to allow only one node to be expanded in tree view at a time. Refer to the following code block for more details.
    
    {% highlight CSHTML %}
        
        <ej-tree-view id="treeView">
		 <e-tree-view-fields datasource="ViewBag.datasource" id="Id" parent-id="Parent" text="Text" enable-multiple-expand="true">
		 </e-tree-view-fields>
		</ej-tree-view>
    
    {% endhighlight %}    
    
    
### Get updated node collection

Get the updated node values after manipulating or editing the node of tree view by using the [getTreeData](http://help.syncfusion.com/js/api/ejtreeview#methods:gettreedata) method. It returns the JSON data with modified structure in tree view.

You can also get the updated data source for remote data binding after performing the operation like editing, selecting/unselecting, expanding/collapsing, checking/unchecking and removing node. You cannot get the updated data source, when you perform operation like drag and drop, adding node for remote data binding.

The updated data source also contains custom attributes, if you return these from server.
     
    {% highlight javascript %}
    
        //create an instance from an existing TreeView.
        // only after control creation you can get treeObj otherwise it throws exception.
        treeObj = $("#treeView").ejTreeView('instance');
            
        //to get TreeView data
        treeObj.getTreeData();
    
    {% endhighlight %}
       
    
## Editing

You can directly edit the tree node’s text in-place by double-click the tree node or select the tree node, and press F2 key. The editing will works only if the [allowEditing](http://help.syncfusion.com/js/api/ejtreeview#members:allowediting) property is true in tree view control. When the editing is completed by focus out or enter key press, the modified node’s text is saved automatically.
        
    {% highlight CSHTML %}
    
      <ej-tree-view id="treeView">
	   <e-tree-view-fields datasource="ViewBag.datasource" id="Id" parent-id="Parent" text="Text" allow-editing="true">
	   </e-tree-view-fields>
	  </ej-tree-view>

    
    {% endhighlight %}
    
        
## Selection

Select a specific node by using the [selectedNode](http://help.syncfusion.com/js/api/ejtreeview#members:selectednode) property or [selectNode](http://help.syncfusion.com/js/api/ejtreeview#methods:selectnode) method.
    
    {% highlight javascript %}
    
        //create an instance from an existing TreeView.
        // only after control creation you can get treeObj otherwise it throws exception.
        treeObj = $("#treeView").ejTreeView('instance');
                
        //to select node
        treeObj.selectNode(2);
    
    {% endhighlight %}
    
## Ensure visibility

You can ensure the particular tree node is in visible state by using the [ensureVisible](http://help.syncfusion.com/js/api/ejtreeview#methods:ensurevisible) method that expands the tree nodes and scrolls the tree view control automatically.
    
    {% highlight CSHTML %}
    
        <script type="text/javascript">        
        function onClick() {
            //create an instance from an existing TreeView.
            // only after control creation you can get treeObj otherwise it throws exception.
            treeObj = $("#treeView").ejTreeView('instance');
    
            //to ensure the visibility of node
            treeObj.ensureVisible("4");
        }        
        </script>
    
    {% endhighlight %}