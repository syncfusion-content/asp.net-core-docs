---
layout: post
title: Editing with Grid widget for Syncfusion Essential ASP.NET Core
description:  How to perform editing and configure edit time functionalities like edit type, edit time controls etc
platform: ASP.NET Core
control: Grid
documentation: ug
---
# Editing

The grid control has support for dynamic insertion, updation and deletion of records. You can start the edit action either by double clicking the particular row or by selecting the required row and clicking on Edit icon in toolbar. Similarly, you can add new record to grid either by clicking on insert icon in toolbar or on an external button which is bound to call `addRecord` method of grid.  `Save` and `Cancel` while on edit mode is possible using respective toolbar icon in grid.

Deletion of the record is possible by selecting the required row and clicking on Delete icon in toolbar. 

The primary key for the data source should be defined in `Columns` definition, for editing to work properly. In `Columns` definition, particular primary column's `IsPrimaryKey` property should be set to `true`. Refer the Knowledge base [link](http://www.syncfusion.com/kb/2675/cant-edit-any-row-except-the-first-row-in-grid# "link") for more information.

N> 1. In grid, the primary key column will be automatically set to read only while editing the row, but you can specify primary key column value while adding a new record.
N> 2. The column which is specified as `IsIdentity` will be in readonly mode both while editing and adding a record. Also, auto incremented value is assigned to that `IsIdentity` column.

## Toolbar with edit option

Using toolbar which is rendered at the top of the grid header, you can show all the CRUD related action. To enable toolbar and toolbar items, set `ShowToolbar` property as true and `ToolbarItems`. The default toolbar items are `Add`, `Edit`, `Delete`, `Update` and `Cancel`.

N> For `ToolbarItems` property you can assign either `string` value ("Add") or `enum` value (`Syncfusion.JavaScript.ToolBarItems.Add`).

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing(); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
              {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
				col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("ShipCity").HeaderText("Ship City").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
              }).Render();
         }      
{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                    var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                    ViewBag.DataSource = DataSource;
                    return View();
                 }
             }
        } 
{% endhighlight  %}    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img1.png)

## Cell edit type and its edit options

The edit type of bound column can be customized using `EditType` property of `Columns`. The following Essential JavaScript controls are supported built-in by `EditType`. You can set the `EditType` based on specific data type of the column. 

* `NumericTextBox` control for integers, double, and decimal data types.
* `DatePicker` control for date data type.
* `DateTimePicker` control for date-time data type.
* `DropDownList` control for list of data type.

And also you can define the model for all the editTypes controls while editing through EditOptions.

The following table describes `EditType` and their corresponding EditOptions of the specific data type of the column.

<table>
<tr>
<th>
EditType</th><th>
EditParams</th><th>
Example</th></tr>
<tr>
<td>
NumericTextBox </td><td>
{{ '[TextBoxes]' | markdownify }} </td><td>
NumericEditOptions(new EditorProperties() { DecimalPlaces = 2,  })</td></tr>
<tr>
<td>
DatePicker </td><td>
{{ '[DatePicker]' | markdownify }} </td><td>
DateEditOptions(new DatePickerProperties() { ButtonText="Now"})</td></tr>
<tr>
<td>
DateTimePicker</td><td>
{{ '[DateTimePicker]' | markdownify }} </td><td>
DateTimeEditOptions(new DateTimePickerProperties() {})</td></tr>
</table>

N> 1. If `EditType` is not set, then by default it will display the input element ("string") while editing a column.
N> 2. For `EditType` property you can assign either `string` value ("Numeric") or `enum` value (`Syncfusion.JavaScript.EditingType.Numeric`).

The following code example describes the above behavior 

{% tabs %}
{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing(); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
			       col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
				   col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).NumericEditOptions(new EditorProperties() { DecimalPlaces = 2 }).Add();
                   col.Field("ShipCity").HeaderText("Ship City").EditType(EditingType.Dropdown).Add();
                   col.Field("ShipCountry").HeaderText("Ship Country").Add();
                   col.Field("OrderDate").HeaderText("Order Date").EditType(EditingType.Datepicker).DateEditOptions(new DatePickerProperties() { ButtonText="Now"}).Format("{0:MM/dd/yyyy}").Add();            
                   col.Field("Verified").HeaderText("Verified").EditType(EditingType.Boolean).Add();

                }).Render();
           }      
{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img2.png)

