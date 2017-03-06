---
layout: post
title: Grid Layout
description: grid layout
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Grid Layout

## Normal Layout

A layout in which summary cells are positioned at the bottom of each parent member and their child members appear next to them. Normal layout is the default layout in PivotGrid control. The enumeration property `layout` needs to be set to **"Normal"** in-order to view PivotGrid in normal layout. 

{% highlight CSHTML %}

<ej-pivot-grid id="PivotGrid1" layout="Normal"></ej-pivot-grid>

{% endhighlight %}

![](Grid-Layout_images/layout-normal.png)

## Excel-like Layout

A layout in which summary cells are positioned besides each parent member and their child members appear next to them. The enumeration property `layout` needs to be set to **"ExcelLikeLayout"** in-order to view PivotGrid in excel-like layout.

{% highlight CSHTML %}

<ej-pivot-grid id="PivotGrid1" layout="ExcelLikeLayout"></ej-pivot-grid>

{% endhighlight %} 

![](Grid-Layout_images/layout-excel.png)
