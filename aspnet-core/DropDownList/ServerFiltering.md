---
layout: post
title: Server Filtering in the DropDownList control for Syncfusion ASP.NET Core
description: Descripes about server filtering in the DropDownList control for Syncfusion ASP.NET Core
platform: aspnet-core
control: DropDownList
documentation: ug
keywords: DropDownList, dropdown, Server Filtering

---

# Server Filtering

Server filtering for displaying only a fixed amount of dataset from the whole dataset. In general, DropDownList displays just the data returned from the server. This feature is convenient for you to apply when the user does not want to see the whole dataset in the popup wrapper.
The property enable-server-filtering If set to true, the filtering operations performed in the remote service and returns the result.

{% highlight CSHTML %}

    <div class="ctrllabel">Select a Company Name</div>
    <ej-drop-down-list id="CompanyNames" width="100%" enable-filter-search="true" enable-server-filtering="true">
        <e-datamanager url="//js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Customers" cross-domain="true"></e-datamanager>
        <e-drop-down-list-fields text="ContactName" value="ContactName"/>
    </ej-drop-down-list>

{% endhighlight %}

![](ServerFiltering_images/ServerFiltering_image2.png)

This sample raises the query on Customer service. Returns ContactName records for customers with ContactName containing the string “d”.

![](ServerFiltering_images/ServerFiltering_image1.png)

