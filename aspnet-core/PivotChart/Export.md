---
layout: post
title: Exporting
description: export
platform: aspnet-core
control: PivotChart
documentation: ug
---

# Exporting

The PivotChart control can be exported to the following file formats.

* Excel
* Word
* PDF
* Image

The PivotChart control can be exported by invoking **“exportPivotChart”** method, with an appropriate export option as parameter.

{% highlight CSHTML %}

    <ej-pivot-chart id="PivotChart1" is-responsive="true" load="onload" pre-render="preRender">
        <e-data-source>
            <e-pivot-rows>
                <e-row-field field-name="Product" field-caption="Product"></e-row-field>
                <e-row-field field-name="Date" field-caption="Date"></e-row-field>
            </e-pivot-rows>
            <e-pivot-columns>
                <e-column-field field-name="Country" field-caption="Country"></e-column-field>
            </e-pivot-columns>
            <e-pivot-values>
                <e-value-field field-name="Amount" field-caption="Amount"></e-value-field>
            </e-pivot-values>
        </e-data-source>
        <e-common-series-options type="Column" enable-animation="true">
            <e-chart-tooltip visible="true"></e-chart-tooltip>
        </e-common-series-options>
        <e-size width="100%" height="460px"></e-size>
        <e-primary-x-axis>
            <e-title text="Date - Fiscal"></e-title>
        </e-primary-x-axis>
        <e-primary-y-axis>
            <e-title text="Amount"></e-title>
        </e-primary-y-axis>
        <e-legend row-count="1"></e-legend>
    </ej-pivot-chart>

    <ej-button id="ExportBtn" width="100px" height="30px" type="Button" text="Export" click="exportBtnClick" />

  <script type="text/javascript">

        function exportBtnClick(args) {
            var PivotChartObj = $('#PivotChart1').data("ejPivotChart");
            var ChartObj = $("#" + PivotChartObj._id + "Container").data("ejChart");
            ChartObj.model.border.opacity = 1;
            ChartObj.redraw();
            PivotChartObj.exportPivotChart("ExportToExcel", "Sample", ej.PivotChart.ExportOptions.Excel);
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
            loadTheme(args);
        }
   </script>
    
{% endhighlight %}

To achieve exporting, we need to add **"Syncfusion.EJ.Export"** dependency library into the application.

When PivotChart is rendered, a method needs to be added in MVC controller file of the application and we need to import **"Syncfusion.EJ.Export"** namespace in the controller file. 

