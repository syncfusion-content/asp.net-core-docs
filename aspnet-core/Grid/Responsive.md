---
layout: post
title: Responsive with Grid widget for Syncfusion ASP.NET Core
description: How to set the grid, responsive to screen resolutions
platform: ASP.NET Core
control: Grid
documentation: ug
---

# Responsive

The grid control has support for responsive behavior based on client browser's width and height. To enable responsive, `is-responsive>` property should be true. There are three modes of responsive layout is available in grid based on client width. They are.

* Mobile(<321px)
* Tablet (321px to 800px)
* Desktop(>800px)

## Mobile Layout

If client width is less than 321px, the grid will render in mobile mode. In which, you can see that grid user interface is customized and redesigned for best view in small screens. The customized features includes responsive row rendering, filtering, sorting, searching and editing.

### Responsive Row

Enabling Responsive row makes the Grid to render the record values in vertical order which removes the need for horizontal scrolling to view complete record details. It can be enabled by defining `enable-responsive-row` property as `true`.

{% tabs %}

{% highlight razor %}

<ej-grid id="FlatGrid" datasource="ViewBag.DataSource" is-responsive="true" enable-responsive-row="true" allow-paging="true">
    <e-page-settings page-count="3" page-size="7"></e-page-settings>
    <e-columns>
        <e-column field="OrderID" header-text="Order ID" is-primary-key="true"></e-column>
        <e-column field="CustomerID" header-text="Customer ID"></e-column>
        <e-column field="EmployeeID" header-text="Employee ID" text-align="Right"></e-column>
        <e-column field="ShipCity" format="{0:c2}" header-text="Ship city"></e-column>
        <e-column field="Freight" header-text="Freight" format="{0:C}"></e-column>
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
        public ActionResult Default()
        {
            ViewBag.datasource = _context.Orders.Take(100).ToList();
            return View();
        }
    }
{% endhighlight  %}
{% endtabs %} 


![](Responsive_images/Responsive_img1.png)


W> IE8 and IE9 does not support responsive row. `ejgrid.responsive.css` should be referred to display Responsive Row.

### Customized Features

The customized layout for filtering, sorting, searching and CRUD operations in mobile device can be seen following screen shots.

![](Responsive_images/Responsive_img2.png)
{:caption}
Responsive row with Filtering , Sorting and Searching

![](Responsive_images/Responsive_img3.png)

{:caption}
CRUD in mobile layout

![](Responsive_images/Responsive_img4.png)

{:caption}
Filtering in mobile layout

![](Responsive_images/Responsive_img5.png)
{:caption}

Filtering in mobile layout

![](Responsive_images/Responsive_img6.png)

{:caption}
Sorting in mobile layout

![](Responsive_images/Responsive_img7.png)
{:caption}

Searching in mobile layout

{% tabs %}

{% highlight razor %}
<ej-grid id="FlatGrid" datasource="ViewBag.DataSource" is-responsive="true" enable-responsive-row="true" allow-paging="true" allow-filtering="true" allow-sorting="true" allow-multi-sorting="true">
    <e-page-settings page-count="3" page-size="7"></e-page-settings>
    <e-edit-settings allow-adding="true" allow-editing="true" allow-deleting="true"></e-edit-settings>
    <e-toolbar-settings show-toolbar="true" toolbar-items='@new List<string> {"add","edit","delete","update","cancel"}' />
    <e-filter-settings filter-type="Menu"></e-filter-settings> 
    <e-columns>
        <e-column field="OrderID" header-text="Order ID" is-primary-key="true">
        </e-column>
        <e-column field="CustomerID" header-text="Customer ID"></e-column>
        <e-column field="EmployeeID" header-text="Employee ID" text-align="Right"></e-column>
        <e-column field="ShipCity" format="{0:c2}" header-text="Ship city"></e-column>
        <e-column field="Freight" header-text="Freight" format="{0:C}"></e-column>
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
        public ActionResult Default()
        {
            ViewBag.datasource = _context.Orders.Take(100).ToList();
            return View();
        }
    }

{% endhighlight  %}
{% endtabs %} 

## Tablet Layout

If the client width is between 321px and 800px, then the grid will render in tablet mode. Also it has customized filtering design to match tablet screen size.

{% tabs %}

{% highlight razor %}

