---
layout: post
title: Grouping with Grid widget for Syncfusion Essential ASP.NET Core
description: How to enable grouping and its functionalities
platform: ASP.NET Core
control: Grid
documentation: ug
---
# Grouping

The Grid control has options to group the records based on the required column. When grouping is applied, grouped records are organized into a hierarchical structure to facilitate easier expand and collapse of records. To enable grouping, set `AllowGrouping` property as `true`.

Columns can be grouped by simply dragging the column header and drop on the group drop area or simply click the group button which is displayed in the column. By default, sorting is done while grouping the column.

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

     @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
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

![](Grouping_images/Grouping_img1.png)


## Initial Grouping

While initializing the grid itself, there is an option to group the column and display it in a hierarchical structure. To enable initial grouping, set array of column's `Field` name to be grouped in `GroupedColumns` property  of `GroupSettings`.

The following code example describes the above behavior.
            
{% tabs %}
 
{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.GroupedColumns(col => { col.Add("ShipCountry"); }); })
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

![](Grouping_images/Grouping_img2.png)


## Multi-Column Grouping

Group multiple columns by simply drag and drop the columns one by one from column header into group drop area.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.GroupedColumns(col => { col.Add("ShipCountry"); col.Add("CustomerID"); }); })
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

![](Grouping_images/Grouping_img3.png)


## Group Buttons

To do grouping easily without doing drag and drop column header by setting `ShowToggleButton` property of `GroupSettings` as `true`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.ShowToggleButton(true); })
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

![](Grouping_images/Grouping_img4.png)


## Hide Ungroup Button

Hide ungroup button from grouped columns which is in the group drop area by setting the `ShowUngroupButton` property of `GroupSettings` as `false`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.ShowUngroupButton(false); })
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

![](Grouping_images/Grouping_img5.png)


## Hide Grouped Column

While grouping a particular column, there is an option to hide the grouped columns from grid. To enable hide grouped column option, set `ShowGroupedColumn` property of `GroupSettings` as `false`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.ShowGroupedColumn(false); })
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

![](Grouping_images/Grouping_img6.png)


## AutoSize Drop Area

Drag any column header and move it to the group drop area, then its portion expands smoothly. Stop this animation by setting `EnableDropAreaAutoSizing` property of `GroupSettings` as `false`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.EnableDropAreaAutoSizing(false); })
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

![](Grouping_images/Grouping_img7.png)


## Hide Drop Area 

To avoid ungrouping or further grouping of a column after an initial column grouping by setting `ShowDropArea` property of `GroupSettings` as `false`.

The following code example describes the above behavior.

{% tabs %}
 
{% highlight razor %}

    @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowGrouping()
            .GroupSettings(group => { group.ShowDropArea(false).GroupedColumns(col => { col.Add("ShipCountry"); }); })
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

![](Grouping_images/Grouping_img8.png)