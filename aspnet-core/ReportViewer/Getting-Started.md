---
layout: post
title: Getting-Started | ReportViewer | ASP.NET Core | Syncfusion
description: getting started
platform: aspnet-core
control: ReportViewer
documentation: ug
---

# Overview

The ReportViewer is a visualization control to view the Microsoft RDL/RDLC format based report on a web page and it is powered by HTML5/JavaScript. This section explains how to add the ReportViewer component in ASP.NET Core MVC application along with simple example of display the invoice report from ASP.Core applcation. 

N> Report Viewer control depdents the server side processing for report rendering. So, we should build the WebAPI service that compatible for report viewer. You can learn in this topic how can create the report viewer compatible WebApi Service with your application.

## Environment Setup

Refer the [Getting Started](/aspnet-core/getting-started) page of the Introduction part to know more about the basic system requirements and the steps to configure the Syncfusion components in an ASP.NET Core application.

### Styles and Scripts

Ensure once whether all the necessary dependency scripts and style packages are included within the *bower.json* file as mentioned [here](/aspnet-core/getting-started#configure-syncfusion-components-in-aspnet-core-application), so that the required scripts and CSS gets installed and loads into the mentioned location (**wwwroot -> lib**) within your project.

Now, refer the necessary scripts and CSS files into your *_Layout.cshtml* page from the **wwwroot -> lib -> syncfusion-javascript** folder.

{% highlight cshtml %}
<!DOCTYPE html>
<html>
<head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>@ViewData["Title"] - ReportViewerDemo</title>

    <environment include="Development">
        <link rel="stylesheet" href="~/lib/bootstrap/dist/css/bootstrap.css" />
        <link rel="stylesheet" href="~/css/site.css" />

        <link href="~/lib/syncfusion-javascript/Content/ej/web/default-theme/ej.web.all.min.css" rel="stylesheet" />
        <link href="~/lib/syncfusion-javascript/Content/ej/web/responsive-css/ej.responsive.css" rel="stylesheet" />

    </environment>
    <environment exclude="Development">
        <link rel="stylesheet" href="https://ajax.aspnetcdn.com/ajax/bootstrap/3.3.7/css/bootstrap.min.css"
              asp-fallback-href="~/lib/bootstrap/dist/css/bootstrap.min.css"
              asp-fallback-test-class="sr-only" asp-fallback-test-property="position" asp-fallback-test-value="absolute" />
        <link rel="stylesheet" href="~/css/site.min.css" asp-append-version="true" />

        <link href="~/lib/syncfusion-javascript/Content/ej/web/default-theme/ej.web.all.min.css" rel="stylesheet" />
        <link href="~/lib/syncfusion-javascript/Content/ej/web/responsive-css/ej.responsive.css" rel="stylesheet" />

    </environment>
</head>
<body>
    <nav class="navbar navbar-inverse navbar-fixed-top">
        <div class="container">
            <div class="navbar-header">
                <button type="button" class="navbar-toggle" data-toggle="collapse" data-target=".navbar-collapse">
                    <span class="sr-only">Toggle navigation</span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                    <span class="icon-bar"></span>
                </button>
                <a asp-area="" asp-controller="Home" asp-action="Index" class="navbar-brand">ReportViewerDemo</a>
            </div>
            <div class="navbar-collapse collapse">
                <ul class="nav navbar-nav">
                    <li><a asp-area="" asp-controller="Home" asp-action="Index">Home</a></li>
                    <li><a asp-area="" asp-controller="Home" asp-action="About">About</a></li>
                    <li><a asp-area="" asp-controller="Home" asp-action="Contact">Contact</a></li>
                </ul>
            </div>
        </div>
    </nav>
    <div class="container body-content">
        @RenderBody()
        <hr />
        <footer>
            <p>&copy; 2018 - ReportViewerDemo</p>
        </footer>
    </div>

    <environment include="Development">
        <script src="~/lib/jquery/dist/jquery.js"></script>
        <script src="~/lib/bootstrap/dist/js/bootstrap.js"></script>
        <script src="~/js/site.js" asp-append-version="true"></script>

        <script src="~/lib/syncfusion-javascript/Scripts/jsrender.min.js"></script>
        <script src="~/lib/syncfusion-javascript/Scripts/ej/web/ej.web.all.min.js"></script>

    </environment>
    <environment exclude="Development">
        <script src="https://ajax.aspnetcdn.com/ajax/jquery/jquery-2.2.0.min.js"
                asp-fallback-src="~/lib/jquery/dist/jquery.min.js"
                asp-fallback-test="window.jQuery"
                crossorigin="anonymous"
                integrity="sha384-K+ctZQ+LL8q6tP7I94W+qzQsfRV2a+AfHIi9k8z8l9ggpc8X+Ytst4yBo/hH+8Fk">
        </script>
        <script src="https://ajax.aspnetcdn.com/ajax/bootstrap/3.3.7/bootstrap.min.js"
                asp-fallback-src="~/lib/bootstrap/dist/js/bootstrap.min.js"
                asp-fallback-test="window.jQuery && window.jQuery.fn && window.jQuery.fn.modal"
                crossorigin="anonymous"
                integrity="sha384-Tc5IQib027qvyjSMfHjOMaLkfuWVxZxUPnCJA7l2mCWNIpG9mGCD8wGNIcPD7Txa">
        </script>
        <script src="~/js/site.min.js" asp-append-version="true"></script>

        <script src="~/lib/syncfusion-javascript/Scripts/jsrender.min.js"></script>
        <script src="~/lib/syncfusion-javascript/Scripts/ej/web/ej.web.all.min.js"></script>

    </environment>

    @RenderSection("Scripts", required: false)

    <ej-script-manager/>
</body>
</html>
{% endhighlight %}

N> Script manager (<ej-script-manager/>) must be defined at the bottom of the *_Layout.cshtml* page.

### References
We have added the following packages for ReportViewer,

    * **Syncfusion.EJ** - It is required for to build the ReportViewer controls with Tag helper.
    * **Syncfusion.EJ.ASPNET.Core** - It is required for to build the ReportViewer controls with Tag helper.
    * **Syncfusion.EJ.ReportViewer.ASPNET.Core** - It is required to build the server side implementations.
    * **Syncfusion.Report.NETStandard** - It is base library for **Syncfusion.EJ.ReportViewer.ASPNET.Core**  package.
    * **Syncfusion.Compression.NETStandard** - It is required to support the export the report with PDF, Word and Excel.
    * **Syncfusion.Pdf.NETStandard** - It is required to support the export the report with PDF.
    * **Syncfusion.DocIO.NETStandard** - It is required to support the export the report with Word.
    * **Syncfusion.XlsIO.NETStandard** - It is required to support the export the report with Excel.
    * **Syncfusion.OfficeChart.NETStandard** - It is base library of **Syncfusion.XlsIO.NETStandard** package.
    * **System.Data.SqlClient** - It is required render the report if has the Report need to get the data from SQL Server and  the package version should  be higher of 4.1.0. This is an optional package for ReportViewer.
    * **Newtonsoft.Json** - It is used to send to serialize and deserializethe data for report viewer client. It is maniotry  package for Report and package version should higher of 10.0.1 for NET Core 2.0 for other that should be higher of 9.0.1.

Find the package details in below table what need to be chosen based on application Target Framework,

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
<td>Syncfusion.EJ<br/><br/>
Syncfusion.EJ.ASPNET.Core<br/><br/>
Syncfusion.EJ.ReportViewer.ASPNET.Core<br/><br/>
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
<td>Syncfusion.EJ<br/><br/>
Syncfusion.EJ.ASPNET.Core<br/><br/>
Syncfusion.EJ.ReportViewer.ASPNET.Core<br/><br/>
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
<td>Syncfusion.EJ<br/><br/>
Syncfusion.EJ.ASPNET.Core<br/><br/>
Syncfusion.EJ.ReportViewer.ASPNET.Core<br/><br/>
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
<td>Syncfusion.EJ<br/><br/>
Syncfusion.EJ.ASPNET.Core<br/><br/>
Syncfusion.EJ.ReportViewer.ASPNET.Core<br/><br/>
Syncfusion.EJ.Report.NETStandard12<br/><br/>
Syncfusion.Compression.NETStandard12<br/><br/>
Syncfusion.Pdf.NETStandard12<br/><br/>
Syncfusion.DocIO.NETStandard12<br/><br/>
Syncfusion.XlsIO.NETStandard12<br/><br/>
Syncfusion.OfficeChart.NETStandard12
</td>
</tr>
</table>

### Tag helper
It is necessary to define the following namespace within the *_viewImports.cshtml* page in order to initialize the ReportViewer component with the tag helper support.

{% highlight cshtml %}

    @addTagHelper *, Microsoft.AspNetCore.Mvc.TagHelpers
    @using Syncfusion.JavaScript
    @addTagHelper "*, Syncfusion.EJ"

{% endhighlight %}

## Add Control with page

We have to use <ej-report-viewer> tag to add the report viewer control. For an example, Index.cshtml page replaced with following code by removing existing codes to add the report viewer. 

{% highlight CSHTML %}
@{
    ViewData["Title"] = "Home Page";
}

<div style="height: 525px;width: 100%;">
    <ej-report-viewer id="reportviewer1" report-service-url="../Home" />
</div>

N> As stated in the beginning itself, we need WebApi service to process the report from server. The service should be mapped with report viewer report-service-url as like the example code available above of this note.

{% endhighlight %}

## Build WebApi Service
We should to inhertied the IReportController interface to build the report viewer compatible Web API and ReportHelper should used with IReportController interface implemented methods. ReportHelper will do the server side related process and will return the required data for the ReportViewer to process the rendering. Here, the sample code provided with MVC application to build the Web API service along with existing controller.

{% highlight C# %}

using System.Collections.Generic;
using Microsoft.AspNetCore.Mvc;

namespace ReportViewerDemo.Controllers
{
    public class HomeController : ApiController, Syncfusion.EJ.ReportViewer.IReportController
    {
        // Reportviewer requires a memory cache to store the information of consecutive client request and
        // have the rendered report viewer information in server.
        private Microsoft.Extensions.Caching.Memory.IMemoryCache _cache;

        // IHostingEnvironment used with sample to get the application data from wwwroot.
        private Microsoft.AspNetCore.Hosting.IHostingEnvironment _hostingEnvironment;

        // Post action to process the report from server based json parameters and send the result back to the client.
        public HomeController(Microsoft.Extensions.Caching.Memory.IMemoryCache memoryCache, 
            Microsoft.AspNetCore.Hosting.IHostingEnvironment hostingEnvironment)
        {
            _cache = memoryCache;
            _hostingEnvironment = hostingEnvironment;
        }

        public IActionResult Index()
        {
            return View();
        }

        ...
        ...
        ...

        // Post action to process the report from server based json parameters and send the result back to the client.
        public object PostReportAction([FromBody] Dictionary<string, object> jsonArray)
        {
            return Syncfusion.EJ.ReportViewer.ReportHelper.ProcessReport(jsonArray, this, this._cache);
        }

        // Method will be called to initialize the report information to load the report with ReportHelper for processing.
        public void OnInitReportOptions(Syncfusion.EJ.ReportViewer.ReportViewerOptions reportOption)
        {
            string basePath = _hostingEnvironment.WebRootPath;
            // Here, we have loaded the sample report report from application the folder wwwroot. Sample.rdl should be there in wwwroot application folder.
            FileStream reportStream = new FileStream(basePath + @"\invoice.rdl", FileMode.Open, FileAccess.Read);
            reportOption.ReportModel.Stream = reportStream;
        }

        // Method will be called when reported is loaded with internally to start to layout process with ReportHelper.
        public void OnReportLoaded(Syncfusion.EJ.ReportViewer.ReportViewerOptions reportOption)
        {
        }
        
        //Get action for getting resources from the report
        [System.Web.Http.ActionName("GetResource")]
        [AcceptVerbs("GET")]
        // Method will be called from Report Viewer client to get the image src for Image report item.
        public object GetResource(Syncfusion.EJ.ReportViewer.ReportResource resource)
        {
            return Syncfusion.EJ.ReportViewer.ReportHelper.GetResource(resource, this, _cache);
        }
    }
}

{% endhighlight %}

N> We dont have option to load the application Report with path information in ASP.NET Core. So, we should load the report with report stream as like an example provided above in  OnInitReportOptions. If you like to get the invoice sample report then you can obtained from Syncfusion ASP.NET Core sample browser installed location (wwwroot\reports\invoice.rdl)

## Run the Application

Run the sample application and you can see the ReportViewer on the page as displayed with Invoice as in the following screenshot.

![](images/reportviewergettingstarted.png)