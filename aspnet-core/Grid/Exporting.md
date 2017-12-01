---
layout: post
title: Exporting | Grid | ASP.NET Core | Syncfusion
description: exporting
platform: aspnet-core
control: Grid
documentation: ug
---

# Exporting

Exporting provides support to export Grid data into excel, word and PDF files. To export the grid, `export` JavaScript method should be called with export action as parameter. To make it work from grid tool bar, `ExcelExport`, `WordExport`, `PdfExport` toolbar items needs to be added in grid tool bar using `toolbar-items` property of `toolbar-settings` which are used to perform exporting. When you click the toolbar exporting icon, it internally invokes the `export` public method of Grid object to export.The code snippet for this is

{% tabs %}
 
{% highlight razor %}

    <ej-grid id="FlatGrid" datasource="ViewBag.datasource" allow-paging="true">
        <e-toolbar-settings show-toolbar="true" toolbar-items=@(new List&lt;string>() {"excelExport","wordExport","pdfExport" })>
           
        </e-toolbar-settings>
        <e-columns>
            <e-column field="OrderID" header-text="Order ID" text-align="Right" width="75"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" width="80"></e-column>
            <e-column field="EmployeeID" header-text="Employee ID" text-align="Left" width="75"></e-column>
            <e-column field="Freight" header-text="Freight" format="{0:C2}" text-align=Right width="75"></e-column>
            <e-column field="ShipCity" header-text="Ship City" width="110"></e-column>
        </e-columns>
    </ej-grid>


{% endhighlight  %}
{% highlight c# %}

    public partial class GridController : Controller
    {

        private NORTHWNDContext _context;

        public GridController(NORTHWNDContext context)
        {
            _context = context;
        }
        // GET: /<controller>/
        public ActionResult Exporting()
        {
            ViewBag.datasource = _context.Orders.Take(100).ToList();
            return View();
        }
        public ActionResult ExportToExcel(string GridModel)
        {
            ExcelExport exp = new ExcelExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = ConvertGridObject(GridModel);
            GridExcelExport excelExp = new GridExcelExport();
            excelExp.FileName = "Export.xlsx"; excelExp.Excelversion = ExcelVersion.Excel2010;
            excelExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, excelExp);
        }

        public ActionResult ExportToWord(string GridModel)
        {
            WordExport exp = new WordExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = ConvertGridObject(GridModel);
            GridWordExport wrdExp = new GridWordExport();
            wrdExp.FileName = "Export.docx"; wrdExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, wrdExp);
        }
        public ActionResult ExportToPdf(string GridModel)
        {
            PdfExport exp = new PdfExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = ConvertGridObject(GridModel);
            GridPdfExport pdfExp = new GridPdfExport();
            pdfExp.FileName = "Export.pdf"; pdfExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, pdfExp);
        }
        private GridProperties ConvertGridObject(string gridProperty)
        {
            GridProperties gridProp = new GridProperties();
            gridProp = (GridProperties)JsonConvert.DeserializeObject(gridProperty, typeof(GridProperties));
            return gridProp;
        }
    }

{% endhighlight  %}
{% endtabs %} 

# Hierarchy Grid Exporting

Grid will be exported with its child Grid. This can be achieved by enabling `IncludeChildGrid` property of the respective Exporting classes like `GridExcelExport`, `GridWordExport` and `GridPdfExport`. Include the dataSource needed for ChildGrid in the GridProperties object after deserializing them. Remaining procedures will be same as the normal Grid Exporting.

{% tabs %}
 
{% highlight razor %}

