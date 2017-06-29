---
layout: post
title: Advanced Filtering
description: advance filtering and sorting
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Advanced Filtering & Sorting

It allows to filter and sort the field members in PivotGrid.

In client mode, you can enable Advanced Filtering and Sorting option in PivotGrid by setting the [`enable-advanced-filter`] property to true.

{% highlight html %}

<ej:PivotGrid ID=" PivotGrid1" enable-advanced-filter="true" runat="server"></ej:PivotGrid>

{% endhighlight %}

## Sorting

Sorting provides an option to sort the members of a field either in ascending or descending order. 

![](AdvanceFiltering_images/sorting.png)

## Label Filtering

Label filtering provides an option to filter the members of a field purely based on their caption. 

![](AdvanceFiltering_images/filtering.png)

![](AdvanceFiltering_images/filtering_dialog.png)


## Value Filtering

Value filtering provides an option to filter members based on the total values of the appropriate measure between the members of the level. 

![](AdvanceFiltering_images/valuefilter.png)

![](AdvanceFiltering_images/valuefilter_dialog.png)