## Cell Edit Template

On editing the column values, custom editor can be created by using `EditTemplate` property of `Columns`. It has three functions, they are

1. `Create` - It is used to create the control at time of initialize.
2. `Read` - It is used to read the input value at time of save.
3. `Write` - It is used to assign the value to control at time of editing.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing(); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
              {
                 col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).Add();
                 col.Field("CustomerID").HeaderText("Customer ID").Add();
			     col.Field("Freight").HeaderText("Freight").Add();
                 col.Field("ShipCountry").HeaderText("Ship Country").Add();
                 col.Field("ShipPostalCode").HeaderText("Ship Postal Code").EditTemplate(a => { a.Create("create").Read("read").Write("write"); }).Add();
                
              }).Render();
           }
              
{% endhighlight  %}  
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
 {% highlight js %}

     <script id="template" type="text/x-jsrender">
        function create() 
            {
	          return $("<input>");
            }
        function write(args) 
	       {
            args.element.ejMaskEdit({
                  maskFormat : "99-99-9999",
                  value : args.rowdata["ShipPostalCode"]
           });
           }
        function read(args) 
	       {
          return args.ejMaskEdit("get_StrippedValue");
          }
    
    </script>
    
{% endhighlight %}   
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img3.png)


## Edit Modes

### Inline 

Set `EditMode` as `Normal`, then the row itself is changed as edited row.

N> For `EditMode` property you can assign either `string` value (`Normal`) or `enum` value (`Syncfusion.JavaScript.EditMode.Normal`).

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().EditMode(EditMode.Normal); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
                   col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
				   col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).NumericEditOptions(new EditorProperties() { DecimalPlaces = 2 }).Add();
                   col.Field("ShipCountry").HeaderText("Ship Country").EditType(EditingType.Dropdown).Add();
                   col.Field("OrderDate").HeaderText("Order Date").EditType(EditingType.Datepicker).Format("{0:MM/dd/yyyy}").Add();            
               }).Render();
           }     

{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img4.png)


### Inline Form

Set `EditMode` as `InlineForm`, then edit form will be inserted next to the row which is to be edited.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().EditMode(EditMode.InlineForm); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
                   col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
				   col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).NumericEditOptions(new EditorProperties() { DecimalPlaces = 2 }).Add();
                   col.Field("ShipCountry").HeaderText("Ship Country").Add();
                   col.Field("OrderDate").HeaderText("Order Date").EditType(EditingType.Datepicker).Format("{0:MM/dd/yyyy}").Add();            
                }).Render();
            }      

{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                    var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                    ViewBag.DataSource = DataSource;
                    return View();
                 }
             }
        } 
{% endhighlight  %}    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img5.png)


### Inline Template Form

You can edit any of the fields pertaining to a single record of data and apply it to a template so that the same format is applied to all the other records that you may edit later.

Using this template support, you can edit the fields that are not bound to grid columns.

To edit the records using Inline template form, set `EditMode` as `InlineFormTemplate` and specify the template ID to `InlineFormTemplateID` property of `EditSettings`.

While using template form, you can change the HTML elements to appropriate JS controls based on the column type. This can be achieved by using `ActionComplete` event of grid.

N> 1. `value` attribute is used to bind the corresponding field value while editing.
N> 2. `name` attribute is used to get the changed field values while saving the edited record.
N> 3.  It's a standard way to enclose the `Template` within the `script` tag with `type` as "text/x-jsrender".
N> 4.  For `EditMode` property you can assign either `string` value (`InlineFormTemplate`) or `enum` value (`Syncfusion.JavaScript.EditMode.InlineTemplateForm`) 

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .ClientSideEvents(eve => { eve.ActionComplete("complete"); })
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().EditMode(EditMode.InlineFormTemplate).InlineFormTemplateID("#template");})
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
                   col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
                   col.Field("ShipCity").HeaderText("Ship City").EditType(EditingType.Dropdown).Add();
				             
              }).Render();
          }  
 
{% endhighlight  %} 
{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}            
{% highlight js %}			  
    
