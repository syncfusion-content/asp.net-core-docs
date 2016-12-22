---
layout: post
title: Paging with Grid widget for Syncfusion Essential ASP.NET Core
description: How to enable paging and its functionalites.
platform: ASP.NET Core
control: Grid
documentation: ug
---
# Paging

 You can display the grid records in paged view, by setting `AllowPaging` property as `true`.

The code snippet to enable paging is follows.

{% tabs %}
{% highlight razor %}

       @{Html.EJ().Grid<Object>("Paging")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCountry").Add();
                col.Field("Freight").Format("{0:C}").Add();
            }).Render();
         }
{% endhighlight  %} 
{% highlight c# %}

      namespace MVCSampleBrowser.Controllers
      {
       public class GridController : Controller
       { 
         public IActionResult Paging()
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
 
 ![](Paging_images/Paging_img1.png)

## Pager with query string


You can pass the current page information as a query string while navigating to other page. To enable query string, set the `EnableQueryString` property of `PageSettings` as `true`.

The following code example describes the above behavior.

{% tabs %}
{% highlight razor %}

     @{Html.EJ().Grid<Object>("Paging")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .PageSettings(Page => { Page.EnableQueryString(true); })
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("CustomerID").Add();
                col.Field("ShipCountry").Add();
                col.Field("Freight").Format("{0:C}").Add();
            }).Render();
        }            
 {% endhighlight  %} 
 {% highlight c# %} 
        
          namespace MVCSampleBrowser.Controllers
           {
            public class GridController : Controller
              { 
               public IActionResult Paging()
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

 ![](Paging_images/Paging_img2.png)


## Pager template

Apart from default pager, there is an option to render a specific custom template in a grid pager. To render template in pager, set `EnableTemplates`  as true and `Template`  properties of `PageSettings`.

 Prevent to show the default pager while enabling the pager `Template`  by setting `ShowDefaults`  property of `PageSettings`  as `false`.

 N> It's a standard way to enclose the `Template`  within the `script` tag with `type` as "text/x-jsrender".

The following code example describes the above behavior.

{% tabs %} 

{% highlight razor %}

        @{Html.EJ().Grid<OrdersView>("Paging")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging() 
            .PageSettings(Page => { Page.EnableTemplates().Template("#template").ShowDefaults(false); })
            .ClientSideEvents(e=>{e.Create("create"); }) 
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add();
                col.Field("Freight").Format("{0:C}").Add();
            }).Render();
         }         
{% endhighlight  %}
{% highlight c# %}

     namespace MVCSampleBrowser.Controllers
      {
       public partial class GridController : Controller
       {
        public IActionResult Paging()
          {
           var DataSource = new NorthwindDataContext().OrdersViews.ToList();
           ViewBag.datasource = DataSource;
           return View();
           }
       }
     }

{% endhighlight  %}
{% highlight js %}

         <script id="template" type="text/x-jsrender">
            <input id="currentPage" type="text" style="text-align: center; width: 32px; height: 21px; background: white;" value="1" />
            <label>of 200</label>
            <button id="btn">Go to</button>
         </script>
          <script>
            function create(args) {
                     $("#btn").ejButton({
                       click : "btnClick"
                         });
                       }
             function btnClick(args) {
                     var val = $("#currentPage").val();
                     var gridObj = $("#Grid").data("ejGrid");
                      gridObj.gotoPage(args.val);
                     }
           </script>
{% endhighlight  %}
{% highlight css %}

     .e-grid .e-pager .e-pagercontainer {
	       border-width: 0px;
	       overflow: visible;
         }         
{% endhighlight  %} 
 {% endtabs %}  
 
 The following output is displayed as a result of the above code example.

![](Paging_images/Paging_img3.png)
