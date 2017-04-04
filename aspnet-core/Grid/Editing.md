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

The primary key for the data source should be defined in `e-columns` definition, for editing to work properly. In `e-columns` definition, particular primary column's `is-primary-key` property should be set to `true`. Refer the Knowledge base [link](http://www.syncfusion.com/kb/2675/cant-edit-any-row-except-the-first-row-in-grid# "link") for more information.

N> 1. In grid, the primary key column will be automatically set to read only while editing the row, but you can specify primary key column value while adding a new record.
N> 2. The column which is specified as `is-identity` will be in readonly mode both while editing and adding a record. Also, auto incremented value is assigned to that `is-identity` column.

## Toolbar with edit option

Using toolbar which is rendered at the top of the grid header, you can show all the CRUD related action. To enable toolbar and toolbar items, set `show-toolbar` property as true and `toolbar-items`. The default toolbar items are `add`, `edit`, `delete`, `update` and `cancel`.

N> For `toolbar-items` property you can assign either `string` value ("Add") or `enum` value (`Syncfusion.JavaScript.ToolBarItems.Add`).

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID"></e-column>
            <e-column field="CustomerID" header-text="CustomerID"></e-column>
            <e-column field="EmployeeID" header-text="Employee ID"></e-column>
            <e-column field="ShipCity" header-text="Ship City"></e-column>
            <e-column field="ShipCountry" header-text="Ship Country"></e-column>
        </e-columns>
   </ej-grid>
                   
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

The edit type of bound column can be customized using `edit-type` property of `e-columns`. The following Essential JavaScript controls are supported built-in by `edit-type`. You can set the `edit-type` based on specific data type of the column. 

* `NumericTextBox` control for integers, double, and decimal data types.
* `DatePicker` control for date data type.
* `DateTimePicker` control for date-time data type.
* `DropDownList` control for list of data type.

And also you can define the model for all the editTypes controls while editing through EditOptions.

The following table describes `edit-type` and their corresponding EditOptions of the specific data type of the column.

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

N> 1. If `edit-type` is not set, then by default it will display the input element ("string") while editing a column.
N> 2. For `edit-type` property you can assign either `string` value ("Numeric") or `enum` value (`Syncfusion.JavaScript.EditingType.Numeric`).

The following code example describes the above behavior 

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="CustomerID" edit-type="String"></e-column>
            <e-column field="Freight" edit-type="Numeric">
               <e-numeric-edit-options decimal-places="2"></e-numeric-edit-options>  
            </e-column>
            <e-column field="ShipCity" header-text="Ship City" edit-type="Dropdown"></e-column>
            <e-column field="ShipCountry" header-text="Ship Country"></e-column>
            <e-column field="OrderDate" header-text="Order Date" edit-type="Datepicker"format="{0:MM/dd/yyyy}" ></e-column>
            <e-column field="Verified" header-text="Verified" edit-type="Boolean"></e-column>
        </e-columns>
   </ej-grid>
                   
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

On editing the column values, custom editor can be created by using `edit-template` property of `e-columns`. It has three functions, they are

1. `Create` - It is used to create the control at time of initialize.
2. `Read` - It is used to read the input value at time of save.
3. `Write` - It is used to assign the value to control at time of editing.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID"></e-column>
            <e-column field="CustomerID" header-text="CustomerID"></e-column>
            <e-column field="Freight" header-text="Freight"></e-column>
            <e-column field="ShipCountry" header-text="Ship Country"></e-column>
            <e-column field="ShipPostalCode" header-text="Ship Postal Code">
              <e-edit-template create="create" read="read" write="write"> 
              </e-edit-template>
            </e-column>
        </e-columns>
   </ej-grid>
                   
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

Set `edit-mode` as `Normal`, then the row itself is changed as edited row.

