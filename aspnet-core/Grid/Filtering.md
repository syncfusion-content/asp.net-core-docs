---
layout: post
title: Filtering with Grid widget for Syncfusion Essential ASP.NET Core
description: How to enable filtering and its functionalities
platform: ASP.NET Core
control: Grid
documentation: ug
---
# Filtering

Filtering helps to view particular or related records from dataSource which meets a given filtering criteria. To enable filter, set `AllowFiltering`property as`true`.   

The Grid supports three types of filter, they are

1. Filter Bar
2. Menu 
3. Excel

And also four types of filter menu is available in all filter types, they are

1. String 
2. Numeric 
3. Date 
4. Boolean

The corresponding filter menu is opened based on the column type.

N>  1. Need to specify the `Type` of column, when first record data value is empty or null otherwise the filter menu is not opened. 
N>  2. The default filter type is Filter bar, when `AllowFiltering` is enabled and `FilterType` is not set.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowFiltering()
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
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

![](filtering_images/filtering_img1.png)


## Menu Filter

You can enable menu filter by setting `FilterType` as `Menu` in `FilterSettings`

There is an option to show or hide the additional filter options in the Menu by setting `ShowPredicate` as `true` or `false` in `FilterSettings` respectively.

N> For `FilterType` property you can assign either `string` value ("Menu") or `enum` value (`Syncfusion.JavaScript.FilterType.Menu`).

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowFiltering()
            .FilterSettings(filter => { filter.FilterType(FilterType.Menu); })
            .Columns(col =>
              {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
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

![](filtering_images/filtering_img2.png)

Numeric Filter

![](filtering_images/filtering_img3.png)

String Filter

![](filtering_images/filtering_img4.png)

Date Filter

![](filtering_images/filtering_img5.png)

Boolean Filter


## Excel-like filter

You can enable excel menu by setting  `FilterType` as` Excel` in `FilterSettings` . The excel menu contains an option such as Sorting, Clear filter, submenu for advanced filtering.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowFiltering()
            .FilterSettings(filter => { filter.FilterType(FilterType.Excel); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
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

![](filtering_images/filtering_img6.png)

### Filtering Between Values

By using the custom filter feature of the Excel filter, we can filter between values of the column. The following screenshot depicts the usage of "Between" option of the custom filter dialog.

{% include image.html url="filtering_images/filterbetween_img1.png" caption="Selecting between filter option from Excel filter dialog"%}

{% include image.html url="filtering_images/filterbetween_img2.png" caption="Filtering column for between values"%}

Checkbox list generation:

By default, the checkbox list is generated from distinct values of the filter column from dataSource which gives an option to search and select the required items.

Also on checkbox list generation, if the number of distinct values are greater than 1000, then the excel filter will display only first 1000 values to ensure the best performance on rendering and searching. However this limit has been customized according to your requirement by setting `MaxFilterChoices` with required limit in integer.

N> 1. Using excel filter events you can change the dataSource of the checkbox list. 
N> 2. `Query` of checkbox list can also be changed using excel filter events.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowFiltering()
            .FilterSettings(filter => { filter.FilterType(FilterType.Excel).MaxFilterChoices(4); })
            .Columns(col =>
             {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
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

![](filtering_images/filtering_img7.png)


### Case Sensitivity

To perform filter operation with case sensitive in excel styled filter menu mode by setting `EnableCaseSensitivity` as `true`.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowFiltering()
            .FilterSettings(filter => { filter.FilterType(FilterType.Excel).EnableCaseSensitivity(true);  })
            .Columns(col =>
             {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
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

![](filtering_images/filtering_img8.png)


## Filter Bar

`Filter bar` row is located next to column header of grid. You can filter the records with different expressions depending upon the column type. To show the filter bar row, set the `FilterType` as `FilterBar`.

List of Filter bar Expressions:

You can enter the below filter expressions manually in the filter bar.

 <table>
        <tr>
            <th>
                Expression
            </th>
            <th>
                Example
            </th>
            <th>
                Description
            </th>
            <th>
                Column Type
            </th>
        </tr>
        <tr>
            <td>
                =
            </td>
            <td>
                = value
            </td>
            <td>
                Equal
            </td>
            <td rowspan="5">
                Numeric
            </td>
        </tr>
        <tr>
            <td>
                != 
            </td>
            <td>
                != value
            </td>
            <td>
                NotEqual
            </td>
           
        </tr>
        <tr>
            <td>
                >
            </td>
            <td>
                > value
            </td>
            <td>
                GreaterThan
            </td>
          
        </tr>
        <tr>
            <td>
                <
            </td>
            <td>
                < value
            </td>
            <td>
                LessThan
            </td>
          
        </tr>
        <tr>
            <td>
                >=
            </td>
            <td>
                >= value
            </td>
            <td>
                GreaterThanOrEqual
            </td>
           
        </tr>
        <tr>
            <td>
                <=
            </td>
            <td>
                <= value
            </td>
            <td>
                LessThanOrEqual
            </td>
           
        </tr>
        <tr>
            <td>
                N/A
            </td>
            <td>
                N/A
            </td>
            <td>
                Always `StartsWith` operator will be used for string filter
            </td>
            <td>
                String
            </td>
        </tr>
        <tr>
            <td>
                N/A
            </td>
            <td>
                N/A
            </td>
            <td>
                Always `Equal` operator will be used for Date filter 
            </td>
            <td>
                Date
            </td>
        </tr>
        <tr>
            <td>
                N/A
            </td>
            <td>
                N/A
            </td>
            <td>
                Always `Equal` operator will be used for Boolean filter
            </td>
            <td>
                Boolean
            </td>
        </tr>
    </table>
	
	
The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowFiltering()
            .FilterSettings(filter => { filter.FilterType(FilterType.FilterBar); })
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
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

![](filtering_images/filtering_img9.png)


Filter bar modes:

This specifies the grid to start the filter action while typing in the filter bar or after pressing the enter key based on `FilterBarMode`.There are two types of `FilterBarMode`, they are

1. OnEnter
2. Immediate

N> For `FilterBarMode` property you can assign either `string` value (OnEnter) or `enum` value (`Syncfusion.JavaScript.FilterBarMode.OnEnter`).

Filter bar message:

The filter bar message is supported only for the `FilterType` as 'FilterBar'. The filtered data with column name is displayed in the grid pager itself. By default `ShowFilterBarStatus` is 'true'.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowFiltering()
            .FilterSettings(filter => { filter.ShowFilterBarStatus(true); })
            .Columns(col =>
             {
                col.Field("OrderID").HeaderText("Order ID").Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Add();
                col.Field("CustomerID").HeaderText("Customer ID").Add();
                col.Field("ShipCountry").HeaderText("Ship Country").Add();
                col.Field("Freight").HeaderText("Freight").Add();
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

![](filtering_images/filtering_img10.png)


## Filter Operators

The grid controls uses filter operators from `DataManager`, which are used at the time of filtering.

List of Column type and Filter operators

<table>
        <tr>
            <th>
                Column Type
            </th>
            <th>
                Filter Operators
            </th>
        </tr>
        <tr>
            <td rowspan="6">
                Number
            </td>
            <td>
                FilterOperatorType.GreaterThan
            </td>
        </tr>
        <tr>
           
            <td>
                FilterOperatorType.GreaterThanOrEqual
            </td>
        </tr>
        <tr>
       
            <td>
                FilterOperatorType.LessThan
            </td>
        </tr>
        <tr>
            
            <td>
                FilterOperatorType.LessThanOrEqual
            </td>
        </tr>
        <tr>
           
            <td>
                FilterOperatorType.Equal
            </td>
        </tr>
        <tr>
          
            <td>
                FilterOperatorType.NotEqual
            </td>
        </tr>
        <tr>
            <td rowspan="5">
                String
            </td>
            <td>
                FilterOperatorType.StartsWith
            </td>
        </tr>
        <tr>
          
            <td>
                FilterOperatorType.EndsWith
            </td>
        </tr>
        <tr>
           
            <td>
                FilterOperatorType.Contains
            </td>
        </tr>
        <tr>
           
            <td>
                FilterOperatorType.Equal
            </td>
        </tr>
        <tr>
           
            <td>
                FilterOperatorType.NotEqual
            </td>
        </tr>
        <tr>
            <td rowspan="2">
                Boolean
            </td>
            <td>
                FilterOperatorType.Equal
            </td>
        </tr>
        <tr>
            
            <td>
                FilterOperatorType.NotEqual
            </td>
        </tr>
        <tr>
            <td rowspan="6">
                Date
            </td>
            <td>
                FilterOperatorType.GreaterThan
            </td>
        </tr>
        <tr>
            
            <td>
                FilterOperatorType.GreaterThanOrEqual
            </td>
        </tr>
        <tr>
           
            <td>
                FilterOperatorType.LessThan
            </td>
        </tr>
        <tr>
           
            <td>
                FilterOperatorType.LessThanOrEqual
            </td>
        </tr>
        <tr>
           
            <td>
                FilterOperatorType.Equal
            </td>
        </tr>
        <tr>
          
            <td>
                FilterOperatorType.NotEqual
            </td>
        </tr>
    </table>

