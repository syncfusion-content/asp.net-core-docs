---
layout: post
title: Save and Load Report
description: save and load report
platform: aspnet-core
control: PivotClient
documentation: ug
---

# Save and Load Report

Save and load report allows you to save the current report collection of PivotClient and render the control later on loading the same.

We can save and load the report in two ways.

* Database
* Local Storage

## Save Report to Database

We can store the report collection of PivotClient to database, by using the `save-report` event in PivotClient.

N> By default, we are using our online hosted URL link for saving the report to Database. If you have installed Essential Studio, then you can provide the URL link by hosting “ejServices” in IIS. “ejServices” folder is available in the below installed location.  
Location:  $system drive:\Users\$UserName#\AppData\Local\Syncfusion\EssentialStudio\$Version# \JavaScript\ejservices 
Eg: C:\Users\UserName\AppData\Local\Syncfusion\EssentialStudio\{{ site.releaseversion }}\JavaScript\ejservices

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" save-report="saveReportSettings">
      //..
</ej-pivot-client>

<script>
    function saveReportSettings(args) {
        if(args.saveReportSettings)
            return args.saveReportSetting.url = "http://js.syncfusion.com/ejservices/api/PivotClient/Olap"; //You can provide the hosted URL link to save report in DB here.
    }
</script>

{% endhighlight %}

## Save Report to Local Storage

We can store the report collection of PivotClient to local storage, by setting the `enable-local-storage` property to true and by defining the `save-report` event of PivotClient.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" save-report="saveReportSettings" enable-local-storage="true">
      //..
</ej-pivot-client>

<script>
    function saveReportSettings(args) {
        var reportCollection = [];
        if ((localStorage.pivotClientRPTCollection != "" && !ej.isNullOrUndefined(localStorage.pivotClientRPTCollection))) {
            reportCollection = JSON.parse(localStorage.pivotClientRPTCollection);
        }
        if(args.saveReportSettings){
            reportCollection.push(({ reportName: args.saveReportSetting.reportName, reportCol: args.saveReportSetting.reportCollection }));
            localStorage.pivotClientRPTCollection = JSON.stringify(reportCollection);;
        }
    }
</script>

{% endhighlight %}

## Load Report from Database

We can load the stored report collection of PivotClient from database, by using the `fetch-report`  and `load-report` events in PivotClient.

N> By default, we are using our online hosted URL link to fetch and load the report from Database. If you have installed Essential Studio, then you can provide the URL link by hosting “ejServices” in IIS. “ejServices” folder is available in the below installed location.  
Location:  $system drive:\Users\$UserName#\AppData\Local\Syncfusion\EssentialStudio\$Version# \JavaScript\ejservices 
Eg: C:\Users\UserName\AppData\Local\Syncfusion\EssentialStudio\{{ site.releaseversion }}\JavaScript\ejservices

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" load-report="reportSettings" fetch-report="reportSettings">
//..
</ej-pivot-client>

<script>
    function reportSettings(args) {
        
        if (args.fetchReportSetting)
            return args.fetchReportSetting.url = "http://js.syncfusion.com/ejservices/api/PivotClient/Olap";//you can provide the hosted url link to fetch report from DB here

        else if (args.loadReportSetting)
            return args.loadReportSetting.url = "http://js.syncfusion.com/ejservices/api/PivotClient/Olap";//you can provide the hosted url link to load report from DB here
    }
</script>
{% endhighlight %}

## Load Report from Local Storage

We can load the stored report collection of PivotClient from local storage, by setting the `enable-local-storage` property to true and using the `load-report` and `fetch-report` events in PivotClient.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" load-report="reportSettings" fetch-report="reportSettings" enable-local-storage="true">
//..
</ej-pivot-client>

<script>
    function reportSettings(args) {
        var reportCollection = [];
        if ((localStorage.pivotClientRPTCollection != "" && !ej.isNullOrUndefined(localStorage.pivotClientRPTCollection))) {
            reportCollection = JSON.parse(localStorage.pivotClientRPTCollection);
        }
        if (args.fetchReportSetting) 
            args.fetchReportSetting.reportList = $.map(reportCollection, function (item, index) { return item.reportName; }).join("__");
        else if (args.loadReportSetting) 
            args.loadReportSetting.reportCollection = $.map(reportCollection, function (item, index) { if (item.reportName == args.loadReportSetting.selectedReport) return item.reportCol; });
    }
</script>
{% endhighlight %}