N> For `edit-mode` property you can assign either `string` value (`Normal`) or `enum` value (`Syncfusion.JavaScript.EditMode.Normal`).

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" edit-mode="Normal"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric">
               <e-numeric-edit-options decimal-places="2"></e-numeric-edit-options>  
            </e-column>
            <e-column field="ShipCountry" header-text="Ship Country" edit-type="Dropdown"></e-column>
            <e-column field="OrderDate" header-text="Order Date" edit-type="Datepicker" format="{0:MM/dd/yyyy}"></e-column>
        </e-columns>
   </ej-grid>
                   
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

Set `edit-mode` as `InlineForm`, then edit form will be inserted next to the row which is to be edited.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" edit-mode="InlineForm"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric">
               <e-numeric-edit-options decimal-places="2"></e-numeric-edit-options>  
            </e-column>
            <e-column field="ShipCountry" header-text="Ship Country" edit-type="Dropdown"></e-column>
            <e-column field="OrderDate" header-text="Order Date" edit-type="Datepicker" format="{0:MM/dd/yyyy}"></e-column>
        </e-columns>
   </ej-grid>
                   
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

To edit the records using Inline template form, set `edit-mode` as `InlineFormTemplate` and specify the template ID to `inline-form-template-id` property of `e-edit-settings`.

While using template form, you can change the HTML elements to appropriate JS controls based on the column type. This can be achieved by using `action-complete` event of grid.

N> 1. `value` attribute is used to bind the corresponding field value while editing.
N> 2. `name` attribute is used to get the changed field values while saving the edited record.
N> 3.  It's a standard way to enclose the `Template` within the `script` tag with `type` as "text/x-jsrender".
N> 4.  For `edit-mode` property you can assign either `string` value (`InlineFormTemplate`) or `enum` value (`Syncfusion.JavaScript.EditMode.InlineTemplateForm`) 

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" edit-mode="InlineFormTemplate" inline-form-template-id="#template" action-complete="complete"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String"></e-column>
            <e-column field="ShipCity" header-text="Ship City" edit-type="Dropdown"></e-column>
        </e-columns>
   </ej-grid>
                   
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
			  
{% endhighlight %}    
{% endtabs %} 

 The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img6.png)

Before the template elements are converted to JS controls

![](Editing_images/Editing_img7.png)

After the template elements are converted to JS controls using action-complete event.

### Dialog

Set `edit-mode` as `Dialog` to edit data using a dialog box, which displays the fields associated with the data record being edited.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" edit-mode="Dialog"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric">
               <e-numeric-edit-options decimal-places="2"></e-numeric-edit-options>  
            </e-column>
            <e-column field="ShipCountry" header-text="Ship Country" edit-type="Dropdown"></e-column>
            <e-column field="OrderDate" header-text="Order Date" edit-type="Datepicker" format="{0:MM/dd/yyyy}"></e-column>
        </e-columns>
   </ej-grid>
                   
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

To edit the records using Dialog template form, set `edit-mode` as 'DialogTemplate' and specify the template id to `dialog-editor-template-id` property of `e-edit-settings`.

While using template, you can change the elements that are defined in the `template`, to appropriate JS controls based on the column type. This can be achieved by using `action-complete` event of grid.

N> 1. `value` attribute is used to bind the corresponding field value while editing.
N> 2. `name` attribute is used to get the changed field values while save the edited record. 
N> 3. For `edit-mode` property you can assign either `string` value (`DialogTemplate`) or `enum` value (`Syncfusion.JavaScript.EditMode.DialogTemplate`).

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" edit-mode="DialogTemplate" dialog-editor-template-id="#template" action-complete="complete"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String"></e-column>
            <e-column field="ShipCity" header-text="Ship City" edit-type="Dropdown"></e-column>
        </e-columns>
   </ej-grid>
                   
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
			  
{% endhighlight %}    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img9.png)

Before the template elements are converted to JS controls

![](Editing_images/Editing_img10.png)

After the template elements are converted to JS controls using actionComplete event.

### External Form

