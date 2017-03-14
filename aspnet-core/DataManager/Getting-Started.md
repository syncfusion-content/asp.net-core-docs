---
layout: post
title: Getting-Started | DataManager | ASP.NET Core | Syncfusion
description: How to create the DataManager
platform: aspnet-core
control: DataManager
documentation: ug
---

# Getting Started 

## Create your DataManager in the ASP.NET Core

DataManager is used to manage relational data. It supports CRUD (Create, Read, Update, and Destroy) in individual requests and Batch. DataManager uses DataManager control for processing and ej.Query for serving the data. DataManager control communicates with data source and ej.Query generates data queries that are read by DataManager. 

### Configure Demo Application

This section briefly describes how to make a connection to WCF “Northwind” OData service and generate a report with top five orders from customer HANAR with higher Freight charges.  In this application scenario, you can learn how to bind the DataManager to the Grid control to do paging, filtering and sorting with Grid control in the DataManager by using ej.Query.

### Create Connection

To define connection to data source, you can use the DataManager control. The data source can be local or remote. Local data source is the local data and remote data source is any web service. 

In this application, as you have web service for Northwnd database, you can assign the web service URL link to the URL property of DataManager, and you can enable crossDomain to retrieve data from another domain.

{% highlight CSHTML %} 
 
    /*ej-Tag Helper code to render DataManager*/

    <e-datamanager url="//mvc.syncfusion.com/Services/Northwnd.svc/Orders" cross-domain="true"></e-datamanager>

{% endhighlight  %}

