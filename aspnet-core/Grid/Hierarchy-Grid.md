---
layout: post
title: Hierarchical binding | Grid | ASP.NET Core | Syncfusion
description: How to bind the hierarchical data
platform: aspnet-core
control: Grid
documentation: ug
---

# Hierarchical Bindings

Hierarchical binding can be used to create the Grid with parent and child relation, this facilitate you to view the child records for a particular row by clicking on the Expander button present in first column of each grid row. This can be enabled by defining Grid within Grid and `query-string`.

The Grid within Grid is used to define the model properties that has to be applied on the child grid. The Grid within Grid is the extended class of the base class Grid such that it holds all the properties of the Grid. The `query-string` is a property that has to be specified within the Grid within the Grid, which defines the relation between the parent and child grid. The `query-string` property is used to denote the primaryKey field of the parent grid which is to be mapped with the foreignKey field of the child grid. Based on the mapping, the child grid records are filtered from the table and is bound as datasource for the child grid.

{% tabs %}

{% highlight razor %}

<ej-grid id="HierarchyGrid" datasource="ViewBag.datasource" allow-paging="true">
    <e-columns>
        <e-column field="EmployeeID" header-text="Employee ID" text-align="Right" width="85"></e-column>
        <e-column field="FirstName" header-text="First Name" width="100"></e-column>
        <e-column field="Title"></e-column>
        <e-column field="City" width="100"></e-column>
        <e-column field="Country" width="100"></e-column>
    </e-columns>
    <ej-grid query-string="EmployeeID" allow-paging="true">
        <e-datamanager url="http://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders"></e-datamanager>
        <e-page-settings page-size="5"></e-page-settings>
        <e-columns>
            <e-column field="OrderID" header-text="OrderID" text-align="Right" width="75"></e-column>
            <e-column field="ShipCity" header-text="ShipCity" width="100"></e-column>
            <e-column field="Freight" width="120"></e-column>
            <e-column field="ShipName" width="100"></e-column>
        </e-columns>
    </ej-grid>
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
        public ActionResult HierarchyGrid()
        {
            
            var DataSource = _context.Employees.ToList();

            ViewBag.datasource = DataSource;

            return View();
        }

    }

{% endhighlight  %}

{% endtabs %} 

![](Hierarchy-Grid_images/Hierarchy-Grid_img1.png)


## Expand or Collapse All Child's

The Grid can able to expand and collapse all the `ChildGrid` through programmatically using [`expandAll`](http://help.syncfusion.com/js/api/ejgrid#methods:expandall "expandAll") and [`collapseAll`](http://help.syncfusion.com/js/api/ejgrid#methods:collapseall "collapseAll") method.

{% tabs %}

{% highlight razor %}

<ej-button id="expand" text="expandAll" show-rounded-corner="true" click="onClick" />
<ej-button id="collapse" text="collapseAll" show-rounded-corner="true" click="onClick" />

<ej-grid id="HierarchyGrid" datasource="ViewBag.datasource" allow-paging="true">
    <e-columns>
        <e-column field="EmployeeID" header-text="Employee ID" text-align="Right" width="85"></e-column>
        <e-column field="FirstName" header-text="First Name" width="100"></e-column>
        <e-column field="Title"></e-column>
        <e-column field="City" width="100"></e-column>
        <e-column field="Country" width="100"></e-column>
    </e-columns>
    <ej-grid query-string="EmployeeID" allow-paging="true">
        <e-datamanager url="http://js.syncfusion.com/demos/ejServices/Wcf/Northwind.svc/Orders"></e-datamanager>
        <e-page-settings page-size="5"></e-page-settings>
        <e-columns>
            <e-column field="OrderID" header-text="OrderID" text-align="Right" width="75"></e-column>
            <e-column field="ShipCity" header-text="ShipCity" width="100"></e-column>
            <e-column field="Freight" width="120"></e-column>
            <e-column field="ShipName" width="100"></e-column>
        </e-columns>
    </ej-grid>
</ej-grid>



    <script type="text/javascript">
        function onClick(args) {
            $("#HierarchyGrid").ejGrid(args.model.text); //invokes expandAll & collapseAll method based on button name
        }
   </script>

{% endhighlight  %}
{% highlight c# %}

public partial class GridController : Controller
    {
        private NORTHWNDContext _context;

        public GridController(NORTHWNDContext context)
        {
            _context = context;
        }
        public ActionResult HierarchyGrid()
        {
            
            var DataSource = _context.Employees.ToList();

            ViewBag.datasource = DataSource;

            return View();
        }

    }


{% endhighlight  %}

{% endtabs %} 

