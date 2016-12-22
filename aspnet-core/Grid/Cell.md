---
layout: post
title: Cell with Grid widget for Syncfusion Essential ASP.NET Core
description: How to use and customize the grid cells
platform: ASP.NET Core
control: Grid
documentation: ug
---

# Cell

## Auto wrap 

Auto wrap enables the Grid to wrap cell content or header content to next line when the content exceeds the boundary of the cell width. To enable auto wrap, set `AllowTextWrap` property as `true`. 

We can specify the mode of auto wrap using `WrapMode` property of the `TextWrapSettings`. 

Three types of `WrapMode` are available and they are,
  
 1. Both
 2. Header
 3. Content 
 
N> 1. By default the `WrapMode` will be set as `Both`. 
N> 2. While using `TextWrapSettings` then it is must to set `AllowTextWrap` as `true`.
N> 3. For `WrapMode` property you can assign `enum` value (`Syncfusion.JavaScript.WrapMode.Both`).
 
## Both

When `WrapMode` of `TextWrapSettings` property set as `Both` then the auto wrap will be enable for both grid content and header. 

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

        @{Html.EJ().Grid<Object>("FlatGrid")
                .Datasource((IEnumerable<object>)ViewBag.DataSource)
                .AllowPaging()
                .AllowTextWrap()
                .TextWrapSettings(wrap => { wrap.WrapMode(WrapMode.Both); })
                .Columns(col =>
                {
                    col.Field("OrderID").Width(100).Add();
                    col.Field("EmployeeID").Width(100).Add();
                    col.Field("Freight").Width(100).Add();
                    col.Field("ShipCity").Width(150).Add();
                    col.Field("ShipAddress").HeaderText("Ship Address").Width(100).Add();
                }).Render();
        }

{% endhighlight  %}
{% highlight c# %}

        namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
            {
                public IActionResult Index()
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

![](Cell_images/Cell_img1.png)

### Header

When `WrapMode` of `TextWrapSettings` property set as `Header` then the auto wrap will be enable only for grid header alone. 

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

        @{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .AllowTextWrap()
            .TextWrapSettings(wrap => { wrap.WrapMode(WrapMode.Header); })
            .Columns(col =>
            {
                col.Field("OrderID").Width(100).Add();
                col.Field("EmployeeID").Width(100).Add();
                col.Field("Freight").Width(100).Add();
                col.Field("ShipCity").Width(150).Add();
                col.Field("ShipAddress").HeaderText("Ship Address").Width(100).Add();
            }).Render();
        }

{% endhighlight  %}
{% highlight c# %}

        namespace MVCSampleBrowser.Controllers
        {
            public class GridController : Controller
            {
                public IActionResult Index()
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

![](Cell_images/Cell_img1_1.png)

### Content

When `WrapMode` of `TextWrapSettings` property set as `Content` then the auto wrap will be enable only for grid content alone. 

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

        @{Html.EJ().Grid<Object>("FlatGrid")
                    .Datasource((IEnumerable<object>)ViewBag.DataSource)
                    .AllowPaging()
                    .AllowTextWrap()
                    .TextWrapSettings(wrap => { wrap.WrapMode(WrapMode.Header); })
                    .Columns(col =>
                    {
                        col.Field("OrderID").Width(100).Add();
                        col.Field("EmployeeID").Width(100).Add();
                        col.Field("Freight").Width(100).Add();
                        col.Field("ShipCity").Width(150).Add();
                        col.Field("ShipAddress").HeaderText("Ship Address").Width(100).Add();
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

![](Cell_images/Cell_img1_2.png)

## Cell Merging

The grid has options to merge the grid cells based on the required conditions. This can be enabled by setting `AllowCellMerging` property as `true` and the merge conditions can be defined in `MergeCellInfo` event. In this event, you can get the column details and data of that particular row and column which is helpful in defining conditions. 

You can merge the rows and cells of grid, using `rowMerge`, `colMerge` and `merge` functions available in `MergeCellInfo` event's argument.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

        @{Html.EJ().Grid<Object>("FlatGrid")
                    .Datasource((IEnumerable<object>)ViewBag.DataSource)
                    .AllowPaging()
                    .AllowCellMerging()
                    .ClientSideEvents(eve => { eve.MergeCellInfo("mergeCellInfo"); })
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
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.DataSource = DataSource;
                return View();
               }
            }
          }
{% endhighlight  %}
{% highlight c# %}

     <script type="text/javascript">         
        function mergeCellInfo(args)
         {
            if (args.column.field == "EmployeeID" && args.data.OrderID == 10248)
                args.rowMerge(3);
            else if (args.column.field == "ShipCity" && args.data.OrderID == 10252)
                args.colMerge(3);
            else if (args.column.field == "ShipCity" && args.data.OrderID == 10255)
                args.merge(0, 3);
         }
    </script>
{% endhighlight  %}
{% endtabs %}  

The following output is displayed as a result of the above code example.

![](Cell_images/Cell_img2.png)


## Custom Attribute

You can add custom attribute for particular column `td` element by using `CustomAttributes` property of the column.

Based on custom attribute you can customize the style and appearance of the `td` element or handling jQuery functionalities. 

You can use JsRender syntax in the template.For more information about JsRender syntax, please refer [the link](http://www.jsviews.com/#jsrapi "the link").

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

@{Html.EJ().Grid<Object>("FlatGrid")
        .Datasource((IEnumerable<object>)ViewBag.DataSource)
        .AllowPaging()
        .Columns(col =>
        {
            col.Field("OrderID").Add();
            col.Field("CustomerID").Add();
            col.Field("EmployeeID").Add();
            col.Field("ShipCity").CustomAttributes(custom => { custom.AddAttribute("title", "'{{"{ { "}}:ShipCity {{}}}}'");}).Add();
            col.Field("ShipCountry").Add();
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
                var DataSource1 = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.DataSource = DataSource1;
                return View();
            }
          }
       }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Cell_images/Cell_img3.png)

## Displaying HTML content

This will helps you to show actual HTML value in grid content and header. To disable HTML code, set `DisableHtmlEncode` property of `Columns` as true. 

The following code example describes the above behavior.

{% tabs %}

{% highlight razor %}

@{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("CustomerID").HeaderText("<div>Cust ID</div>").disableHtmlEncode(true).Add();
                col.Field("EmployeeID").HeaderText("<div>Employee ID</div>").disableHtmlEncode(false).Add();
                col.Field("ShipCountry").Add();
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
                var DataSource1 = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.DataSource = DataSource1;
                return View();
             }
          }
       }
{% endhighlight  %}
{% endtabs %} 

The following output is displayed as a result of the above code example.

![](Cell_images/Cell_img4.png)


## Tooltip

When you move the cursor over the particular cell it provides an information about the corresponding cell value.

**Template**

HTML templates can be specified in the `Tooltip` property of the particular column cell as a string (HTML element) or ID of the template's HTML element.You can use JsRender syntax in the template. For more information about JsRender syntax, please refer [this link](http://www.jsviews.com/#jsrapi "this link"). 

N> It's a standard way to enclose the template within the `script` tag with `type` as "text/x-jsrender". 
N> The `Tooltip` template must contain `value` property to bind the corresponding cell text in tooltip
 
The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}
 
@{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("ShipCity").Tooltip("#colTip").Add();
                col.Field("Freight").Add();
            }).Render();
}

{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
        public class GridController : Controller
         {
           public IActionResult DetailTemplate()
               {
                  var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
                  ViewBag.datasource = DataSource;
                  return View();
                }
           }
        }
{% endhighlight  %}
{% highlight js %}

     <script type="text/template" id="colTip">
          {{"{{"}}:value{{}}}}
      </script>
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Cell_images/Cell_img5.png)

## ClipMode

When the cell value contains a long text that is not fit into the grid column cell, the `ClipMode` property is used. By using the `ClipMode`, the cell value will be displayed with ellipsis or with clipped content when the text overflows inside a column cell.

N> By default the `ClipMode` will be set as `Clip`. 

**List of types**
  
 1. Clip
 2. Ellipsis
 3. EllipsisWithTooltip 
 
### Clip

When the content overflows, the remaining content will be hidden in the particular cell

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

@{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipName").ClipMode(ClipMode.Clip).Add();
                col.Field("Freight").Add();
            }).Render();
}
{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
        public class GridController : Controller
         {
          public IActionResult DetailTemplate()
            {
               var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
               ViewBag.datasource = DataSource;
                return View();
             }
          }
        }
{% endhighlight  %}
{% endtabs %}


