---
layout: post
title: Getting Started | ASP.NET Core | Syncfusion
description: Getting Started.
platform: aspnet-core 
control: Kanban 
documentation: ug
---

# Getting Started

Refer the [Getting Started](/aspnet-core/getting-started) page of the Introduction part to know more about the basic system requirements and the steps to configure the Syncfusion components in an ASP.NET Core application.

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

It is necessary to define the following namespace within the *_viewImports.cshtml* page in order to make use of the Kanban component with the tag helper support.
 
{% highlight cshtml %}
 
    @using Syncfusion.JavaScript
    @addTagHelper "*, Syncfusion.EJ"
    
{% endhighlight %}

N> Script manager must be defined at the bottom of the *_Layout.cshtml* page. 

## Data Binding

You can bind the data to Kanban control by either locally or remotely. Assign the remote service URL to `e-datamanager` property of Kanban control to bind remote data using `ej.DataManager`.

{% highlight CSHTML %}

    <ej-kanban id="KanbanBoard">
        <e-datamanager url="//mvc.syncfusion.com/Services/Northwnd.svc/Tasks"></e-datamanager> 
        <e-kanbancolumns>
            <e-kanbancolumn header-text="Backlog"></e-kanbancolumn>
            <e-kanbancolumn header-text="In Progress"></e-kanbancolumn>
            <e-kanbancolumn header-text="Testing"></e-kanbancolumn>      
        </e-kanbancolumns>
    </ej-kanban>


{% endhighlight  %}

![](getting-started-images/Kanban_img.png)

## Mapping Values

In order to display cards in Kanban control, you need to map the database fields to Kanban cards and ` e-kanbancolumn`. The required mapping field are listed as follows
*	`key-field ` -  Map the column name to use as `key` values to columns.
*	`e-kanbancolumn`- Map the corresponding `key` values of `key-field` column to each columns
*	`content` - Map the column name to use as content to cards in the Fields.
*	`primary-key`- Map the column name to use as Primary Key in Fields.


{% highlight CSHTML %}

    <ej-kanban id="KanbanBoard" key-field="Status">
        <e-datamanager url="//mvc.syncfusion.com/Services/Northwnd.svc/Tasks"></e-datamanager> 
        <e-kanbancolumns>
            <e-kanbancolumn header-text="Backlog" key=@(new List<string>(){"Open"})>        
            </e-kanbancolumn>
            <e-kanbancolumn header-text="In Progress" key=@(new List<string>() {"InProgress"})></e-kanbancolumn>
            <e-kanbancolumn header-text="Done" key=@(new List<string>() {"Close"}) ></e-kanbancolumn>
        </e-kanbancolumns>
        <e-kanbanfield content="Summary" primary-key="Id">
        </e-kanbanfield>
    </ej-kanban>

{% endhighlight  %}


![](getting-started-images/Kanban_img1.png)

## Enable Swimlane

`Swimlane` can be enabled by mapping the ` swimlane-key ` to appropriate column name in ` DataSource`. This enables the grouping of the cards based on the mapped column values.

{% highlight CSHTML %}

    <ej-kanban id="KanbanBoard" key-field="Status">
        <e-datamanager url="//mvc.syncfusion.com/Services/Northwnd.svc/Tasks"></e-datamanager> 
        <e-kanbancolumns>
            <e-kanbancolumn header-text="Backlog" key=@(new List<string>(){"Open"})>        
            </e-kanbancolumn>
            <e-kanbancolumn header-text="In Progress" key=@(new List<string>() {"InProgress"})></e-kanbancolumn>
            <e-kanbancolumn header-text="Done" key=@(new List<string>() {"Close"}) ></e-kanbancolumn>
        </e-kanbancolumns>
        <e-kanbanfield content="Summary" primary-key="Id" swimlane-key="Assignee">
        </e-kanbanfield>
    </ej-kanban>


{% endhighlight  %}

![](getting-started-images/Kanban_img2.png)

## Adding Filters

{% highlight CSHTML %}

    <ej-kanban id="KanbanBoard" key-field="Status">
        <e-datamanager url="//mvc.syncfusion.com/Services/Northwnd.svc/Tasks"></e-datamanager>
        <e-kanbancolumns>
            <e-kanbancolumn header-text="Backlog" key=@(new List<string>(){"Open"})>
            </e-kanbancolumn>
            <e-kanbancolumn header-text="In Progress" key=@(new List<string>() {"InProgress"})></e-kanbancolumn>
            <e-kanbancolumn header-text="Testing" key=@(new List<string>() {"Testing"})></e-kanbancolumn>
        </e-kanbancolumns>
        <e-kanbanfield content="Summary" primary-key="Id" swimlane-key="Assignee">
        </e-kanbanfield>
        <e-kanbanfilter-settings>
            <e-kanbanfilter-setting text="Janet Issues" query="new ej.Query().where('Assignee', 'equal', 'Janet Leverling')" description="Displays issues which matches the assignee as 'Janet Leverling`"></e-kanbanfilter-setting>
            <e-kanbanfilter-setting text="Testing Issues" query="new ej.Query().where('Status', 'equal', 'Testing')" description="Display the issues of 'Testing'"></e-kanbanfilter-setting>
        </e-kanbanfilter-settings>
    </ej-kanban>

{% endhighlight  %}


![](getting-started-images/Kanban_img3.png)