<script id="template" type="text/template">                             
   <table cellspacing="10">
		<tr>
			<td>Order ID</td>
			<td>
				<input id="OrderID" name="OrderID" disabled="disabled" value="{{"{{"}}:OrderID{{}}}}" class="e-field e-ejinputtext" style="width:116px;height:28px" />
            </td>
			<td>Customer ID</td>
			<td>
				<input id="CustomerID" name="CustomerID" value="{{"{{"}}:CustomerID{{}}}}" class="e-field e-ejinputtext" style="width: 116px; height: 28px" />
			</td>
		</tr>
		<tr>
			<td>Employee ID</td>
			<td>
				<input type="text" id="EmployeeID" name="EmployeeID" value="{{"{{"}}:EmployeeID{{}}}}" />
			</td>
			<td>Ship City</td>
			<td>
				<select id="ShipCity" name="ShipCity">
					<option value="Argentina">Argentina</option>
					<option value="Austria">Austria</option>
					<option value="Belgium">Belgium</option>
					<option value="Brazil">Brazil</option>
					<option value="Canada">Canada</option>
					<option value="Denmark">Denmark</option>
				</select>
			</td>
		</tr>
   </table>
 </script>
	    <script>
              function complete(args) {
	             $("#EmployeeID").ejNumericTextbox();
	             $("#Freight").ejNumericTextbox();
	             $("#ShipCity").ejDropDownList();
              }
        </script>
			  
{% endhighlight  %}    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img6.png)

Before the template elements are converted to JS controls

![](Editing_images/Editing_img7.png)

After the template elements are converted to JS controls using actionComplete event.


### Dialog

Set `EditMode` as `Dialog` to edit data using a dialog box, which displays the fields associated with the data record being edited.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().EditMode(EditMode.Dialog); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
                   col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
				   col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).NumericEditOptions(new EditorProperties() { DecimalPlaces = 2 }).Add();
                   col.Field("ShipCountry").HeaderText("Ship Country").Add();
                   col.Field("OrderDate").HeaderText("Order Date").EditType(EditingType.Datepicker).Format("{0:MM/dd/yyyy}").Add();            
               }).Render();
          }     

{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img8.png)


### Dialog Template Form

You can edit any of the fields pertaining to a single record of data and apply it to a template so that the same format is applied to all the other records that you may edit later.

Using this template support, you can edit the fields that are not bound to grid columns.

To edit the records using Dialog template form, set `EditMode` as 'DialogTemplate' and specify the template id to `DialogEditorTemplateID` property of `EditSettings`.

While using template, you can change the elements that are defined in the `Template`, to appropriate JS controls based on the column type. This can be achieved by using `ActionComplete` event of grid.

N> 1. `value` attribute is used to bind the corresponding field value while editing.
N> 2. `name` attribute is used to get the changed field values while save the edited record. 
N> 3. For `EditMode` property you can assign either `string` value (`DialogTemplate`) or `enum` value (`Syncfusion.JavaScript.EditMode.DialogTemplate`).

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .ClientSideEvents(eve => { eve.ActionComplete("complete"); })
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().EditMode(EditMode.DialogTemplate).DialogEditorTemplateID("#template"); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
                   col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
				   col.Field("ShipCity").HeaderText("Ship City").EditType(EditingType.Dropdown).Add();
                     
               }).Render();
           }  
{% endhighlight  %}
{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}               
{% highlight js %} 		  
    
 <script id="template" type="text/template">
   <table cellspacing="10">
		<tr>
			<td>Order ID</td>
			<td>
				<input id="OrderID" name="OrderID" disabled="disabled" value="{{"{{"}}:OrderID{{}}}}" class="e-field e-ejinputtext" style="width:116px;height:28px" />
            </td>
			<td>Customer ID</td>
			<td>
				<input id="CustomerID" name="CustomerID" value="{{"{{"}}:CustomerID{{}}}}" class="e-field e-ejinputtext" style="width: 116px; height: 28px" />
			</td>
		</tr>
		<tr>
			<td>Employee ID</td>
			<td>
				<input type="text" id="EmployeeID" name="EmployeeID" value="{{"{{"}}:EmployeeID{{}}}}" />
			</td>
			<td>Ship City</td>
			<td>
				<select id="ShipCity" name="ShipCity">
					<option value="Argentina">Argentina</option>
					<option value="Austria">Austria</option>
					<option value="Belgium">Belgium</option>
					<option value="Brazil">Brazil</option>
					<option value="Canada">Canada</option>
					<option value="Denmark">Denmark</option>
				</select>
			</td>
		</tr>
   </table>
 </script>
	    <script>
              function complete(args) {
	             $("#EmployeeID").ejNumericTextbox();
	             $("#Freight").ejNumericTextbox();
	             $("#ShipCity").ejDropDownList();
              }
        </script>
			  
{% endhighlight  %}   
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img9.png)

Before the template elements are converted to JS controls

![](Editing_images/Editing_img10.png)

After the template elements are converted to JS controls using actionComplete event.


### External Form

By setting the `EditMode` as `ExternalForm`, the edit form is opened outside the grid content.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().EditMode(EditMode.ExternalForm); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
                {
                   col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
				   col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).NumericEditOptions(new EditorProperties() { DecimalPlaces = 2 }).Add();
                   col.Field("ShipCountry").HeaderText("Ship Country").Add();
                   col.Field("OrderDate").HeaderText("Order Date").EditType(EditingType.Datepicker).Format("{0:MM/dd/yyyy}").Add();            
                }).Render();
           }      

{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                    var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                    ViewBag.DataSource = DataSource;
                    return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img11.png)


Form Position:

You can position an External edit form in the following two ways. 

1. Top-right
2. Bottom left

This can be achieved by setting the `FormPosition` property of `EditSettings` as 'TopRight' or 'BottomLeft'.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().EditMode(EditMode.ExternalForm).FormPosition(FormPosition.TopRight);  })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
                   col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
				   col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).Add();
                   col.Field("ShipCountry").HeaderText("Ship Country").Add();
                            
             }).Render();
         }      