By setting the `edit-mode` as `ExternalForm`, the edit form is opened outside the grid content.

The following code example describes the above behavior.
 
{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" edit-mode="ExternalForm"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric">
               <e-numeric-edit-options decimal-places="2"></e-numeric-edit-options>  
            </e-column>
            <e-column field="ShipCountry" header-text="Ship Country" edit-type="Dropdown"></e-column>
            <e-column field="OrderDate" header-text="Order Date" edit-type="Datepicker" format="{0:MM/dd/yyyy}"></e-column>
        </e-columns>
   </ej-grid>
                   
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

This can be achieved by setting the `form-position` property of `e-edit-settings` as 'TopRight' or 'BottomLeft'.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" edit-mode="ExternalForm" form-position="TopRight"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric"></e-column>
            <e-column field="ShipCountry" header-text="Ship Country"></e-column>
        </e-columns>
   </ej-grid>
                   
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

To edit the records using External template form, set `edit-mode` as `ExternalFormTemplate` and specify the template id to `external-form-template-id` property of `e-edit-settings`.

While using template, you can change the elements that are defined in the template, to appropriate JS controls based on the column type. This can be achieved by using `action-complete` event of grid.

N> 1. `value` attribute is used to bind the corresponding field value while editing. 
N> 2. `name` attribute is used to get the changed field values while save the edited record. 
N> 3. For `edit-mode` property you can assign either `string` value (`ExternalFormTemplate`) or `enum` value (`Syncfusion.JavaScript.EditMode.ExternalFormTemplate`).

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" edit-mode="ExternalFormTemplate" external-form-template-id="#template" action-complete="complete"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String"></e-column>
            <e-column field="ShipCity" header-text="Ship City" edit-type="Dropdown"></e-column>
        </e-columns>
   </ej-grid>
                   
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
			  
{% endhighlight %}    
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img13.png)

Before the template elements are converted to JS controls

![](Editing_images/Editing_img14.png)

After the template elements are converted to JS controls using actionComplete event.


### Batch / Excel-like

Users can start editing by clicking a cell and typing data into it. Edited cell will be marked while navigating to next cell or any other row, so that you know which fields or cells has been edited. Set `edit-mode` as `Batch` to enable batch editing.

N> Refer the KB [link](http://www.syncfusion.com/kb/3016/how-to-suppress-grid-confirmation-messages# "link") for "How to suppress grid confirmation messages" in batch mode.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" edit-mode="Batch"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric">
               <e-numeric-edit-options decimal-places="2"></e-numeric-edit-options>  
            </e-column>
            <e-column field="ShipCountry" header-text="Ship Country" edit-type="Dropdown"></e-column>
            <e-column field="OrderDate" header-text="Order Date" edit-type="Datepicker" format="{0:MM/dd/yyyy}"></e-column>
        </e-columns>
   </ej-grid>
                   
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

To show the confirm dialog while saving or discarding the Batch changes (discarding during the grid action like filtering, sorting and paging), set `show-confirm-dialog` as `true`.

N> `show-confirm-dialog` property is only for Batch editing mode.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" edit-mode="Batch" show-confirm-dialog="true"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric">
               <e-numeric-edit-options decimal-places="2"></e-numeric-edit-options>  
            </e-column>
            <e-column field="ShipCountry" header-text="Ship Country" edit-type="Dropdown"></e-column>
            <e-column field="OrderDate" header-text="Order Date" edit-type="Datepicker" format="{0:MM/dd/yyyy}"></e-column>
        </e-columns>
   </ej-grid>
                   
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

To show delete confirm dialog while deleting a record, set `show-delete-confirm-dialog` as true.

N> `show-delete-confirm-dialog` property is for all type of `edit-mode`.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" edit-mode="Batch" show-delete-confirm-dialog="true"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric">
               <e-numeric-edit-options decimal-places="2"></e-numeric-edit-options>  
            </e-column>
            <e-column field="ShipCountry" header-text="Ship Country" edit-type="Dropdown"></e-column>
            <e-column field="OrderDate" header-text="Order Date" edit-type="Datepicker" format="{0:MM/dd/yyyy}"></e-column>
        </e-columns>
   </ej-grid>
                   
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


You can set validation rules using `validation-rules` property of `e-columns`. The following are jQuery validation methods.

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

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID" validation-rules='@(new Dictionary<string,object> { {"required",true}, {"number",true} })' text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String" validation-rules='@(new Dictionary<string,object> { {"required",true}, {"minlength",3} })'></e-column>
            <e-column field="ShipCity" header-text="Ship City"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric" validation-rules='@(new Dictionary<string,object> { {"required",true}, {"range","[0,1000]"} })' ></e-column>
            <e-column field="ShipCountry" header-text="Ship Country"></e-column>
       </e-columns>
   </ej-grid>
                   
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

In addition to jQuery validation methods, you can also add your own custom validation methods for a specific column. Function call to custom validator function to be mentioned within `validation-rules` property of `e-columns`. 

Using `messages` property of `validation-rules` you can specify the error message for that column.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID"  text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" edit-type="String" validation-rules='@(new Dictionary<string,object> {{"customRegex",5}})'></e-column>
            <e-column field="ShipCountry" header-text="Ship City"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric" validation-rules='@(new Dictionary<string,object> {{"customCompare",new List <Object>() {0,1000}} })' ></e-column>
            <e-column field="ShipCountry" header-text="Ship Country"></e-column>
       </e-columns>
   </ej-grid>
                   
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
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Editing_images/Editing_img19.png)