<ej-grid id="Grid" datasource=ViewBag.parent allow-paging="true">
    <ej-grid query-string="EmployeeID" datasource="ViewBag.child">
        <e-columns>
            <e-column field="OrderID" header-text="Order ID" text-align="Right" width="30"></e-column>
            <e-column field="ShipCity" header-text="Ship City" width="80"></e-column>
            <e-column field="CustomerID" header-text="Customer ID" width="80"></e-column>
            <e-column field="Freight" header-text="Freight" format="{0:C2}" text-align="Right" width="80"></e-column>
        </e-columns>
    </ej-grid>
    <e-toolbar-settings show-toolbar="true" toolbar-items=@(new List<string>() {"excelExport","wordExport","pdfExport" })>
    </e-toolbar-settings>
    <e-columns>
        <e-column field="EmployeeID" header-text="EmployeeID" text-align="Right" width="30"></e-column>
        <e-column field="FirstName" header-text="First Name" width="80"></e-column>
        <e-column field="LastName" header-text="Last Name" width="80"></e-column>
        <e-column field="Title" header-text="Title" width="80"></e-column>
        <e-column field="Country" header-text="Country" width="80"></e-column>
    </e-columns>
</ej-grid>


{% endhighlight  %}
{% highlight c# %}

    public partial class GridController : Controller
    {

        private NORTHWNDContext _contextData;

        public static List<Employees> emp = new List<Employees>();

        // GET: /<controller>/
        public ActionResult HierarchyGridExporting()
        {
            if (emp.Count == 0)
                BindParentData();
            ViewBag.parent = emp;
            ViewBag.child = _context.Orders.Take(100).ToList();
            return View();
        }
        public ActionResult ExportToExcel(string GridModel)
        {
            ExcelExport exp = new ExcelExport();
            var DataSource = emp;
            GridProperties gridProp = ConvertGridModel(GridModel);
            gridProp.ChildGrid.DataSource = _context.Orders.Take(100).ToList();
            GridExcelExport excelExp = new GridExcelExport();
            excelExp.FileName = "Export.xlsx"; excelExp.Excelversion = ExcelVersion.Excel2010;
            excelExp.Theme = "flat-saffron";
            excelExp.IncludeChildGrid = true;
            return exp.Export(gridProp, DataSource, excelExp);
        }

        public ActionResult ExportToWord(string GridModel)
        {
            WordExport exp = new WordExport();
            var DataSource = emp;
            GridProperties gridProp = ConvertGridModel(GridModel);
            gridProp.ChildGrid.DataSource = _context.Orders.Take(100).ToList();
            GridWordExport wrdExp = new GridWordExport();
            wrdExp.FileName = "Export.docx"; wrdExp.Theme = "flat-saffron";
            wrdExp.IncludeChildGrid = true;
            return exp.Export(gridProp, DataSource, wrdExp);
        }
        public ActionResult ExportToPdf(string GridModel)
        {
            PdfExport exp = new PdfExport();
            var DataSource = emp;
            GridProperties gridProp = ConvertGridModel(GridModel);
            gridProp.ChildGrid.DataSource = _context.Orders.Take(100).ToList();
            GridPdfExport pdfExp = new GridPdfExport();
            pdfExp.FileName = "Export.pdf"; pdfExp.Theme = "flat-saffron";
            pdfExp.IncludeChildGrid = true;
            return exp.Export(gridProp, DataSource, pdfExp);
        }
        private GridProperties ConvertGridModel(string gridProperty)
        {
            GridProperties gridProp = new GridProperties();
            gridProp = (GridProperties)JsonConvert.DeserializeObject(gridProperty, typeof(GridProperties));
            return gridProp;
        }
        private void BindParentData()
        {
            emp.Add(new Employees(1, "Nancy", "Davolio", new DateTime(1948, 12, 08), "USA", "Sales Representative"));
            emp.Add(new Employees(2, "Andrew", "Fuller", new DateTime(1952, 02, 19), "USA", "Vice President, Sales"));
            emp.Add(new Employees(3, "Janet", "Leverling", new DateTime(1963, 08, 30), "USA", "Sales Representative"));
            emp.Add(new Employees(4, "Margaret", "Peacock", new DateTime(1937, 09, 19), "USA", "Sales Representative"));
            emp.Add(new Employees(5, "Steven", "Buchanan", new DateTime(1955, 03, 04), "UK", "Sales Manager"));
            emp.Add(new Employees(6, "Michael", "Suyama", new DateTime(1963, 07, 02), "UK", "Sales Representative"));
            emp.Add(new Employees(7, "Robert", "King", new DateTime(1960, 05, 29), "UK", "Sales Representative"));
            emp.Add(new Employees(8, "Laura", "Callahan", new DateTime(1958, 01, 09), "USA", "Inside Sales Coordinator"));
            emp.Add(new Employees(9, "Sans", "Serif", new DateTime(1958, 10, 10), "USA", "Sales Representative"));

        }
        public class Employees
        {
            public Employees()
            {

            }
            public Employees(int EmployeeId, string FirstName, string LastName, DateTime BirthDate, string Country, string title)
            {

                this.EmployeeID = EmployeeId;
                this.FirstName = FirstName;
                this.LastName = LastName;
                this.BirthDate = BirthDate;
                this.Country = Country;
                this.Title = title;
            }
            public int EmployeeID { get; set; }
            public string FirstName { get; set; }
            public string LastName { get; set; }
            public DateTime BirthDate { get; set; }
            public string Country { get; set; }
            public string Title { get; set; }
        }
    }

{% endhighlight  %}
{% endtabs %} 


## Server Dependencies

Export Helper functions are available in the Assembly `Syncfusion.EJ.Export`, which is available in the Essential Studio builds. Full list of assemblies needed for grid Export as follows

    1.  Syncfusion.EJ
    2.  Syncfusion.EJ.Export
    3.  Syncfusion.Linq.Base
    4.  Syncfusion.Compression.Base
    5.  Syncfusion.DocIO.Base
    6.  Syncfusion.XlsIO.Base
    7.  Syncfusion.PDF.Base


## Support Export Types

Currently server helper function allows following three types of exporting.

    1.  Word
    2.  Excel
    3.  PDF

##  Server side handlers

In ASP.NET Corw, exporting is achieved by using action controller method. In controller method, Grid property is passed as string parameter, you need to deserialize it into the Grid Property. By using the `Export` server method, you can export the Grid into excel, PDF and word documents.

{% tabs %}
 
{% highlight razor %}

<ej-grid id="FlatGrid" datasource="ViewBag.datasource" allow-paging="true">
    <e-toolbar-settings show-toolbar="true" toolbar-items=@(new List<string>() {"excelExport","wordExport","pdfExport" })>

    </e-toolbar-settings>
    <e-columns>
        <e-column field="OrderID" header-text="Order ID" text-align="Right"></e-column>
        <e-column field="CustomerID" header-text="Customer ID"></e-column>
        <e-column field="EmployeeID" header-text="Employee ID" text-align="@TextAlign.Right"></e-column>
        <e-column field="Freight" header-text="Freight" text-align=Right></e-column>
        <e-column field="OrderDate" header-text="Order Date" text-align="@TextAlign.Right"></e-column>
        <e-column field="ShipCity" header-text="Ship City"></e-column>
    </e-columns>
</ej-grid>


{% endhighlight  %}
{% highlight c# %}

    public partial class GridController : Controller
    {

        private NORTHWNDContext _context;

        public GridController(NORTHWNDContext context)
        {
            _context = context;
        }
        // GET: /<controller>/
        public ActionResult Exporting()
        {
            ViewBag.datasource = _context.Orders.Take(100).ToList();
            return View();
        }
        public ActionResult ExportToExcel(string GridModel)
        {
            ExcelExport exp = new ExcelExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
            GridExcelExport excelExp = new GridExcelExport();
            excelExp.FileName = "Export.xlsx"; excelExp.Excelversion = ExcelVersion.Excel2010;
            excelExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, excelExp);
        }

        public ActionResult ExportToWord(string GridModel)
        {
            WordExport exp = new WordExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
            GridWordExport wrdExp = new GridWordExport();
            wrdExp.FileName = "Export.docx"; wrdExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, wrdExp);
        }
        public ActionResult ExportToPdf(string GridModel)
        {
            PdfExport exp = new PdfExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
            GridPdfExport pdfExp = new GridPdfExport();
            pdfExp.FileName = "Export.pdf"; pdfExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, pdfExp);
        }
    }

