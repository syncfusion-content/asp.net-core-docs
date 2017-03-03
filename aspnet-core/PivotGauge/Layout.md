---
layout: post
title: Layout
description: layout 
platform: aspnet-core
control: PivotGauge
documentation: ug
---

# Layout 

## Row-wise Layout

Gauges can be arranged in specified number of rows by using the `RowsCount` property.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1" rows-count="2"></ej-pivot-gauge>

{% endhighlight %}

![](Layout_images/RowBased.png) 

## Column-wise Layout

Gauges can be arranged in specified number of columns by using the `ColumnsCount` property.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1" columns-count="2"></ej-pivot-gauge>

{% endhighlight %}

![](Layout_images/ColumnBased.png)

