---
layout: post
title: Print Grid for Syncfusion Essential ASP.NET Core
description: How to enable print option in Grid
platform: ASP.NET Core
control: Grid
documentation: ug
---

# Print

You need to use `print()` method from Grid instance to print the Grid. You can add Print option in Toolbar item by adding `printGrid` in `toolbar-items`.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"printGrid"}'/>
        <e-columns>
            <e-column field="OrderID" header-text="Order ID" width="75" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="CustomerID" width="90"></e-column>
            <e-column field="EmployeeID" header-text="Employee ID" width="80" text-align="Right"></e-column>
            <e-column field="Freight" header-text="Freight" text-align="Right" width="80"></e-column>
            <e-column field="ShipCity" header-text="Ship City" width="90"></e-column>
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

![](Print-Grid_images/Print_img1.png)


## Page Setup

Some of print options are not configurable through JavaScript code. You need to customize layout, paper size, margins options through browser's page setup dialog. Please find the following guidelines link to browser page setup.

* [Chrome](https://support.google.com/chrome/answer/1379552?hl=en)
* [Firefox](https://support.mozilla.org/en-US/kb/how-print-web-pages-firefox)
* [Safari](http://www.mintprintables.com/print-tips/adjust-margins-osx/)
* [IE](http://www.helpteaching.com/help/print/index.htm) 

## Print on external Button Click

By default, the Grid can be print from toolbar. To print from external button action, you need to call the grid's [`print()`](http://help.syncfusion.com/js/api/ejgrid#methods:print) method from required button event.

{% tabs %}
{% highlight razor %}
   
   <button id="print">Print</button>
   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"printGrid"}'/>
        <e-columns>
            <e-column field="OrderID" header-text="Order ID" width="75" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" width="90"></e-column>
            <e-column field="EmployeeID" header-text="Employee ID" width="80" text-align="Right"></e-column>
            <e-column field="Freight" header-text="Freight" text-align="Right" width="80"></e-column>
            <e-column field="ShipCity" header-text="Ship City" width="90"></e-column>
        </e-columns>
   </ej-grid>
   <script type="text/javascript">
      $("#print").ejButton({ 
            showRoundedCorner: true,
            size: "mini",
            click: function () {
            $("#PrintGrid").ejGrid("print");
        }
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

![](Print-Grid_images/Print_img2.png)

{:caption}
Grid with external button for Print

![](Print-Grid_images/Print_img3.png)
{:caption}

Print dialog in Chrome browser

## Print Visible Page

By default, the Grid will print all records. To print current page, you need to set `print-mode` as `CurrentPage` in `e-page-settings` property.

{% tabs %}
{% highlight razor %}

   <ej-grid id="FlatGrid" allow-paging="true" datasource="ViewBag.DataSource">
      <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"printGrid"}'/>
       <e-page-settings print-mode="CurrentPage"></e-page-settings>
        <e-columns>
            <e-column field="OrderID" header-text="Order ID" width="75" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="CustomerID" width="90"></e-column>
            <e-column field="EmployeeID" header-text="Employee ID" width="80" text-align="Right"></e-column>
            <e-column field="Freight" header-text="Freight" text-align="Right" width="80"></e-column>
            <e-column field="ShipCity" header-text="Ship City" width="90"></e-column>
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