{% endhighlight  %}

{% endtabs %} 

On Exporting, the default routing path to server-side that contains the action name as ExportToExcel for Excel Exporting, ExportToWord for Word Exporting and ExportToPdf for PDF Exporting. The default controller name in routing path is the Grid view page’s Controller name. For instance, when Grid is rendered in GridFeatures View Page of Home Controller, then on Excel exporting Grid Content, the default routing path is ~/Home/ExportToExcel.



## Export Mapper in MVC

`export-to-pdf-action`, `export-to-word-action`,`export-to-excel-action` Grid property is used to modify the default routing path during exporting. By using these properties, you can use any action name in Controller for exporting and the action can be in any controller (Need not to be in Grid View Page Controller).

{% tabs %}
 
{% highlight razor %}


       <ej-grid id="FlatGrid" datasource="ViewBag.datasource" allow-paging="true" export-to-pdf-action="PdfAction" export-to-word-action="WordAction" export-to-excel-action="ExcelAction">
        <e-toolbar-settings show-toolbar="true" toolbar-items=@(new List<string>() {"excelExport","wordExport","pdfExport" }) >
           
        </e-toolbar-settings>
        <e-columns>
            <e-column field="OrderID" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID"></e-column>
            <e-column field="EmployeeID" header-text="Employee ID" text-align="@TextAlign.Right"></e-column>
            <e-column field="Freight" header-text="Freight" text-align=Right></e-column>
            <e-column field="OrderDate" header-text="Order Date" text-align="@TextAlign.Right"></e-column>
            <e-column field="ShipCity" header-text="Ship City"></e-column>
        </e-columns>
    </ej-grid>