## Adding New Row Position

To add new row in the top or bottom position of grid content, set `row-position` property of `e-edit-settings` depending on the requirement.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" row-position="Bottom"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID"></e-column>
            <e-column field="CustomerID" header-text="Customer ID"></e-column>
            <e-column field="ShipCity" header-text="Ship City"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric"></e-column>
            <e-column field="ShipCountry" header-text="Ship Country"></e-column>
       </e-columns>
   </ej-grid>
                   
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

![](Editing_images/Editing_img26.png)


## Render with blank row for easy add new

The blank add new row is displayed in the grid content during grid initialization itself to add a new record easily. To enable show add new row by default, set `show-add-new-row` property of `e-edit-settings` as `true`.

The blank add new row is displayed either in the top or bottom of the corresponding page, its position is based on the `row-position` property of `e-edit-settings`.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" show-add-new-row="true"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID"></e-column>
            <e-column field="CustomerID" header-text="Customer ID"></e-column>
            <e-column field="ShipCity" header-text="Ship City"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric"></e-column>
            <e-column field="ShipCountry" header-text="Ship Country"></e-column>
       </e-columns>
   </ej-grid>
                   
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

![](Editing_images/Editing_img27.png)

N> 1. If it is remote, then the newly added record is placed based on the index from current view data. 
N> 2. If it is local, then the newly added record is added at the top of the page even if the added new `row-position` is mentioned as "Bottom".


## Default column values on add new

While adding new record in grid, there is an option to set the default value for the columns. Using `default-value` property of `e-columns` you can set the default values for that particular column while editing or adding a new row.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true" show-add-new-row="true"></e-edit-settings>
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}'/>
        <e-columns>
            <e-column field="OrderID" is-primary-key="true" header-text="Order ID"></e-column>
            <e-column field="CustomerID" header-text="Customer ID"></e-column>
            <e-column field="ShipCity" header-text="Ship City" default-value="Bern"></e-column>
            <e-column field="Freight" header-text="Freight" edit-type="Numeric" default-value="45"></e-column>
            <e-column field="ShipCountry" header-text="Ship Country" default-value="Brazil"></e-column>
       </e-columns>
   </ej-grid>
                   
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

![](Editing_images/Editing_img28.png)