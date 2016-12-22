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

## Details Template

It provides a detailed view /additional information about each row of the grid. You can render any type of JsRender template and assign the script template id in the `DetailsTemplate` property. And also you can change HTML elements in detail template row into JavaScript controls using `DetailsDataBound ` event.

On enabling details template, new column will be added in grid with an expander button in it and that can be expanded or collapsed to show or hide the underlying details row respectively.

N> It's a standard way to enclose the template within the `script` tag with `type` as "text/x-jsrender".

The following code example describes the above behavior.

{% tabs %}
{% highlight  razor %}

   @{Html.EJ().Grid<EmployeeView>("DetailTemplate")
          .Datasource((IEnumerable<object>)ViewBag.datasource)
          .DetailsTemplate("#tabGridContents")
          .ClientSideEvents(eve => { eve.DetailsDataBound("detailGridData"); })
          .Columns(col =>
               {
                     col.Field("EmployeeID").Add();
                     col.Field("FirstName").Add();
                     col.Field("Title").Add();
                     col.Field("City").Add();
                     col.Field("Country").Add();
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

   <script id="tabGridContents" type="text/x-jsrender">
        <div class="tabcontrol" id="Test">
                  <ul>
                      <li><a href="#gridTab{{"{{"}}:EmployeeID {{}}}}">Stock Grid</a></li>
                  </ul>
             <div id="gridTab{{"{{"}}:EmployeeID {{}}}}">
                  <div id="detailGrid">
                    </div>
             </div>
       </div>
</script>
<script src="~/Scripts/jsondata.min.js"></script>
<script type="text/javascript">
      function detailGridData(e) {
          var filteredData = e.data["EmployeeID"];
          // the datasource "window.ordersView" is referred from jsondata.min.js
          var data = ej.DataManager(window.ordersView).executeLocal(ej.Query().where("EmployeeID", "equal", parseInt(filteredData), true).take(5));
          e.detailsElement.find("#detailGrid").ejGrid({
          dataSource: data,
          columns: [
                        {field: "OrderID"},
                        {field: "EmployeeID"},
                        {field: "ShipCity"},
                        {field: "ShipCountry"},
	                    {field: "Freight"}
	               ]
	     });
       e.detailsElement.find(".tabcontrol").ejTab();
}
</script>
{% endhighlight  %}
{% endtabs %}
The following output is displayed as a result of the above code example.

![](Row_images/Row_img2.png)

## Row Template

Row template enables you to set the customized look and behavior to grid all rows. `RowTemplate` property can be used bind the `id` of HTML template.
The following code example describes the above behavior.

{% tabs %}
{% highlight  js %}
<script id="templateData" type="text/x-jsrender">
    <tr>
             <td class="photo">
                 <img style="width:130px;height: 160px" src="/13.2.0.29/themes/web/images/employees/{{"{{"}}:EmployeeID {{}}}}.png" alt="{{"{{"}}:EmployeeID {{}}}}" />
             </td>
             <td class="details">
                 <table class="CardTable" cellpadding="3" cellspacing="2">
                      <colgroup>
                              <col width="50%">
                              <col width="50%">
                      </colgroup>
                      <tbody>
                          <tr>
                              <td class="CardHeader">First Name</td>
                              <td>{{"{{"}}:FirstName {{}}}} </td>
                          </tr>
                          <tr>
                              <td class="CardHeader">Last Name</td>
                              <td>{{"{{"}}:LastName {{}}}}</td>
                          </tr>
                          <tr>
                              <td class="CardHeader">Title</td>
                              <td>{{"{{"}}:Title {{}}}}</td>
                          </tr>
                      </tbody>
                 </table>
            </td>
      </tr>
</script>
{% endhighlight  %}
{% highlight  css %}
<style>
    .photo img {
        width: 130px;
    }
    .photo, .details {
        border-color: #c4c4c4;
        border-style: solid;
    }
    .photo {
        border-width: 1px 0px 0px 0px;
    }
    .details {
        border-width: 1px 0px 0px 1px;
    }
    .details > table {
            width: 100%;
        }
    .CardHeader {
        font-weight: bolder;
    }
</style>
{% endhighlight  %}
{% highlight  razor %}
@{Html.EJ().Grid<EmployeeView>("RowTemplate")
        .Datasource((IEnumerable<object>)ViewBag.datasource)
        .Query("new ej.Query().take(2)")
        .RowTemplate("#templateData")    // row template
        .Columns(col =>
            {
                col.HeaderText("Photo").Width(30).Add();
                col.HeaderText("Employee Details").Width(70).Add();
            }).Render();
       
}
{% endhighlight  %}
{% highlight c# %}
namespace MVCSampleBrowser.Controllers
  {
	   public class GridController : Controller
         {
               public IActionResult RowTemplate()
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

![](Row_images/Row_img3.png)

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