<ej-grid id="FlatGrid" datasource="ViewBag.DataSource" is-responsive="true" allow-paging="true">
    <e-page-settings page-count="3" page-size="7"></e-page-settings>
    <e-filter-settings filter-type="Menu"></e-filter-settings> 
    <e-columns>
        <e-column field="OrderID" header-text="Order ID" is-primary-key="true" text-align="Right" width="90">
        </e-column>
        <e-column field="CustomerID" header-text="Customer ID" width="100"></e-column>
        <e-column field="EmployeeID" header-text="Employee ID" text-align="Right" width="90"></e-column>
        <e-column field="ShipCity" format="{0:c2}" header-text="Ship city" width="120"></e-column>
        <e-column field="Freight" header-text="Freight" format="{0:C}" width="80"></e-column>
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
        public ActionResult Default()
        {
            ViewBag.datasource = _context.Orders.Take(100).ToList();
            return View();
        }
    }
   
{% endhighlight  %}
{% endtabs %} 

![](Responsive_images/Responsive_img8.png)
{:caption}

Default tab layout

![](Responsive_images/Responsive_img9.png)

{:caption}
Filtering design in tab layout.

## Width

By default, the grid is adaptable to its parent container. It can adjust its width of columns based on parent container width. You can also assign `width` of `columns` in percentage. 

{% tabs %}

{% highlight razor %}
<ej-grid id="FlatGrid" datasource="ViewBag.DataSource"> 
    <e-columns>
        <e-column field="OrderID" header-text="Order ID" is-primary-key="true" text-align="Right" width="10%">
        </e-column>
        <e-column field="CustomerID" header-text="Customer ID" width="15%"></e-column>
        <e-column field="EmployeeID" header-text="Employee ID" text-align="Right" width="10%"></e-column>
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
        public ActionResult Default()
        {
            ViewBag.datasource = _context.Orders.Take(100).ToList();
            return View();
        }
    }

{% endhighlight  %}
{% endtabs %} 

I>  `AllowScrolling` should be false while defining Width in percentage.

## Min Width

Min Width is used to maintain minimum width for the Grid. To enable Min Width, `min-width` should be defined. If the grid width is less than `min-width` then the scrollbar will be displayed to maintain minimum width.

{% tabs %}

{% highlight razor %}

<ej-grid id="FlatGrid" datasource="ViewBag.DataSource" allow-paging="true" min-width="700"> 
    <e-columns>
        <e-column field="OrderID" header-text="Order ID" is-primary-key="true" text-align="Right" width="90">
        </e-column>
        <e-column field="CustomerID" header-text="Customer ID" width="100"></e-column>
        <e-column field="EmployeeID" header-text="Employee ID" text-align="Right" width="90"></e-column>
        <e-column field="ShipCity" format="{0:c2}" header-text="Ship city" width="120"></e-column>
        <e-column field="Freight" header-text="Freight" format="{0:C}" width="80"></e-column>
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
        public ActionResult Default()
        {
            ViewBag.datasource = _context.Orders.Take(100).ToList();
            return View();
        }
    }

{% endhighlight  %}
{% endtabs %} 

MinWidth set to Grid

## Priority for Columns

Priority makes column to be visible or hidden based on the `priority` value and browser's width to best accommodate the possible columns. To enable `Priority` for `Columns`, `Priority` needs to be defined in columns collection. These Priority values are from one to six.

{% tabs %}

{% highlight razor %}

<ej-grid id="FlatGrid" datasource="ViewBag.DataSource" allow-paging="true"> 
    <e-columns>
        <e-column field="OrderID" header-text="Order ID" is-primary-key="true" text-align="Right" width="90" priority="1">
        </e-column>
        <e-column field="CustomerID" header-text="Customer ID" width="100" priority="2"></e-column>
        <e-column field="EmployeeID" header-text="Employee ID" text-align="Right" width="90" priority="1"></e-column>
        <e-column field="ShipCity" format="{0:c2}" header-text="Ship city" width="120" priority="3"></e-column>
        <e-column field="Freight" header-text="Freight" format="{0:C}" width="80" priority="4"></e-column>
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
        public ActionResult Default()
        {
            ViewBag.datasource = _context.Orders.Take(100).ToList();
            return View();
        }
    }

{% endhighlight  %}
{% endtabs %} 

I> `ejgrid.responsive.css` should be referred.