The following output is displayed as a result of the above code example.

![](Cell_images/Cell_img6.png)
 
### Ellipsis

Ellipsis will be displayed when the content overflows its column width. Here Tooltip will not be shown for corresponding columns.

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

@{Html.EJ().Grid<Object>("FlatGrid")
            .Datasource((IEnumerable<object>)ViewBag.DataSource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipName").ClipMode(ClipMode.Ellipsis).Add();
                col.Field("Freight").Add();
            }).Render();
}
{% endhighlight  %}
{% highlight c# %}

      namespace MVCSampleBrowser.Controllers
       {
         public class GridController : Controller
          {
            public IActionResult DetailTemplate()
             {
                  var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
                  ViewBag.datasource = DataSource;
                  return View();
              }
          }
       }
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Cell_images/Cell_img7.png)

### Ellipsis With Tooltip

Ellipsis will be displayed when the content overflows its column width. Here tooltip will be shown only for the corresponding column cells that shows ellipsis.

N> If `ClipMode` is set as `EllipsisWithTooltip`, then `Tooltip` must be given.

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

@{Html.EJ().Grid<Object>("FlatGrid")
        .Datasource((IEnumerable<object>)ViewBag.DataSource)
        .AllowPaging()
        .Columns(col =>
        {
            col.Field("OrderID").Add();
            col.Field("ShipCity").Add();
            col.Field("ShipName").Tooltip("#colTip").ClipMode(ClipMode.EllipsisWithTooltip).Add();
            col.Field("Freight").Add();
        }).Render();
}
{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
        public class GridController : Controller
         {
          public IActionResult DetailTemplate()
            {
               var DataSource = new NorthwindDataContext().EmployeeViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
             }
          }
        }
{% endhighlight  %}
{% highlight js %}

      <script type="text/template" id="colTip">
          {{"{{"}}:value{{}}}}
      </script>
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Cell_images/Cell_img8.png)