{% endhighlight  %}

{% highlight c# %}

     private NORTHWNDContext _context;

        public GridController(NORTHWNDContext context)
        {
            _context = context;
        }
        // GET: /<controller>/
        public ActionResult Exporting()
        {
            ViewBag.datasource = _context.Orders.Take(100).ToList();
            return View();
        }
        public ActionResult ExcelAction(string GridModel)
        {
            ExcelExport exp = new ExcelExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
            GridExcelExport excelExp = new GridExcelExport();
            excelExp.FileName = "Export.xlsx"; excelExp.Excelversion = ExcelVersion.Excel2010;
            excelExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, excelExp);
        }

        public ActionResult WordAction(string GridModel)
        {
            WordExport exp = new WordExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
            GridWordExport wrdExp = new GridWordExport();
            wrdExp.FileName = "Export.docx"; wrdExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, wrdExp);
        }
        public ActionResult PdfAction(string GridModel)
        {
            PdfExport exp = new PdfExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
            GridPdfExport pdfExp = new GridPdfExport();
            pdfExp.FileName = "Export.pdf"; pdfExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, pdfExp);
        }
    }

{% endhighlight  %}
{% endtabs %} 


## Export required grid in single file

You can export required grids in single file using `ej.Grid.exportAll` method. This method can be used with export action and array of jQuery selector of grid which need to be export. The code snippet for it is

{% highlight js %}

    $('#exportAll').click(function(){
			ej.Grid.exportAll('MultipleExportToExcel',['Grid1', 'Grid2']);
		});

{% endhighlight %}

## List of properties ignored on export

Following are the list of properties that are exclude during grid export, to reduce the unwanted data transfer to server.  

* dataSource
* query
* rowTemplate
* detailsTemplate
* pageSettings
* enableRTL
* cssClass

## Export only visible records


By default `pageSettings` is ignored in export to facilitate all pages export. To achieve current visible page record export, `pageSettings` should be removed from ignore list using following code.

The snippet for this is.

{% highlight js %}

	var grid = $('#Grid').ejGrid('instance');
	grid.ignoreOnExport.splice(grid.ignoreOnExport.indexOf('pageSettings'), 1);

