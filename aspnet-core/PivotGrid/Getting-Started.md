---
layout: post
title: Getting-Started
description: getting started
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Getting Started

Refer the [Getting Started](/aspnet-core/getting-started) page of the introduction part to know more about the basic system requirements and the steps to configure the Syncfusion components in an ASP.NET Core application.

Ensure once whether all the necessary dependency packages are included within the *bower.json* file as mentioned [here](/aspnet-core/getting-started#configure-syncfusion-components-in-aspnet-core-application), so that the required scripts and CSS to render the PivotGrid control gets installed and loads into the mentioned location (**wwwroot -> lib**) within your project.

Also, check whether the assembly dependency package **Syncfusion.EJ.Pivot**  added within the *project.json* file.

Now, refer the necessary scripts and CSS files into your *_Layout.cshtml* page from the **wwwroot -> lib -> syncfusion-javascript** folder.

{% highlight cshtml %}

<html>
<head>
    <environment names="Development">
        <link rel="stylesheet" href="~/lib/bootstrap/dist/css/bootstrap.css" />
        <link rel="stylesheet" href="~/css/site.css" />
        <link href="~/lib/syncfusion-javascript/Content/ej/web/default-theme/ej.web.all.min.css" rel="stylesheet" />
        <link href="~/lib/syncfusion-javascript/Content/ej/web/responsive-css/ej.responsive.css" rel="stylesheet" />
    </environment>
</head>
<body>

    <environment names="Development">
        <script src="~/lib/jquery/dist/jquery.js"></script>
        <script src="~/lib/bootstrap/dist/js/bootstrap.js"></script>
        <script src="~/js/site.js" asp-append-version="true"></script>
        <script src="~/lib/syncfusion-javascript/Scripts/jsrender.min.js"></script>
        <script src="~/lib/syncfusion-javascript/Scripts/ej/web/ej.web.all.min.js"></script>
    </environment>

</body>
</html>

{% endhighlight %}

It is necessary to define the following namespace within the *_viewImports.cshtml* page in order to make use of the PivotGrid control with the tag helper support.
 
{% highlight cshtml %}
 
@using Syncfusion.JavaScript
@addTagHelper "*, Syncfusion.EJ"
@addTagHelper "*, Syncfusion.EJ.Pivot"
    
{% endhighlight %}

N> Script manager must be defined at the bottom of the *_Layout.cshtml* page.

## Relational

This section covers the information that you need to know to populate a simple PivotGrid with Relational data source.

### Initialize PivotGrid

Before initializing, empty the contents of Index.cshtml file under Views > Home folder and add the following codes.

{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1"></ej-pivot-grid>

{% endhighlight %}

### Populate PivotGrid With Data

Let us now see how to populate the PivotGrid control using a sample JSON data as shown below. 

{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1" load="onload"></ej-pivot-grid>

<script type="text/javascript">
function onload(args) {
    args.model.dataSource.data = [
                    { Amount: 100, Country: "Canada", Date: "FY 2005", Product: "Bike", Quantity: 2, State: "Alberta" },
                    { Amount: 200, Country: "Canada", Date: "FY 2006", Product: "Van", Quantity: 3, State: "British Columbia" },
                    { Amount: 300, Country: "Canada", Date: "FY 2007", Product: "Car", Quantity: 4, State: "Brunswick" },
                    { Amount: 150, Country: "Canada", Date: "FY 2008", Product: "Bike", Quantity: 3, State: "Manitoba" },
                    { Amount: 200, Country: "Canada", Date: "FY 2006", Product: "Car", Quantity: 4, State: "Ontario" },
                    { Amount: 100, Country: "Canada", Date: "FY 2007", Product: "Van", Quantity: 1, State: "Quebec" },
                    { Amount: 200, Country: "France", Date: "FY 2005", Product: "Bike", Quantity: 2, State: "Charente-Maritime" },
                    { Amount: 250, Country: "France", Date: "FY 2006", Product: "Van", Quantity: 4, State: "Essonne" },
                    { Amount: 300, Country: "France", Date: "FY 2007", Product: "Car", Quantity: 3, State: "Garonne (Haute)" },
                    { Amount: 150, Country: "France", Date: "FY 2008", Product: "Van", Quantity: 2, State: "Gers" },
                    { Amount: 200, Country: "Germany", Date: "FY 2006", Product: "Van", Quantity: 3, State: "Bayern" },
                    { Amount: 250, Country: "Germany", Date: "FY 2007", Product: "Car", Quantity: 3, State: "Brandenburg" },
                    { Amount: 150, Country: "Germany", Date: "FY 2008", Product: "Car", Quantity: 4, State: "Hamburg" },
                    { Amount: 200, Country: "Germany", Date: "FY 2008", Product: "Bike", Quantity: 4, State: "Hessen" },
                    { Amount: 150, Country: "Germany", Date: "FY 2007", Product: "Van", Quantity: 3, State: "Nordrhein-Westfalen" },
                    { Amount: 100, Country: "Germany", Date: "FY 2005", Product: "Bike", Quantity: 2, State: "Saarland" },
                    { Amount: 150, Country: "United Kingdom", Date: "FY 2008", Product: "Bike", Quantity: 5, State: "England" },
                    { Amount: 250, Country: "United States", Date: "FY 2007", Product: "Car", Quantity: 4, State: "Alabama" },
                    { Amount: 200, Country: "United States", Date: "FY 2005", Product: "Van", Quantity: 4, State: "California" },
                    { Amount: 100, Country: "United States", Date: "FY 2006", Product: "Bike", Quantity: 2, State: "Colorado" },
                    { Amount: 150, Country: "United States", Date: "FY 2008", Product: "Car", Quantity: 3, State: "New Mexico" },
                    { Amount: 200, Country: "United States", Date: "FY 2005", Product: "Bike", Quantity: 4, State: "New York" },
                    { Amount: 250, Country: "United States", Date: "FY 2008", Product: "Car", Quantity: 3, State: "North Carolina" },
                    { Amount: 300, Country: "United States", Date: "FY 2007", Product: "Van", Quantity: 4, State: "South Carolina" }
    ];
}
</script>

{% endhighlight %}

The JSON data is set to the **"data"** property present inside the **"e-data-source"** object. **"e-data-source"** object allows us to set both datasource as well as the fields that needs to be displayed in the row, column, value and filter section of the PivotGrid control.
  
{% highlight cshtml %}
  
<ej-pivot-grid id="PivotGrid1" load="onload">
    <e-data-source>
        <e-pivot-rows>
            <e-row-field field-name="Country" field-caption="Country"></e-row-field>
        </e-pivot-rows>
        <e-pivot-columns>
            <e-column-field field-name="Product" field-caption="Product"></e-column-field>
        </e-pivot-columns>
        <e-pivot-values>
            <e-value-field field-name="Amount" field-caption="Amount"></e-value-field>
        </e-pivot-values>
    </e-data-source>
</ej-pivot-grid>

{% endhighlight %}

The above code will generate a simple PivotGrid with "Country" field in Row, "Product" field in Column and "Amount" field in Value section.

![](Getting-Started_images/purejs.png)

### Apply Sorting

You can sort a field either to ascending or descending order using the "sort-order" property. Sorting is applicable only for Row and Column fields. By default, fields are arranged in ascending order.
 
{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1" load="onload">
    <e-data-source>
        <e-pivot-rows>
            <e-row-field field-name="Country" field-caption="Country" sort-order="Descending"></e-row-field>
        </e-pivot-rows>
        <e-pivot-columns>
            <e-column-field field-name="Product" field-caption="Product"></e-column-field>
        </e-pivot-columns>
        <e-pivot-values>
            <e-value-field field-name="Amount" field-caption="Amount"></e-value-field>
        </e-pivot-values>
    </e-data-source>
</ej-pivot-grid>

{% endhighlight %}

![](Getting-Started_images/purejssorting.png)

### Sort Row/Column by Date

You can sort a field either to ascending or descending order acording to date by using the **sortOrder** property. Sorting is applicable only for Row and Column fields. By default, fields are arranged in ascending order.

N> To apply sorting by date, you need to specify the require `format` and `formatString` to the field.

{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1" load="onload">
    <e-data-source>
        <e-pivot-rows>
            <e-row-field field-name="Date" field-caption="Date" format="date" format-string="dd-MM-yyy" sort-order="Descending"></e-row-field>
        </e-pivot-rows>
        <e-pivot-columns>
            <e-column-field field-name="Day" field-caption="Day" format="date" format-string="ddd" sort-order="Ascending"></e-column-field>
        </e-pivot-columns>
        <e-pivot-values>
            <e-value-field field-name="Amount" field-caption="Amount"></e-value-field>
        </e-pivot-values>
    </e-data-source>
</ej-pivot-grid>

<script type="text/javascript">
function onload(args) {
    args.model.dataSource.data = [
            { Amount: 100, Date: "5-1-2017", Day: "Wednesday" },
            { Amount: 200, Date: "1-2-2017", Day: "Sunday" },
            { Amount: 300, Date: "1-1-2018", Day: "Thursday" },
            { Amount: 150, Date: "5-1-2018", Day: "Wednesday" },
            { Amount: 200, Date: "1-2-2017", Day: "Thursday" },
            { Amount: 100, Date: "1-1-2018", Day: "Sunday" },
            { Amount: 200, Date: "5-1-2017", Day: "Wednesday" },
            { Amount: 250, Date: "1-2-2017", Day: "Sunday" }
            //....
        ];
}
</script>

{% endhighlight %}

![](Getting-Started_images/sortbydate.png)

### Apply Summary Types

Allow us to specify the required summary type that PivotGrid should use in its summary cells. **"Sum"** is the default summary type. Following are the summary types that are supported:

* Sum
* Average
* Count
* Min
* Max

{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1" is-responsive="true" load="onload">
    <e-data-source>
        <e-pivot-rows>
            <e-row-field field-name="Country" field-caption="Country"></e-row-field>
        </e-pivot-rows>
        <e-pivot-columns>
            <e-column-field field-name="Product" field-caption="Product"></e-column-field>
        </e-pivot-columns>
        <e-pivot-values>
            <e-value-field field-name="Amount" field-caption="Amount" summary-type="Average"></e-value-field>
            <e-value-field field-name="Quantity" field-caption="Quantity" summary-type="Count"></e-value-field>
        </e-pivot-values>
    </e-data-source>
</ej-pivot-grid>

{% endhighlight %}    

![](Getting-Started_images/purejssummarytype.png)

## OLAP

This section covers the information that you need to know to populate a simple PivotGrid with OLAP data source.

### Initialize PivotGrid

Before initializing, empty the contents of Index.cshtml file under Views > Home folder and add the following codes.

{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1"></ej-pivot-grid>

{% endhighlight %}

### Populate PivotGrid With DataSource

Initializes the OLAP datasource for PivotGrid control as shown below.

{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1">
    <e-data-source catalog="Adventure Works DW 2008 SE" cube="Adventure Works" data="//bi.syncfusion.com/olap/msmdpump.dll">
        <e-pivot-rows>
            <e-row-field field-name="[Date].[Fiscal]"></e-row-field>
        </e-pivot-rows>
        <e-pivot-columns>
            <e-column-field field-name="[Customer].[Customer Geography]"></e-column-field>
        </e-pivot-columns>
        <e-pivot-values>
            <e-value-field axis="Column">
                <e-measures>
                    <e-measure-items field-name="[Measures].[Internet Sales Amount]"></e-measure-items>
                </e-measures>
            </e-value-field>
        </e-pivot-values>
    </e-data-source>
</ej-pivot-grid>

{% endhighlight %}

The above code will generate a simple PivotGrid with "Fiscal" field in Row, "Customer Geography" field in Column and "Internet Sales Amount" field in Value section.

![](Getting-Started_images/Olap.png)
