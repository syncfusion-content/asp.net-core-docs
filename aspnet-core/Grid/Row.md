---
layout: post
title: Row with Grid widget for Syncfusion Essential ASP.NET Core
description: How to use and customize the grid row
platform: ASP.NET Core
control: Grid
documentation: ug
---
# Row
It represents the record details that are fetched from the datasource.

## Row Hover
You can see the mouse hovering effect on the corresponding grid rows using `EnableRowHover` property. By default its value is `true`.
The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

     @{Html.EJ().Grid<OrdersView>("FlatGrid")
         .Datasource((IEnumerable<object>)ViewBag.datasource)
         .AllowPaging()   
         .EnableRowHover(true)        
         .Columns(col =>
          {
             col.Field("OrderID").Add();
             col.Field("EmployeeID").Add();
             col.Field("ShipCity").Add();
             col.Field("ShipCountry").Add();
             col.Field("Freight").Add();
        }).Render();
      }
{% endhighlight %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
       public class GridController : Controller
        {
         public IActionResult Default()
          {
            var DataSource = new NorthwindDataContext().OrdersViews.ToList();
            ViewBag.datasource = DataSource;
            return View();
           }
        }
      }
{% endhighlight  %}
{% endtabs %} 
The following output is displayed as a result of the above code example.

![](Row_images/Row_img1.png)

## Alternate row styling

Alternate row styling enhances the readability of grid rows by setting different background color for every alternate row. You can enable the alternative row styling in grid by using `EnableAltRow` property. 

By default its value is `true`, so the following code example describes the how to turn off alternate row behavior.

{% tabs %}
{% highlight  razor %}

   @{Html.EJ().Grid<OrdersView>("Grid")
         .Datasource((IEnumerable<object>)ViewBag.datasource)
         .AllowPaging()
         .EnableAltRow(false)
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
           public IActionResult Default()
            {
               var DataSource = new NorthwindDataContext().OrdersViews.ToList();
               ViewBag.datasource = DataSource;
               return View();
            }
        }
     }
{% endhighlight  %}
{% endtabs %} 
The following output is displayed as a result of the above code example.

![](Row_images/Row_img4.png)