{% endhighlight %}

On server before calling the `Export` function, the data source should be processed using DataOperations's Execute function. 

{% highlight c# %}

       public partial class GridController : Controller
    {

        private NORTHWNDContext _context;

        public GridController(NORTHWNDContext context)
        {
            _context = context;
        }
        // GET: /<controller>/
            public ActionResult Exporting()
            {
                ViewBag.datasource = _context.Orders.Take(100).ToList();
                return View();
            }
            public ActionResult ExportToExcel(string GridModel)
            {
                ExcelExport exp = new ExcelExport();
                var DataSource = _context.Orders.Take(100).ToList();
                GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
                GridExcelExport excelExp = new GridExcelExport();
                excelExp.FileName = "Export.xlsx"; excelExp.Excelversion = ExcelVersion.Excel2010;
                excelExp.Theme = "flat-saffron";
                var dataSource = new DataOperations().Execute(DataSource, gridProp);
                return exp.Export(gridProp, dataSource, excelExp);
            }

            public ActionResult ExportToWord(string GridModel)
            {
                WordExport exp = new WordExport();
                var DataSource = _context.Orders.Take(100).ToList();
                GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
                GridWordExport wrdExp = new GridWordExport();
                wrdExp.FileName = "Export.docx"; wrdExp.Theme = "flat-saffron";
                var dataSource = new DataOperations().Execute(DataSource, gridProp);
                return exp.Export(gridProp, dataSource, wrdExp);
            }
            public ActionResult ExportToPdf(string GridModel)
            {
                PdfExport exp = new PdfExport();
                var DataSource = _context.Orders.Take(100).ToList();
                GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
                GridPdfExport pdfExp = new GridPdfExport();
                pdfExp.FileName = "Export.pdf"; pdfExp.Theme = "flat-saffron";
                var dataSource = new DataOperations().Execute(DataSource, gridProp);
                return exp.Export(gridProp, dataSource, pdfExp);
            }
        }

{% endhighlight %}

## Local data 

By default, client data source is not sent to server to prevent unwanted data transfer since all data origin is server. In case, if you don't want to query the data source again for exporting in server, the grid's client [`dataSource`](http://help.syncfusion.com/js/api/ejgrid#members:datasource) can be sent to server on export PostBack by removing the [`dataSource`](http://help.syncfusion.com/js/api/ejgrid#members:datasource) property in grid's ignore list. The code snippet for this as follows

{% highlight js %}

var grid = $('#GridId').ejGrid('instance');
grid.ignoreOnExport.splice(grid.ignoreOnExport.indexOf('dataSource'), 1);

{% endhighlight %}



## Themes

The grid export have 13 theme option to match with our [built-in control themes](http://helpjs.syncfusion.com/js/theming-in-essential-javascript-components#). They are

<table>
<tr><th>Enum</th><th>Equivalent string input</th></tr>

<tr><td>ExportTheme.FlatAzure</td><td>default-theme</td></tr>

<tr><td>ExportTheme.FlatSaffron</td><td>flat-saffron</td></tr>

<tr><td>ExportTheme.FlatLime</td><td>flat-lime</td></tr>

<tr><td>ExportTheme.FlatDarkAzure</td><td>flat-azure-dark</td></tr>

<tr><td>ExportTheme.FlatDarkSaffron</td><td>flat-saffron-dark</td></tr>

<tr><td>ExportTheme.FlatDarkLime</td><td>flat-lime-dark</td></tr>

<tr><td>ExportTheme.GradientAzure</td><td>gradient-azure</td></tr>

<tr><td>ExportTheme.GradientSaffron</td><td>gradient-saffron</td></tr>

<tr><td>ExportTheme.GradientLime</td><td>gradient-lime</td></tr>

<tr><td>ExportTheme.GradientDarkAzure</td><td>gradient-azure-dark</td></tr>

<tr><td>ExportTheme.GradientDarkSaffron</td><td>gradient-saffron-dark</td></tr>

<tr><td>ExportTheme.GradientDarkLime</td><td>gradient-lime-dark</td></tr>

<tr><td>ExportTheme.BootstrapTheme</td><td>bootstrap-theme</td></tr>

<tr><td>ExportTheme.None</td><td>none</td></tr>
</table>

Also, it has `none` option which will export the grid without any theme.  The desired theme name can be passed as a parameter to `Export` method and the code snippet for this as follows

{% tabs %}

{% highlight c# %}

    public partial class GridController : Controller
    {

        private NORTHWNDContext _context;

        public GridController(NORTHWNDContext context)
        {
            _context = context;
        }
        // GET: /<controller>/
        public ActionResult Exporting()
        {
            ViewBag.datasource = _context.Orders.Take(100).ToList();
            return View();
        }
        public ActionResult ExportToExcel(string GridModel)
        {
            ExcelExport exp = new ExcelExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
            GridExcelExport excelExp = new GridExcelExport();
            excelExp.FileName = "Export.xlsx"; excelExp.Excelversion = ExcelVersion.Excel2010;
            excelExp.Theme = "none";
            return exp.Export(gridProp, DataSource, excelExp);
        }

        public ActionResult ExportToWord(string GridModel)
        {
            WordExport exp = new WordExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
            GridWordExport wrdExp = new GridWordExport();
            wrdExp.FileName = "Export.docx"; wrdExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, wrdExp);
        }
        public ActionResult ExportToPdf(string GridModel)
        {
            PdfExport exp = new PdfExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = (GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
            GridPdfExport pdfExp = new GridPdfExport();
            pdfExp.FileName = "Export.pdf"; pdfExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, pdfExp);
        }
        public ActionResult ExportingGrid()

        {

            var DataSource = _context.Orders.Take(100).ToList();

            ViewBag.datasource = DataSource;

            return View();

        }
    }

{% endhighlight %}

{% highlight razor %}

    <ej-grid id="FlatGrid" datasource="ViewBag.datasource" allow-paging="true">
        <e-toolbar-settings show-toolbar="true" toolbar-items=@(new List<string>() {"excelExport","wordExport","pdfExport" }) >
           
        </e-toolbar-settings>
        <e-columns>
            <e-column field="OrderID" header-text="Order ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID"></e-column>
            <e-column field="EmployeeID" header-text="Employee ID" text-align="Right"></e-column>
            <e-column field="ShipCity" header-text="ShipCity" text-align=Right></e-column>
            <e-column field="ShipCountry" header-text="Ship Country" text-align="Right"></e-column>
            <e-column field="Freight" header-text="Freight"></e-column>
        </e-columns>
    </ej-grid

{% endhighlight %}
{% endtabs %}  
When the theme is set as none and the autoFormat is not set to the grid, then no theme is applied to the exported grid. The grid is exported without any theme as in the following screenshots:

![](Exporting_images/Customizing-Themes_img1.png)


## AutoFormat Class

The **AutoFormat** Class can be used to customize the styles or themes applied to the exported grid. With the autoFormat class, you can provide required color to the grid content, alt row background or border color.

The various properties available under the autoFormat class are listed in the following table.

<table>
<tr>
<th>
Properties</th><th>
Type</th><th>
Description</th></tr>
<tr>
<td>
FontFamily</td><td>
String</td><td>
The font name</td></tr>
<tr>
<td>
HeaderBorderColor</td><td>
System.Drawing.Color</td><td>
The border color of the grid header</td></tr>
<tr>
<td>
HeaderFontSize</td><td>
int</td><td>
The size of the grid header font</td></tr>
<tr>
<td>
GHeaderBgColor</td><td>
System.Drawing.Color</td><td>
The Column Header cell color and the Group Header Indent cell color</td></tr>
<tr>
<td>
ContentBgColor</td><td>
System.Drawing.Color</td><td>
The background color of the content</td></tr>
<tr>
<td>
ContentBorderColor</td><td>
System.Drawing.Color</td><td>
The border color of the grid content</td></tr>
<tr>
<td>
ContentFontSize</td><td>
int</td><td>
The font size of the grid content</td></tr>
<tr>
<td>
GContentFontColor</td><td>
System.Drawing.Color</td><td>
The font color of the record field cell</td></tr>
<tr>
<td>
GCaptionBorderColor</td><td>
System.Drawing.Color</td><td>
The border color of the group caption cell</td></tr>
<tr>
<td>
AltRowBgColor</td><td>
System.Drawing.Color</td><td>
The background color of the alternative row of the grid content</td></tr>
</table>


{% tabs %}
 
{% highlight razor %}

       <ej-grid id="FlatGrid" datasource="ViewBag.datasource" allow-paging="true" >
        <e-toolbar-settings show-toolbar="true" toolbar-items=@(new List<string>() {"excelExport","wordExport","pdfExport" }) >
           
        </e-toolbar-settings>
        <e-columns>
            <e-column field="OrderID" header-text="OrderID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="CustomerID"></e-column>
            <e-column field="EmployeeID" header-text="EmployeeID" text-align="Right"></e-column>
            <e-column field="ShipCity" header-text="Freight" text-align=Right></e-column>
            <e-column field="ShipCountry" header-text="Ship Country" text-align="Right"></e-column>
            <e-column field="Freight" header-text="Freight"></e-column>
        </e-columns>
    </ej-grid>

{% endhighlight %}
{% highlight c# %}

       public partial class GridController : Controller
    {

        private NORTHWNDContext _context;

        public GridController(NORTHWNDContext context)
        {
            _context = context;
        }
        // GET: /<controller>/
        public ActionResult Exporting()
        {
            ViewBag.datasource = _context.Orders.Take(100).ToList();
            return View();
        }
        public ActionResult ExportToExcel(string GridModel)
        {
            ExcelExport exp = new ExcelExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = ConvertGridObject(GridModel);
            GridExcelExport excelExp = new GridExcelExport();
            excelExp.FileName = "Export.xlsx"; excelExp.Excelversion = ExcelVersion.Excel2010;
            excelExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, excelExp);
        }

        public ActionResult ExportToWord(string GridModel)
        {
            WordExport exp = new WordExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = ConvertGridObject(GridModel);
            GridWordExport wrdExp = new GridWordExport();
            wrdExp.FileName = "Export.docx"; wrdExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, wrdExp);
        }
        public ActionResult ExportToPdf(string GridModel)
        {
            PdfExport exp = new PdfExport();
            var DataSource = _context.Orders.Take(100).ToList();
            GridProperties gridProp = ConvertGridObject(GridModel);
            GridPdfExport pdfExp = new GridPdfExport();
            pdfExp.FileName = "Export.pdf"; pdfExp.Theme = "flat-saffron";
            return exp.Export(gridProp, DataSource, pdfExp);
        }
        private GridProperties ConvertGridObject(string gridProperty)
        {
            GridProperties gridProp = (GridProperties)JsonConvert.DeserializeObject(gridProperty, typeof(GridProperties));

            GridExtensions ext = new GridExtensions();

            AutoFormat auto = new AutoFormat();

            ext.SetTheme(auto, "flat-saffron");


            auto.FontFamily = "Arial";


            auto.ContentBorderColor = new Syncfusion.JavaScript.Models.Color(165, 42, 42, "brown");

            auto.ContentFontSize = 10;

            auto.GCaptionBorderColor = new Syncfusion.JavaScript.Models.Color(255, 248, 220, "Cornsilk");

            auto.GContentFontColor = new Syncfusion.JavaScript.Models.Color(0, 0, 139, "DarkBlue");

            auto.HeaderFontSize = 12;

            auto.HeaderBorderColor = new Syncfusion.JavaScript.Models.Color(255, 0, 0, "Red");

            auto.ContentBgColor = new Syncfusion.JavaScript.Models.Color(245, 222, 179, "Wheat");

            auto.GHeaderBgColor = new Syncfusion.JavaScript.Models.Color(220, 20, 60, "Crimson");

            auto.AltRowBgColor = new Syncfusion.JavaScript.Models.Color(224, 255, 255, "LightCyan");

            gridProp.AutoFormat = auto;
            return gridProp;
        }
        public ActionResult ExportingGrid()

        {

            var DataSource = _context.Orders.Take(100).ToList();

            ViewBag.datasource = DataSource;

            return View();

        }
    }

{% endhighlight %}


{% endtabs %} 
![](Exporting_images/Customizing-Themes_img2.png)

## Exporting server events

`Exporting` feature supports server side event handler. You can handle server side event while exporting grid to various files such as Excel, PDF and Word. The various server side events available in Exporting and its argument types are listed in the following table.

<table>
<tr>
<th>
Event Name
</th>
<th>
Argument 
</th>
<th>
Description
</th>
</tr>
<tr>
<td>
ServerExcelQueryCellInfo
</td>
<td>
currentCell
</td>
<td>
It returns the current cell of excel sheet.
</td>
</tr>
<tr>
<td>
ServerExcelRowInfo
</td>
<td>
range
</td>
<td>
It returns the current row of excel sheet.
</td>
</tr>
<tr>
<td>
ServerWordQueryCellInfo
</td>
<td>
currentCell
</td>
<td>
It returns the current cell of word.
</td>
</tr>
<tr>
<td>
ServerWordRowInfo
</td>
<td>
range
</td>
<td>
It returns the current row of word.
</td>
</tr>
<tr>
<td>
ServerPdfQueryCellInfo
</td>
<td>
currentCell
</td>
<td>
It returns the current cell of PDF.
</td>
</tr>
<tr>
<td>
ServerPdfRowInfo
</td>
<td>
range
</td>
<td>
It returns the current row of PDF.
</td>
</tr>
</table>


You can customize the particular cell or particular  row of exporting files using server events. The code snippet for this is

{% tabs %}
 
{% highlight razor %}

    <ej-grid id="FlatGrid" datasource="ViewBag.datasource" allow-paging="true" >
        <e-toolbar-settings show-toolbar="true" toolbar-items=@(new List<string>() {"excelExport","wordExport","pdfExport" }) >
           
        </e-toolbar-settings>
        <e-columns>
            <e-column field="EmployeeID" header-text="Employee ID" text-align="Right"></e-column>
            <e-column field="CustomerID" header-text="Customer ID"></e-column>
            <e-column field="Freight" header-text="Freight" text-align="Right"></e-column>
            <e-column field="ShipCity" header-text="Ship City" text-align=Right></e-column>
            <e-column field="OrderDate" header-text="Order Date" text-align="Right"></e-column>
            <e-column field="ShipCountry" header-text="Ship Country"></e-column>
        </e-columns>
    </ej-grid> 

{% endhighlight %}
{% highlight c# %}

    public partial class GridController : Controller

    {

	public void ExportToExcel(string GridModel)
    {
            ExcelExport exp = new ExcelExport();
            var DataSource = new NorthwindDataContext().EmployeeViews.Take(100).ToList(); 
            GridProperties obj =(GridProperties)Syncfusion.JavaScript.Utils.DeserializeToModel(typeof(GridProperties), GridModel);
            obj.ServerExcelQueryCellInfo = QueryCellInfo;
            exp.Export(obj, DataSource, "Export.xlsx", ExcelVersion.Excel2010, false, false, "flat-saffron");
    }
    public void QueryCellInfo(object currentCell)
    {
            IRange range = (IRange)currentCell;
            if (range.Column==1 && int.Parse(range.Value) == 5)
                range.CellStyle.Color = Color.Red;
    } 
	public ActionResult ExportingGrid()
	{

		var DataSource = new NorthwindDataContext().OrdersViews.ToList();

		ViewBag.datasource = DataSource;

		return View();

	}

    }

{% endhighlight %}


{% endtabs %}

![](Exporting_images/Exporting_Serverside_Event.png)















