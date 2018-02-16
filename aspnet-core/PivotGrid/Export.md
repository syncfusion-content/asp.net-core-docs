---
layout: post
title: Exporting
description: exporting
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Exporting

The PivotGrid control can be exported to the following file formats.

* Excel
* Word
* PDF

The PivotGrid control can be exported by invoking **“exportPivotGrid”** method, with an appropriate export option as parameter.

## JSON Export

{% highlight CSHTML %}

    <ej-pivot-grid id="PivotGrid1" is-responsive="true" load="onload">
        <e-data-source>
            <e-pivot-rows>
                <e-row-field field-name="Country" field-caption="Country"></e-row-field>
            </e-pivot-rows>
            <e-pivot-columns>
                <e-column-field field-name="Date" field-caption="Date"></e-column-field>
            </e-pivot-columns>
            <e-pivot-values>
                <e-value-field field-name="Amount" field-caption="Amount"></e-value-field>
            </e-pivot-values>
        </e-data-source>
    </ej-pivot-grid>

    <ej-button id="ExportBtn" width="100px" height="30px" type="Button" text="Export" click="exportBtnClick" />

  <script type="text/javascript">

        function exportBtnClick(args) {
            var pGridObj = $('#PivotGrid1').data("ejPivotGrid");
            pGridObj.exportPivotGrid("ExcelExport","fileName");
        }

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

To achieve exporting, we need to add **"Syncfusion.EJ.Export"** dependency library into the application.

When PivotGrid is rendered, a method needs to be added in MVC controller file of the application and we need to import **"Syncfusion.EJ.Export"** namespace in the controller file. 

{% highlight c# %}

        //...
        using Syncfusion.EJ.Export;

        private IHttpContextAccessor _contextAccessor;

        public PivotGridController(IHttpContextAccessor contextAccessor, IHostingEnvironment envrnmt)
        {
            _contextAccessor = contextAccessor;
        }

        public ActionResult ExcelExport()
        {
            PivotGridExcelExport pGrid = new PivotGridExcelExport();
            var context = _contextAccessor.HttpContext;
            var args = context.Request.Form.ElementAt(0).Value;
            string fileName = "Sample";
            return pGrid.ExportToExcel(fileName, args, context.Response);
        }
        
{% endhighlight %}

### Excel Export

User can export the contents of PivotGrid to an Excel document for future archival, references and analysis purposes.

To achieve Excel export, the controller method name **"ExcelExport"** and file name is sent as the parameter.

{% highlight js %}

   <script type="text/javascript">

       function exportBtnClick(args)
       {
          var pGridObj = $('#PivotGrid1').data("ejPivotGrid");
          pGridObj.exportPivotGrid("ExcelExport","fileName");
       }

   </script>
    
{% endhighlight %}  

Following method needs to be added in controller file of the application.

{% highlight c# %}

        public ActionResult ExcelExport()
        {
            PivotGridExcelExport pGrid = new PivotGridExcelExport();
            var context = _contextAccessor.HttpContext;
            var args = context.Request.Form.ElementAt(0).Value;
            string fileName = "Sample";
            return pGrid.ExportToExcel(fileName, args, context.Response);
        }

{% endhighlight %}

### Word Export
User can export the contents of PivotGrid to a Word document for future archival, references and analysis purposes.

To achieve Word export, controller method name **"WordExport"** and file name is sent as the parameter.

{% highlight js %}

   <script type="text/javascript">

       function exportBtnClick(args)
       {
          var pGridObj = $('#PivotGrid1').data("ejPivotGrid");
          pGridObj.exportPivotGrid("WordExport","fileName");
       }

   </script>
    
{% endhighlight %}  

Following method needs to be added in controller file of the application.

{% highlight c# %}

        public ActionResult WordExport()
        {
            PivotGridWordExport pGrid = new PivotGridWordExport();
            var context = _contextAccessor.HttpContext;
            var args = context.Request.Form.ElementAt(0).Value;
            string fileName = "Sample";
            return pGrid.ExportToWord(fileName, args, context.Response);
        }

{% endhighlight %}

### PDF Export

User can export contents of the PivotGrid to PDF document for future archival, references and analysis purposes.

To achieve Word export, controller method name **"PDFExport"** and file name is sent as the parameter.

{% highlight js %}

   <script type="text/javascript">

       function exportBtnClick(args)
       {
          var pGridObj = $('#PivotGrid1').data("ejPivotGrid");
          pGridObj.exportPivotGrid("PDFExport","fileName");
       }

   </script>
    
{% endhighlight %}  

Following method needs to be added in MVC controller file of the application.

{% highlight c# %}

        public ActionResult PDFExport()
        {
            PivotGridPDFExport pGrid = new PivotGridPDFExport();
            var context = _contextAccessor.HttpContext;
            var args = context.Request.Form.ElementAt(0).Value;
            string fileName = "Sample";
            return pGrid.ExportToPDF(fileName, args, context.Response);
        }      

{% endhighlight %}


### Customize the export document name

For customizing file name, we need to send file name as parameter to the **“exportPivotGrid”**  method along with method name.

{% highlight js %}

function exportBtnClick(args)
{
    var pGridObj = $('#PivotGrid1').data("ejPivotGrid");
    pGridObj.exportPivotGrid("ExcelExport","fileName");
}

{% endhighlight %}

The below screenshot shows the PivotGrid control exported to Excel document.

![](Exporting_images/ExportOLAPExcel.png)

The below screenshot shows the PivotGrid control exported to Word document.

![](Exporting_images/ExportOLAPWord.png)

The below screenshot shows the PivotGrid control exported to PDF document.

![](Exporting_images/ExportOLAPPDF.png)


