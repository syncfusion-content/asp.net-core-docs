---
layout: post
title: Layout Customization
description: layout customization
platform: aspnet-core
control: PivotClient
documentation: ug
---

# Layout Customization

# Size

Allows you to render PivotClient in different sizes. You can set height and width under `e-size` property.

## Set size in Pixels

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" >
    //..
    <e-size width="1000px" height="685px"></e-size>
</ej-pivot-client>

{% endhighlight %}

PivotClient with decreased size from default size

![](Layout-Customization_images/small-size.png)

## Set size in percentage

You can set the PivotClient size in percentage also.

N> Size of the parent container should be set in Pixels.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" >
    //..
    <e-size width="50%" height="80%"></e-size>
</ej-pivot-client>

{% endhighlight %}

## Control Placement 

### Tab View

In Tab view representation, both Grid and Chart will be displayed in separate tabs.  This could be set by using the `control-placement` property under the `e-display-settings` option.  By default, **Tab** value is set.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" >
    //..
    <e-display-settings control-placement="Tab"></e-display-settings>
</ej-pivot-client>

{% endhighlight %}

![](Layout-Customization_images/tabview.png)

### Tile View

In Tile View representation, both Grid and Chart will be displayed one above the other, in the same layout. Tile view can be set by using the `control-placement` property under the `e-display-settings` option.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" >
    //..
    <e-display-settings control-placement="Tile"></e-display-settings>
</ej-pivot-client>

{% endhighlight %}

![](Layout-Customization_images/tileview.png)

## Default View

### Grid View

To display Grid control by default, set `default-view` property under `e-display-settings` option to **Grid**, which is the default value of the property.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" >
    //..
    <e-display-settings default-view="Grid"></e-display-settings>
</ej-pivot-client>

{% endhighlight %}

![](Layout-Customization_images/gridview.png)

### Chart View

To display Chart control by default, set the property `default-view` property to **Chart**.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" >
    //..
    <e-display-settings default-view="Chart"></e-display-settings>
</ej-pivot-client>

{% endhighlight %}

![](Layout-Customization_images/chartview.png)

## Display Mode

### Grid Only

By the `mode` property under `e-display-settings` option to **GridOnly**, PivotGrid component alone will get rendered and PivotChart will not be rendered.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" >
    //..
    <e-display-settings mode="GridOnly"></e-display-settings>
</ej-pivot-client>

{% endhighlight %}

![](Layout-Customization_images/gridonlyview.png)

### Chart Only

By the `mode` property under `e-display-settings` option to **ChartOnly**, PivotChart component alone will get rendered and PivotGrid will not be rendered.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" >
    //..
    <e-display-settings mode="ChartOnly"></e-display-settings>
</ej-pivot-client>


{% endhighlight %}

![](Layout-Customization_images/chartonlyview.png)

### Both Chart and Grid

By the `mode` property under `e-display-settings` option to **ChartAndGrid**, data is displayed in both Grid and Chart.  This is the default value of the property.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" >
    //..
    <e-display-settings mode="ChartAndGrid"></e-display-settings>
</ej-pivot-client>

{% endhighlight %}

![](Layout-Customization_images/tileview.png)

## Toggle Panel

Toggle panel option lets the user to toggle the visibility of Axis Element Builder and Cube Dimension Browser panels in PivotClient with a use of a button. The button could be added to the control by enabling the `enable-toggle-panel` property under `e-display-settings` option.  This property is disabled by default.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" >
    //..
    <e-display-settings enable-toggle-panel="true"></e-display-settings>
</ej-pivot-client>

{% endhighlight %}

![](Layout-Customization_images/toggleview.png)

## Collapse Toggle Panel By Default

Allows the user to hide “Cube Browser” and “Axis Element Builder” panels while initiating the widget. You can enable this option in PivotClient by setting the `collapse-cube-browser-by-default` property to true.  

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" collapse-cube-browser-by-default="true">
    //..
</ej-pivot-client>

{% endhighlight %}

![](Layout-Customization_images/collapse-cube-browser-by-default.png)

## Maximized/Full Screen View

Full screen view helps to visualize the PivotGrid and PivotChart controls inside PivotClient precisely according to the browser window size.  By selecting full screen icon in the toolbar, the control which is in the view gets maximized.  Drilldown action can also be performed in both PivotGrid and PivotChart in the maximized view.  This option is enabled by setting the `enable-full-screen` property under `e-display-settings` option to true.  The value is false by default.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1">
    //..
    <e-display-settings enable-full-screen="true"></e-display-settings>
</ej-pivot-client>

{% endhighlight %}

![](Layout-Customization_images/maximizeicon.png)

The following screenshot shows the maximized view of PivotGrid.

![](Layout-Customization_images/maximizedview.png)


## Chart Types

While loading the PivotClient initially, the PivotChart widget can be rendered in any one of the available chart types using the `chart-type` property.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" chart-type="Column">
    //..
</ej-pivot-client>

{% endhighlight %}

The `ChartType` property takes Column Chart by default. The types available are Column, Stacking Column, Bar, Stacking Bar, Line, Spline, Step Line, Area, Spline Area, Step Area, Stacking Area, Pie, Funnel and Pyramid.

The Chart Type can also be changed dynamically through the toolbar icon.

![](Layout-Customization_images/charttypes.png)

![](Layout-Customization_images/linechart.png) 

### PivotTreeMap

I> This feature is applicable only for OLAP data source bound from server-side.

You can include the PivotTreeMap component as one of the chart types by setting `enable-pivot-tree-map` property to true.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" enable-pivot-tree-map="true">
    //..
</ej-pivot-client>

{% endhighlight %}

![](Layout-Customization_images/TreeMap1.png)

![](Layout-Customization_images/TreeMap2.png)


## Report Toolbar

You can customize the display of toolbar by enabling/disabling the visibility of each of the icons. This can be achieved by setting the properties under `e-toolbar-icon-settings` option to false. The values are true by default.​​​

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1">
    //..
    <e-toolbar-icon-settings enable-add-report="false" enable-new-report="false" enable-remove-report="false"></e-toolbar-icon-settings>
</ej-pivot-client>

{% endhighlight %}

![](Layout-Customization_images/toolbarIconSettings1.png)

The following screenshot shows after disabling the toolbar icons.

![](Layout-Customization_images/toolbarIconSettings2.png)
