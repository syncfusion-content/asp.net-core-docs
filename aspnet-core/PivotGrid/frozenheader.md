---
layout: post
title:  Frozen Header | PivotGrid | ASP.NET MVC | Syncfusion
description:  frozen header
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Frozen Header

Allows you to freeze the header of the Grid so that it will be always visible when scrolling the content with a large number of rows or columns providing a precise view.

{% highlight CSHTML %}

<ej-pivot-grid id="PivotGrid1" >
    <e-frozen-header enable-frozen-headers="true"></e-frozen-header>
</ej-pivot-grid>

{% endhighlight %}

![](FrozenHeader_images/row_col_freeze.png)

We can also freeze the row/column headers individually by setting the below properties.

{% highlight CSHTML %}

<ej-pivot-grid id="PivotGrid1" >
    <e-frozen-header enable-frozen-row-headers="true"></e-frozen-header>
</ej-pivot-grid>

{% endhighlight %}

![](FrozenHeader_images/row_freeze.png)

{% highlight CSHTML %}

<ej-pivot-grid id="PivotGrid1" >
    <e-frozen-header enable-frozen-column-headers="true"></e-frozen-header>
</ej-pivot-grid>

{% endhighlight %}

![](FrozenHeader_images/col_freeze.png)