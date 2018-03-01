---
layout: post
title: Layout
description: layout 
platform: aspnet-core
control: PivotGauge
documentation: ug
---

# Layout 

## Row-wise layout

Gauges can be arranged in specified number of rows by using the `rows-count` property.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1" rows-count="2"></ej-pivot-gauge>

{% endhighlight %}

![](Layout_images/RowBased.png) 

## Column-wise layout

Gauges can be arranged in specified number of columns by using the `columns-count` property.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1" columns-count="2"></ej-pivot-gauge>

{% endhighlight %}

![](Layout_images/ColumnBased.png)

