---
layout: post
title: Getting-Started | ReportWriter | ASP.NET Core | Syncfusion
description: getting started
platform: aspnet-core
control: ReportWriter
documentation: ug
---

# Overview

ReportWriter is a class library that enables the user to render reports defined in Microsoft’s RDL/RDLC format as PDF, Word and Excel documents. This section describes how to export the RDL report as PDF, Word and Excel formats in ASP.NET Core application using ReportWriter.


## Environment setup
Refer the [installation](/aspnet-core/installation) page to know more about the basic steps to configure the Syncfusion components to use with ASP.NET Core application. 

N> NuGet package reference will be more over referred from Syncfusion NuGet source for ASP.NET Core development to prepare the environment without installation, if you missed to explored then referred the [nuget-package-manager-settings](/aspnet-core/installation#nuget-package-manager-settings).

### References
You should add the following packages for the report viewer:

**Syncfusion.Report.NETStandard**: It is a base library for the **Syncfusion.EJ.ReportViewer.ASPNET.Core**  package.
**Syncfusion.Compression.NETStandard**: Supports for exporting the report to PDF, Microsoft Word, and Microsoft Excel format.
**Syncfusion.Pdf.NETStandard**: Supports for exporting the report to a PDF.
**Syncfusion.DocIO.NETStandard**: Supports for exporting the report to a Word.**Syncfusion.XlsIO.NETStandard**: Supports for exporting the report to an Excel.
**Syncfusion.OfficeChart.NETStandard**: It is a base library of the **Syncfusion.XlsIO.NETStandard** package.
**System.Data.SqlClient**: Renders the report to get the data from SQL Server if required. The package version should be higher of 4.1.0 and this is an optional package for the report viewer.
**Newtonsoft.Json**: Serializes and deserializes the data for report viewer client. It is a mandatory package for the report, and the package version should be higher of 10.0.1 for NET Core 2.0 and others should be higher of 9.0.1.

Find the package details in the following table, which is to be chosen based on the application target framework:

<table>
<tr>
<th>
Targeted Framework</th>
<th>
Packages
</th>
</tr>
<tr>
<td>.NET Core 2.0 </td>
<td>
Syncfusion.EJ.Report.NETStandard20<br/><br/>
Syncfusion.Compression.NETStandard20<br/><br/>
Syncfusion.Pdf.NETStandard20<br/><br/>
Syncfusion.DocIO.NETStandard20<br/><br/>
Syncfusion.XlsIO.NETStandard20<br/><br/>
Syncfusion.OfficeChart.NETStandard20
</td></tr>
<tr>
<td>
.NET Core 1.1 & .NET Core 1.0 </td>
<td>
Syncfusion.EJ.Report.NETStandard14<br/><br/>
Syncfusion.Compression.NETStandard14<br/><br/>
Syncfusion.Pdf.NETStandard14<br/><br/>
Syncfusion.DocIO.NETStandard14<br/><br/>
Syncfusion.XlsIO.NETStandard14<br/><br/>
Syncfusion.OfficeChart.NETStandard14
</td></tr>
<tr>
<td>
.NET Framework (>= 4.6.1) </td>
<td>
Syncfusion.EJ.Report.NETStandard14<br/><br/>
Syncfusion.Compression.NETStandard14<br/><br/>
Syncfusion.Pdf.NETStandard14<br/><br/>
Syncfusion.DocIO.NETStandard14<br/><br/>
Syncfusion.XlsIO.NETStandard14<br/><br/>
Syncfusion.OfficeChart.NETStandard14
</td></tr>
<tr>
<td>
.NET Framework (>= 4.5.1) </td>
<td>
Syncfusion.EJ.Report.NETStandard12<br/><br/>
Syncfusion.Compression.NETStandard12<br/><br/>
Syncfusion.Pdf.NETStandard12<br/><br/>
Syncfusion.DocIO.NETStandard12<br/><br/>
Syncfusion.XlsIO.NETStandard12<br/><br/>
Syncfusion.OfficeChart.NETStandard12
</td>
</tr>
</table>


## Add ReportWriter option in CSHTML page

Add the following code example in the CSHTML page to view ReportWriter export options.

{% highlight CSHTML %}
@{Html.BeginForm("Pdf", "Home", FormMethod.Post);
    {
<div>
    <input name="invoiceId" value="10255" style="width: 150px;" />
    <input type="submit" value="Generate PDF" style="width: 150px;" />

</div>
        }
        Html.EndForm();
    }

{% endhighlight %}


## Add the ReportWriter code in controller class
You should inherit the IReportController interface to build the report viewer compatible Web API, and the ReportHelper should be used with IReportController interface implemented methods. The ReportHelper will perform the server-side related process and will return the required data for the ReportViewer to process the rendering. Here, the sample code is provided with an MVC application to build the Web API service along with the existing controller.

{% highlight C# %}
public class HomeController : Controller
    {
        // IHostingEnvironment used with sample to get the application data from wwwroot.
        private Microsoft.AspNetCore.Hosting.IHostingEnvironment _hostingEnvironment;

        // IHostingEnvironment initialized with controller to get the data from application data folder.
        public HomeController(Microsoft.AspNetCore.Hosting.IHostingEnvironment hostingEnvironment)
        {
            _hostingEnvironment = hostingEnvironment;
        }

[HttpPost]
        public IActionResult Pdf()
        {

            string basePath = _hostingEnvironment.WebRootPath;
            // Here, we have loaded the sample report report from application the folder wwwroot. 
            // Invoice.rdl should be there in wwwroot application folder.
            FileStream inputStream = new FileStream(basePath + @"\Invoice.rdl", FileMode.Open, FileAccess.Read);
            Syncfusion.ReportWriter.ReportWriter writer = new Syncfusion.ReportWriter.ReportWriter(inputStream);

            // Assigning the report parameter based on selected value from user.
            string invoiceID = this.HttpContext.Request.Form["invoiceId"].ToString();

            List<Syncfusion.Report.ReportParameter> parameters = new List<Syncfusion.Report.ReportParameter>();
            Syncfusion.Report.ReportParameter param = new Syncfusion.Report.ReportParameter();
            param.Name = "InvoiceID";
            param.Values = new List<string>() { invoiceID };
            parameters.Add(param);
            writer.SetParameters(parameters);

            // Steps to generate PDF report using Report Writer.
            MemoryStream memoryStream = new MemoryStream();
            writer.Save(memoryStream, Syncfusion.ReportWriter.WriterFormat.PDF);

            // Download the generated from client.
            memoryStream.Position = 0;
            FileStreamResult fileStreamResult = new FileStreamResult(memoryStream, "application/pdf");
            fileStreamResult.FileDownloadName = "Invoice.pdf";
            return fileStreamResult;
        }
}

{% endhighlight %}

N> You cannot load the application report with path information in ASP.NET Core. So, you should load the report with report stream as like an example provided above in OnInitReportOptions. If you need to get the invoice sample report then you can obtain it from the Syncfusion ASP.NET Core sample browser installed location (wwwroot\reports\invoice.rdl).