{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img12.png)


### External Template Form

You can edit any of the fields pertaining to a single record of data and apply it to a template so that the same format is applied to all the other records that you may edit later.

Using this template support, you can edit the fields that are not bound to grid columns.

To edit the records using External template form, set `EditMode` as `ExternalFormTemplate` and specify the template id to `ExternalFormTemplateID` property of `EditSettings`.

While using template, you can change the elements that are defined in the template, to appropriate JS controls based on the column type. This can be achieved by using `ActionComplete` event of grid.

N> 1. `value` attribute is used to bind the corresponding field value while editing. 
N> 2. `name` attribute is used to get the changed field values while save the edited record. 
N> 3. For `EditMode` property you can assign either `string` value (`ExternalFormTemplate`) or `enum` value (`Syncfusion.JavaScript.EditMode.ExternalFormTemplate`).

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .ClientSideEvents(eve => { eve.ActionComplete("complete"); })
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().EditMode(EditMode.ExternalFormTemplate).ExternalFormTemplateID("#template");})
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
                   col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
				   col.Field("ShipCity").HeaderText("Ship City").EditType(EditingType.Dropdown).Add();
              }).Render();
          }  
{% endhighlight  %}
{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
{% highlight js %}              
			  
  <script id="template" type="text/template">
   <table cellspacing="10">
		<tr>
			<td>Order ID</td>
			<td>
				<input id="OrderID" name="OrderID" disabled="disabled" value="{{"{{"}}:OrderID{{}}}}" class="e-field e-ejinputtext" style="width:116px;height:28px" />
            </td>
			<td>Customer ID</td>
			<td>
				<input id="CustomerID" name="CustomerID" value="{{"{{"}}:CustomerID{{}}}}" class="e-field e-ejinputtext" style="width: 116px; height: 28px" />
			</td>
		</tr>
		<tr>
			<td>Employee ID</td>
			<td>
				<input type="text" id="EmployeeID" name="EmployeeID" value="{{"{{"}}:EmployeeID{{}}}}" />
			</td>
			<td>Ship City</td>
			<td>
				<select id="ShipCity" name="ShipCity">
					<option value="Argentina">Argentina</option>
					<option value="Austria">Austria</option>
					<option value="Belgium">Belgium</option>
					<option value="Brazil">Brazil</option>
					<option value="Canada">Canada</option>
					<option value="Denmark">Denmark</option>
				</select>
			</td>
		</tr>
   </table>
 </script>
        <script>
              function complete(args) {
	             $("#EmployeeID").ejNumericTextbox();
	             $("#Freight").ejNumericTextbox();
	             $("#ShipCity").ejDropDownList();
              }
        </script>
			  
{% endhighlight  %}   
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img13.png)

Before the template elements are converted to JS controls

![](Editing_images/Editing_img14.png)

After the template elements are converted to JS controls using actionComplete event.


### Batch / Excel-like

Users can start editing by clicking a cell and typing data into it. Edited cell will be marked while navigating to next cell or any other row, so that you know which fields or cells has been edited. Set `EditMode` as `Batch` to enable batch editing.

N> Refer the KB [link](http://www.syncfusion.com/kb/3016/how-to-suppress-grid-confirmation-messages# "link") for "How to suppress grid confirmation messages" in batch mode.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().EditMode(EditMode.Batch); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
                   col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
				   col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).NumericEditOptions(new EditorProperties() { DecimalPlaces = 2 }).Add();
                   col.Field("ShipCountry").HeaderText("Ship Country").Add();
                   col.Field("OrderDate").HeaderText("Order Date").EditType(EditingType.Datepicker).Format("{0:MM/dd/yyyy}").Add();            
               }).Render();
          }      

{% endhighlight  %}
{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img15.png)


## Confirmation messages

To show the confirm dialog while saving or discarding the Batch changes (discarding during the grid action like filtering, sorting and paging), set `ShowConfirmDialog` as `true`.

N> `ShowConfirmDialog` property is only for Batch editing mode.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().EditMode(EditMode.Batch).ShowConfirmDialog(); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
                   col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
				   col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).NumericEditOptions(new EditorProperties() { DecimalPlaces = 2 }).Add();
                   col.Field("ShipCountry").HeaderText("Ship Country").Add();
                   col.Field("OrderDate").HeaderText("Order Date").EditType(EditingType.Datepicker).Format("{0:MM/dd/yyyy}").Add();            
              }).Render();
          }      