{% highlight Razor %} 

    /*Razor code to render DataManager*/

    @{Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").CrossDomain(true).Render();}

{% endhighlight  %}

N> To render the DataManager Control you can use either Razor or Tag helper code as given in the above code snippet.

You can use the ej.Query to generate the report from web service.

## Binding with Grid Control

You can bind the DataManager with Grid by defining the ID of DataManager in the DataManagerID property of the Grid control.

{% highlight CSHTML %}

    /*ej-Tag Helper code to render DataManager*/

    <ej-grid id="FlatGrid" allow-sorting="true" allow-paging="true">
        <e-datamanager url="http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/?$top=45" offline="true"></e-datamanager>
        <e-columns>
            <e-column field="OrderID" header-text="Order ID" text-align="Right" width="75"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" width="80"></e-column>
            <e-column field="EmployeeID" header-text="Employee ID" text-align="Left" width="75"></e-column>
            <e-column field="Freight" header-text="Freight" format="{0:C2}" text-align=Right width="75"></e-column>
            <e-column field="OrderDate" header-text="Order Date" format="{0:MM/dd/yyyy}" text-align=Right width="80"></e-column>
            <e-column field="ShipCity" header-text="Ship City" width="110"></e-column>
        </e-columns>
    </ej-grid>

{% endhighlight  %}

{% highlight Razor %}

    /*Razor code to render DataManager*/

    @{Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").CrossDomain(true).Render();}

    @{Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")
        .DataManagerID("FlatData") //DataManagerID(DataManager ID)
        .Query("new ej.Query().take(5)")
        .Columns(col =>
        {
            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
        }).Render();
    }

{% endhighlight  %}

When you run, the following table is displayed.

![](Getting-Started_images/Getting-Started_img1.png)

DataManager with Grid Control
{:.caption}

## Filter

You can generate the Filter query to filter the CustomerID column based on VINET value and it is ran by using the DataManager.

The where function is used to filter the records based on the specified filter condition.

The select property of ejQuery is used to retrieve the specified columns from the data source.

{% highlight CSHTML %}

    /*ej-Tag Helper code to render DataManager*/

    <ej-grid id="FlatGrid" allow-sorting="true" allow-paging="true" allow-filtering="true">
        <e-datamanager url="http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/?$top=45" offline="true"></e-datamanager> 
        <e-filter-settings>
            <e-filtered-columns>
                <e-filtered-column field="CustomerID" operator="Equals" value="VINET"></e-filtered-column>
            </e-filtered-columns>
        </e-filter-settings>
        <e-columns>
            <e-column field="OrderID" header-text="Order ID" text-align="Right" width="75"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" width="80"></e-column>
            <e-column field="EmployeeID" header-text="Employee ID" text-align="Left" width="75"></e-column>
            <e-column field="Freight" header-text="Freight" format="{0:C2}" text-align=Right width="75"></e-column>
            <e-column field="OrderDate" header-text="Order Date" format="{0:MM/dd/yyyy}" text-align=Right width="80"></e-column>
            <e-column field="ShipCity" header-text="Ship City" width="110"></e-column>
        </e-columns>
    </ej-grid>


{% endhighlight %}

{% highlight Razor %}

    /*Razor code to render DataManager*/

    @{Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").CrossDomain(true).Render();}

    @{Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")
        .DataManagerID("FlatData")
        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).where('CustomerID', 'equal', 'VINET').take(5)")
        //where(fieldName, operator, value, [ignoreCase])
        .Columns(col =>
        {
            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
        }).Render();
    }

{% endhighlight %}

When you run the filter query and bind the result to the Grid, the following table is displayed.

![](Getting-Started_images/Getting-Started_img2.png)

Data with Filtering
{:.caption}

## Sort

You can generate the Sort query to sort the Freight column in descending order and that is executed by using the DataManager. 

The sortBy property of ejQuery is used to sort the records based on the field and direction specified.

{% highlight CSHTML %}

    /*ej-Tag Helper code to render DataManager*/

    <ej-grid id="FlatGrid" allow-sorting="true" allow-paging="true" allow-multi-sorting="true">
        <e-datamanager url="http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/?$top=45" offline="true"></e-datamanager> 
    
        <e-sort-settings>
            <e-sorted-columns>
                <e-sorted-column field="Freight" direction="Descending">

                </e-sorted-column>
            </e-sorted-columns>
        </e-sort-settings>
        <e-columns>
            <e-column field="OrderID" header-text="Order ID" text-align="Right" width="75"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" width="80"></e-column>
            <e-column field="EmployeeID" header-text="Employee ID" text-align="Left" width="75"></e-column>
            <e-column field="Freight" header-text="Freight" format="{0:C2}" text-align=Right width="75"></e-column>
            <e-column field="OrderDate" header-text="Order Date" format="{0:MM/dd/yyyy}" text-align=Right width="80"></e-column>
            <e-column field="ShipCity" header-text="Ship City" width="110"></e-column>
        </e-columns>
    </ej-grid>

{% endhighlight %}

{% highlight Razor %}

/*Razor code to render DataManager*/

    @{Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").CrossDomain(true).Render();}

    @{Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")
            .DataManagerID("FlatData")
            .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).where('CustomerID', 'equal', 'VINET').sortBy('Freight desc').take(5)")
            //sortBy(field direction)
            .Columns(col =>
            {
                col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
                col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
                col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
                col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
            }).Render();
    }

{% endhighlight %}

When you run the sort query and bind the result to the table, the following table is displayed.

![](Getting-Started_images/Getting-Started_img3.png)

Data with Sorting
{:.caption}

## Page

You can generate the Paging query to get the top four orders and it is ran by using the DataManager.  

The Page property of ejQuery is used to retrieve the records based on the given pageIndex and pageSize.

{% highlight CSHTML %}

    /*ej-Tag Helper code to render DataManager*/

    <ej-grid id="FlatGrid" allow-sorting="true" allow-paging="true" allow-multi-sorting="true">
        <e-datamanager url="http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/?$top=45" offline="true"></e-datamanager> 
        <e-sort-settings>
            <e-sorted-columns>
                <e-sorted-column field="Freight" direction="Descending">
                </e-sorted-column>
            </e-sorted-columns>
        </e-sort-settings>
        <e-page-settings page-count="3" page-size="5">       
        </e-page-settings>
        <e-columns>
            <e-column field="OrderID" header-text="Order ID" text-align="Right" width="75"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" width="80"></e-column>
            <e-column field="EmployeeID" header-text="Employee ID" text-align="Left" width="75"></e-column>
            <e-column field="Freight" header-text="Freight" format="{0:C2}" text-align=Right width="75"></e-column>
            <e-column field="OrderDate" header-text="Order Date" format="{0:MM/dd/yyyy}" text-align=Right width="80"></e-column>
            <e-column field="ShipCity" header-text="Ship City" width="110"></e-column>
        </e-columns>
    </ej-grid>

{% endhighlight %}

{% highlight Razor %}

    /*Razor code to render DataManager*/

    @{Html.EJ().DataManager("FlatData").URL("http://mvc.syncfusion.com/Services/Northwnd.svc/Orders/").CrossDomain(true).Render();}

    @{Html.EJ().Grid<MVCdoc.OrdersView>("FlatGrid")
        .DataManagerID("FlatData")
        .Query("new ej.Query().select(['OrderID', 'CustomerID', 'EmployeeID', 'ShipCity', 'Freight']).where('CustomerID', 'equal', 'VINET').sortBy('Freight desc').page(3,5)")
        //page(pageIndex,pageSize)
        .Columns(col =>
        {

            col.Field("OrderID").HeaderText("Order ID").IsPrimaryKey(true).TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("CustomerID").HeaderText("Customer ID").Width(80).Add();
            col.Field("EmployeeID").HeaderText("Employee ID").TextAlign(TextAlign.Right).Width(75).Add();
            col.Field("Freight").HeaderText("Freight").TextAlign(TextAlign.Right).Width(75).Format("{0:C}").Add();
            col.Field("ShipCity").HeaderText("Ship City").Width(110).Add();
        }).Render();
    }

{% endhighlight %}

![](Getting-Started_images/Getting-Started_img4.png)

In this section, you can learn how to enable basic properties available in the DataManager and the usage of the various queries in the DataManager.  

