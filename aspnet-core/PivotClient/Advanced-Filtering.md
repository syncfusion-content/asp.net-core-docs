---
layout: post
title: Advanced Filtering and Soritng
description: advanced filtering and sorting
platform: aspnet-core
control: PivotClient
documentation: ug
---


# Advanced Filtering & Sorting

It allows to filter and sort the field members in PivotClient.

You can enable "Advanced Filtering and Sorting" option in PivotClient by setting the [`enable-advanced-filter`] property under [`e-data-source`] to true.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1">
    <e-data-source enable-advanced-filter="true">
        //..
    </e-data-source>
</ej-pivot-client>

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
