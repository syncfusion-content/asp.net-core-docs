---
layout: post
title: Sorting with Grid widget for Syncfusion Essential ASP.NET Core
description: How to enable sorting and its functionalities
platform: ASP.NET Core
control: Grid
documentation: ug
---
# Sorting

The Grid control has support to sort data bound columns in ascending or descending order. This can be achieved by setting `AllowSorting` property as `true`. 

To dynamically sort a particular column, click on its column header. The order switch between ascending and descending each time you click a column header for sorting.

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

     @{Html.EJ().Grid<object>("Grid")
        .Datasource((IEnumerable<object>)ViewBag.datasource)
        .AllowPaging()
        .AllowSorting()
        .Columns(col =>
           {
              col.Field("OrderID").Add();
              col.Field("EmployeeID").Add();
              col.Field("ShipCity").Add();
              col.Field("ShipCountry").Add();
              col.Field("Freight").Add();
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
                   var DataSource = OrderRepository.GetAllRecords();
                   ViewBag.datasource = DataSource;
                   return View();
                 }
            }
       }
{% endhighlight  %}
{% endtabs %} 
The following output is displayed as a result of the above code example.

![](Sorting_images/Sorting_img1.png)

## Initial Sorting

Through `SortedColumns` property of `SortSettings`, you can sort the columns while initializing the grid itself. You need to specify the `Field` (Columns) name and `Direction` in the `SortedColumns`.

N> 1. For `Direction` property you can assign either `string` value ("Descending") or `enum` value (`SortOrder.Descending`). 
N> 2. You can add multiple columns in `SortedColumns` for multi column sorting while initializing the grid itself.

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

     @{Html.EJ().Grid<object>("Grid")
         .Datasource((IEnumerable<object>)ViewBag.datasource)
         .AllowPaging()
         .AllowSorting()
         .SortSettings(sort => sort.SortedColumns(col => col.Field("EmployeeID").Direction(SortOrder.Descending).Add()))
         .Columns(col =>
             {
               col.Field("OrderID").Add();
               col.Field("EmployeeID").Add();
               col.Field("CustomerID").Add();
               col.Field("ShipCountry").Add();
               col.Field("Freight").Add();
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
                var DataSource = OrderRepository.GetAllRecords();
                 ViewBag.datasource = DataSource;
                 return View();
                }
           }
        }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Sorting_images/Sorting_img2.png)

## Multi-Column Sorting

Sort multiple columns in grid by setting `AllowMultiSorting` property as true. The sorting order is displayed in the header while doing multi sorting.

You can sort more than one column by pressing "Ctrl key + mouse left click" on the column header. To clear sorting for particular column, press "Shift + mouse left click". 

N> `AllowSorting` must be true while enabling multi sort.

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

     @{Html.EJ().Grid<object>("Grid")
         .Datasource((IEnumerable<object>)ViewBag.datasource)
         .AllowPaging()
         .AllowSorting()
         .AllowMultiSorting()
         .SortSettings(sort =>
            {
             sort.SortedColumns(col => col.Field("EmployeeID").Direction(SortOrder.Descending).Add());
             sort.SortedColumns(col => col.Field("CustomerID").Add());
             })
         .Columns(col =>
                {
                   col.Field("OrderID").Add();
                   col.Field("EmployeeID").Add();
                   col.Field("CustomerID").Add();
                   col.Field("ShipCountry").Add();
                   col.Field("Freight").Add();
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
               var DataSource = OrderRepository.GetAllRecords();
               ViewBag.datasource = DataSource;
               return View();
             }
         }
      }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Sorting_images/Sorting_img3.png)

## Stable sorting

For sorting, grid uses default browser's sort function for better performance. On multi column sorting in some browsers like chrome, the records order will be different due to unstable implementation of sorting algorithm in it. 

To resolve this, you need to set `ej.support.stableSort` as `false`.

This will tell the "DataManager" to use custom sort function for sorting data. 

Please refer the [link](https://en.wikipedia.org/wiki/Category:Stable_sorts# "link"), to know more information about stable sort.

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

     @{Html.EJ().Grid<object>("Grid")
         .Datasource((IEnumerable<object>)ViewBag.datasource)
         .AllowPaging()
         .AllowSorting()
         .AllowMultiSorting()
         .Columns(col =>
               {
                   col.Field("OrderID").Add();
                   col.Field("EmployeeID").Add();
                   col.Field("ShipCity").Add();
                   col.Field("ShipCountry").Add();
                   col.Field("Freight").Add();
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
               var DataSource = OrderRepository.GetAllRecords();
               ViewBag.datasource = DataSource;
                return View();
              }
           }
      }
{% endhighlight  %}
{% highlight js %} 
      <script type="text/javascript">
            ej.support.stableSort = true
       </script>
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Sorting_images/Sorting_img4.png)

## Touch options

While using Grid in a touch device, you have an option for multi sorting in single tap on the grid header. By tapping on the grid header, it will show the toggle button in small popup with sort icon. Now tap the button to enable multi sorting in single tap.

Again if you tap the popup symbol, then the single tap multi sorting will be disabled. 

N> `AllowMultiSorting` and `AllowSorting` should be `true` then only the popup will be shown.

The following code example describes the above behavior.
{% tabs %}
{% highlight  razor %}

     @{Html.EJ().Grid<object>("Grid")
         .Datasource((IEnumerable<object>)ViewBag.datasource)
         .AllowPaging()
         .AllowMultiSorting()
         .AllowSorting()
         .Columns(col =>
             {
                 col.Field("OrderID").Add();
                 col.Field("EmployeeID").Add();
                 col.Field("CustomerID").Add();
                 col.Field("ShipCountry").Add();
                 col.Field("Freight").Add();
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
                   var DataSource = OrderRepository.GetAllRecords();
                   ViewBag.datasource = DataSource;
                   return View();
                 }
           }
       }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Sorting_images/Sorting_img5.png)