{% endhighlight  %}

{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img16.png)


To show delete confirm dialog while deleting a record, set `ShowDeleteConfirmDialog` as true.

N> `ShowDeleteConfirmDialog` property is for all type of `EditMode`.

The following code example describes the above behavior.


{% tabs %}

{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().ShowDeleteConfirmDialog(); })
            .ToolbarSettings(toolbar =>
               {
                  toolbar.ShowToolbar().ToolbarItems(items =>
                    {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
                   col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Add();
				   col.Field("CustomerID").HeaderText("Customer ID").EditType(EditingType.String).Add();
				   col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).NumericEditOptions(new EditorProperties() { DecimalPlaces = 2 }).Add();
                   col.Field("ShipCountry").HeaderText("Ship Country").Add();
                   col.Field("OrderDate").HeaderText("Order Date").EditType(EditingType.Datepicker).Format("{0:MM/dd/yyyy}").Add();            
             }).Render();
          }      

{% endhighlight  %}

{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img17.png)


## Column Validation

We can validate the value of the added or edited record cell before saving.

The below validation script files are needed when editing is enabled with validation.

1. jquery.validate.min.js
2. jquery.validate.unobtrusive.min.js
 
 
### jQuery Validation


You can set validation rules using ` ValidationRules` property of `Columns`. The following are jQuery validation methods.

__List__ __of__ __Jquery__ __validation__ __methods__

<table>
<tr>
<th>
Rules</th><th>
Description</th></tr>
<tr>
<td>
required</td><td>
Requires an element.</td></tr>
<tr>
<td>
remote</td><td>
Requests a resource to check the element for validity.</td></tr>
<tr>
<td>
minlength</td><td>
Requires the element to be of given minimum length.</td></tr>
<tr>
<td>
maxlength</td><td>
Requires the element to be of given maximum length.</td></tr>
<tr>
<td>
range</td><td>
Requires the element to be in given value range.</td></tr>
<tr>
<td>
min</td><td>
The element requires a given minimum.</td></tr>
<tr>
<td>
max</td><td>
The element requires a given maximum.</td></tr>
<tr>
<td>
email</td><td>
The element requires a valid email.</td></tr>
<tr>
<td>
url</td><td>
The element requires a valid URL</td></tr>
<tr>
<td>
date</td><td>
Requires the element to be a date.</td></tr>
<tr>
<td>
dateISO</td><td>
The element requires an ISO date.</td></tr>
<tr>
<td>
number</td><td>
The element requires a decimal number.</td></tr>
<tr>
<td>
digits</td><td>
The element requires digits only.</td></tr>
<tr>
<td>
creditcard</td><td>
Requires the element to be a credit card number.</td></tr>
<tr>
<td>
equalTo</td><td>
Requires the element to be the same as another.</td></tr>
</table>