{% highlight c# %}

        private IHttpContextAccessor _contextAccessor;
        
        public PivotChartController(IHttpContextAccessor contextAccessor, IHostingEnvironment envrnmt)
        {
            _contextAccessor = contextAccessor;
        }

        public ActionResult ExportToExcel()
        {
            PivotChartExcelExport pivotChart = new PivotChartExcelExport();
            var context = _contextAccessor.HttpContext;
            var args = context.Request.Form.ElementAt(0).Value;
            Dictionary<string, string> clientParams = JsonConvert.DeserializeObject<Dictionary<string, string>>(args);
            clientParams["fileName"] = "sample";
            return pivotChart.ExportToExcel(clientParams);
        }
        
{% endhighlight %}

## Excel Export

User can export contents of the PivotChart to Excel document for future archival, references and analysis purposes.

To achieve Excel export, method name **"ExportToExcel"** and file name is sent as the parameter.

{% highlight js %}

   <script type="text/javascript">

       function exportBtnClick(args) {
            var PivotChartObj = $('#PivotChart1').data("ejPivotChart");
            var ChartObj = $("#" + PivotChartObj._id + "Container").data("ejChart");
            ChartObj.model.border.opacity = 1;
            ChartObj.redraw();
            PivotChartObj.exportPivotChart("ExportToExcel", "Sample", ej.PivotChart.ExportOptions.Excel);
        }

   </script>
    
{% endhighlight %}  

Following method need to be added in controller file of the application.

{% highlight c# %}

        public ActionResult ExportToExcel()
        {
            PivotChartExcelExport pivotChart = new PivotChartExcelExport();
            var context = _contextAccessor.HttpContext;
            var args = context.Request.Form.ElementAt(0).Value;
            Dictionary<string, string> clientParams = JsonConvert.DeserializeObject<Dictionary<string, string>>(args);
            clientParams["fileName"] = "sample";
            return pivotChart.ExportToExcel(clientParams);
        }

{% endhighlight %}

## Word Export
User can export contents of the PivotChart to Word document for future archival, references and analysis purposes.

To achieve Word export, method name **"ExportToWord"** and file name is sent as the parameter.

{% highlight js %}

   <script type="text/javascript">

       function exportBtnClick(args) {
            var PivotChartObj = $('#PivotChart1').data("ejPivotChart");
            var ChartObj = $("#" + PivotChartObj._id + "Container").data("ejChart");
            ChartObj.model.size.width = "700px";
            ChartObj.redraw();
            PivotChartObj.exportPivotChart("ExportToWord", "Sample", ej.PivotChart.ExportOptions.Word);
            ChartObj.model.size.width = "100%";
            ChartObj.redraw();
        }

   </script>
    
{% endhighlight %}  

Following method need to be added in controller file of the application.

{% highlight c# %}

        public ActionResult ExportToWord()
        {
            PivotChartWordExport pivotChart = new PivotChartWordExport();
            var context = _contextAccessor.HttpContext;
            var args = context.Request.Form.ElementAt(0).Value;
            Dictionary<string, string> clientParams = JsonConvert.DeserializeObject<Dictionary<string, string>>(args);
            clientParams["fileName"] = "sample";
            return pivotChart.ExportToWord(clientParams);
        }

{% endhighlight %}

## PDF Export

User can export contents of the PivotChart to PDF document for future archival, references and analysis purposes.

To achieve PDF export, method name **"ExportToPDF"** and file name is sent as the parameter.

{% highlight js %}

   <script type="text/javascript">

       function exportBtnClick(args) {
            var PivotChartObj = $('#PivotChart1').data("ejPivotChart");
            var ChartObj = $("#" + PivotChartObj._id + "Container").data("ejChart");
            ChartObj.model.size.width = "500px";
            ChartObj.redraw();
            PivotChartObj.exportPivotChart("ExportToPDF", "Sample", ej.PivotChart.ExportOptions.PDF);
            ChartObj.model.size.width = "100%";
            ChartObj.redraw();
        }

   </script>
    
{% endhighlight %}  

Following method need to be added in controller file of the application.

{% highlight c# %}

        public ActionResult ExportToPDF()
        {
            PivotChartPDFExport pivotChart = new PivotChartPDFExport();
            var context = _contextAccessor.HttpContext;
            var args = context.Request.Form.ElementAt(0).Value;
            Dictionary<string, string> clientParams = JsonConvert.DeserializeObject<Dictionary<string, string>>(args);
            clientParams["fileName"] = "sample";
            return pivotChart.ExportToPDF(clientParams);
        }      

{% endhighlight %}

## Image Export
User can export contents of the PivotChart to image format for future archival, references and analysis purposes. We can export PivotChart to the following image formats.

* PNG
* EMF
* JPG
* GIF
* BMP

To achieve image export, method name **"ExportToImage"** ,**“ej.PivotChart.ExportOptions.PNG”** and file name is sent as the parameter.This is similar to other image formats.

{% highlight js %}

   <script type="text/javascript">

       function exportBtnClick(args) {
            var PivotChartObj = $('#PivotChart1').data("ejPivotChart");
            var ChartObj = $("#" + PivotChartObj._id + "Container").data("ejChart");
            ChartObj.model.border.opacity = 1;
            ChartObj.redraw();
            PivotChartObj.exportPivotChart("ExportToImage", "Sample", ej.PivotChart.ExportOptions.PNG);
        }

        function preRender(sender) {
            if (sender.model.theme.indexOf("light") > -1 || sender.model.theme == "bootstrap" || sender.model.theme == "material") {
                sender.model.background = "white";
                sender.model.chartArea.background = "white";
            }
            else {
                sender.model.background = "black";
                sender.model.chartArea.background = "black"
            }
        }

   </script>
    
{% endhighlight %}  

Following method need to be added in controller file of the application.

{% highlight c# %}

        static string path = "E:\\";

        public void ExportToImage()
        {
            PivotChartImageExport pivotChart = new PivotChartImageExport();
            var context = _contextAccessor.HttpContext;
            var args = context.Request.Form.ElementAt(0).Value;
            Dictionary<string, string> clientParams = JsonConvert.DeserializeObject<Dictionary<string, string>>(args);
            clientParams.Add("Path", path);
            clientParams["fileName"] = "sample";
            pivotChart.ExportToImage(clientParams);
        }

{% endhighlight %}

The below screenshot shows the PivotChart control exported to Excel document.

![](Export_images/Export_ExcelClient.png)

The below screenshot shows the PivotChart control exported to PDF document.

![](Export_images/Export_PDFClient.png)

The below screenshot shows the PivotChart control exported to Word document.

![](Export_images/Export_WordClient.png)

The below screenshot shows the PivotChart control exported to PNG format.

![](Export_images/Export_PNGClient.png)