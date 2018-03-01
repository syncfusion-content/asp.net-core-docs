---
layout: post
title: Advanced Filtering and Soritng
description: advanced filtering and sorting
platform: aspnet-core
control: PivotClient
documentation: ug
---


# Advanced filtering and sorting

It allows you to filter and sort the field members in the pivot client.

You can enable the "Advanced Filtering and Sorting" option in the pivot client by setting the [`enable-advanced-filter`] property under [`e-data-source`] to true.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1">
    <e-data-source enable-advanced-filter="true">
        //..
    </e-data-source>
</ej-pivot-client>

{% endhighlight %}

## Sorting

Sorting provides an option to sort the members of a field in the ascending or descending order.

![](AdvanceFiltering_images/sorting.png)

## Label filtering

Label filtering provides an option to filter the members of a field purely based on their caption.

![](AdvanceFiltering_images/filtering.png)

![](AdvanceFiltering_images/filtering_dialog.png)

## Value filtering

Value filtering provides an option to filter members based on the total values of the appropriate measure between the members of the level. 

![](AdvanceFiltering_images/valuefilter.png)

![](AdvanceFiltering_images/valuefilter_dialog.png)