Grid supports all the standard validation methods of jQuery, please refer the jQuery validation documentation [link](http://jqueryvalidation.org/documentation/# "link") for more information.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing(); })
            .ToolbarSettings(toolbar =>
               {
                  toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
              {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).ValidationRules(v => v.AddRule("required",true).AddRule("number", true)).Add();
                col.Field("CustomerID").HeaderText("Customer ID").ValidationRules(v => v.AddRule("required", true).AddRule("minlength", 3)).Add();
			    col.Field("ShipCity").HeaderText("Ship City").Add();
                col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).ValidationRules(v => v.AddRule("range", "[0,1000]")).Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
            }).Render();
         }      
{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img18.png)


### Custom Validation

In addition to jQuery validation methods, you can also add your own custom validation methods for a specific column. Function call to custom validator function to be mentioned within `ValidationRules` property of `Columns`. 

Using `messages` property of `ValidationRules` you can specify the error message for that column.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing(); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
              {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).Add();
                col.Field("CustomerID").HeaderText("Customer ID").ValidationRules(v => v.AddRule("customRegex", 5)).Add();
			    col.Field("ShipCity").HeaderText("Ship City").Add();
                col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).ValidationRules(rule => rule.AddRule("customCompare", new List<object>() { 0, 1000 })).Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
              }).Render();
          }    
            
 {% endhighlight  %}          
           
{% highlight js %}           
          
          <script type="text/javascript">
               $(function () {
                  $.validator.addMethod("customCompare", function (value, element, params) {
                  return element.value > params[0] && element.value < params[1];
                }, "Freight value must be between 0 and 1000");

                  $.validator.addMethod("customRegex", function (value, element, params) {
                  if (element.value.length == params)
                  return true;
                  return false;
               }, "Customer ID must be 5 characters");
            });
          </script>
     
{% endhighlight  %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img19.png)


## Adding New Row Position

To add new row in the top or bottom position of grid content, set `RowPosition` property of `EditSettings` depending on the requirement.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().RowPosition(RowPosition.Bottom) })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
              {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
			    col.Field("ShipCity").HeaderText("Ship City").Add();
                col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
             }).Render();
        }  
{% endhighlight %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img26.png)


## Render with blank row for easy add new

The blank add new row is displayed in the grid content during grid initialization itself to add a new record easily. To enable show add new row by default, set `ShowAddNewRow` property of `EditSettings` as `true`.

The blank add new row is displayed either in the top or bottom of the corresponding page, its position is based on the `RowPosition` property of `EditSettings`.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().ShowAddNewRow(); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
              {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
			    col.Field("ShipCity").HeaderText("Ship City").Add();
                col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
              }).Render();
         }  
{% endhighlight %}

{% highlight c# %}

    namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img27.png)

N> 1. If it is remote, then the newly added record is placed based on the index from current view data. 
N> 2. If it is local, then the newly added record is added at the top of the page even if the added new `RowPosition` is mentioned as "Bottom".


## Default column values on add new

While adding new record in grid, there is an option to set the default value for the columns. Using `DefaultValue` property of `Columns` you can set the default values for that particular column while editing or adding a new row.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .EditSettings(edit => { edit.AllowAdding().AllowDeleting().AllowEditing().ShowAddNewRow(); })
            .ToolbarSettings(toolbar =>
               {
                   toolbar.ShowToolbar().ToolbarItems(items =>
                   {
                       items.AddTool(ToolBarItems.Add);
                       items.AddTool(ToolBarItems.Edit);  
                       items.AddTool(ToolBarItems.Delete);
                       items.AddTool(ToolBarItems.Update);
                       items.AddTool(ToolBarItems.Cancel);
                   });
               })
            .Columns(col =>
               {
                 col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).Add();
                 col.Field("CustomerID").HeaderText("Customer ID").Add();
			     col.Field("ShipCity").HeaderText("Ship City").DefaultValue("Bern").Add();
                 col.Field("Freight").HeaderText("Freight").EditType(EditingType.Numeric).DefaultValue(45).Add();
                 col.Field("ShipCountry").HeaderText("Ship Country").DefaultValue("Brazil").Add();
               }).Render();
          }  
{% endhighlight %}

{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
              { 
                public IActionResult GridFeatures()
                 {
                   var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                   ViewBag.DataSource = DataSource;
                   return View();
                 }
             }
        } 
{% endhighlight  %}
    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img28.png)