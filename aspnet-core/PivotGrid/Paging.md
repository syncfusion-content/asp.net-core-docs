---
layout: post
title: Paging
description: paging
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Paging

## Pager

Paging helps you to improve the rendering performance of the pivot grid control by dividing large amount of data into sections and displaying one section at a time. You can enable the paging option in the pivot grid by setting the `enable-paging` property to true. You can provide the page size and current page details for each axis in the `e-pager-options` property.

Inside the **ej-pivot-pager** , the enumeration property mode should be set to **Both** to display both categorical pager and series pager. The other enumerations such as **Categorical** and **Series** will display only the categorical pager and the series pager respectively.

{% highlight html %}

    <ej-pivot-grid id="PivotGrid1" load="onload" enable-paging="true">
        <e-data-source>
            <e-pivot-rows>
                <e-row-field field-name="Country" field-caption="Country"></e-row-field>
                <e-row-field field-name="State" field-caption="State"></e-row-field>
            </e-pivot-rows>
            <e-pivot-columns>
                <e-column-field field-name="Date" field-caption="Date"></e-column-field>
            </e-pivot-columns>
            <e-pivot-values>
                <e-value-field field-name="Amount" field-caption="Amount"></e-value-field>
                <e-value-field field-name="Quantity" field-caption="Quantity"></e-value-field>
            </e-pivot-values>
            <e-pager-options categorical-page-size="3" categorical-current-page="1" series-page-size="3" series-current-page="1"></e-pager-options>
        </e-data-source>
    </ej-pivot-grid>
    <ej-pivot-pager id="Pager1" target-control-id="PivotGrid1" mode="Both"></ej-pivot-pager>

{% endhighlight %}


Following are the navigation options available in the pager:

* Move first: Navigates to the first page.
* Move last: Navigates to the last page.
* Move previous: Navigates to the previous page from the current page.
* Move next: Navigates to the next page from the current page.
* Numeric box: Navigates to the desired page by entering an appropriate page number in the numeric value.

![](Paging_images/paging.png)


## Virtual scrolling

Virtual scrolling is a technique that allows you to view the pivot grid information page by page with the use of vertical and horizontal scrollbar. You can enable the virtual scrolling option in the pivot grid by setting the `enable-virtual-scrolling` property to true. You can provide the page size and current page details for each axis in the `e-pager-options` property.

{% highlight html %}

    <ej-pivot-grid id="PivotGrid1" load="onload" enable-virtual-scrolling="true">
        <e-data-source>
            <e-pivot-rows>
                <e-row-field field-name="Country" field-caption="Country"></e-row-field>
                <e-row-field field-name="State" field-caption="State"></e-row-field>
            </e-pivot-rows>
            <e-pivot-columns>
                <e-column-field field-name="Date" field-caption="Date"></e-column-field>
            </e-pivot-columns>
            <e-pivot-values>
                <e-value-field field-name="Amount" field-caption="Amount"></e-value-field>
                <e-value-field field-name="Quantity" field-caption="Quantity"></e-value-field>
            </e-pivot-values>
            <e-pager-options categorical-page-size="3" categorical-current-page="1" series-page-size="3" series-current-page="1"></e-pager-options>
        </e-data-source>
    </ej-pivot-grid>

{% endhighlight %}

![](Paging_images/virtual-scrolling.png)

## Page settings

The properties associated to paging are:

* EnablePaging: This property is used to enable/disable paging in the pivot client control.
* PagerOptions.CategoricalPageSize: Specifies the number of categorical columns to be displayed within a page of the pivot client control.
* PagerOptions.SeriesPageSize: Specifies the number of series rows to be displayed within a page of the pivot client control.
* PagerOptions.CategoricalCurrentPage: Sets the current page of the categorical axis in the pivot client control.
* PagerOptions.SeriesCurrentPage: Sets the current page of the series axis in the pivot client control.

The page setting for categorical and series axes are needed to be set in the data source property by using the following properties:

`categorical-page-size` - Allows to set the number of categorical columns to be displayed in each page on applying the paging.

`series-page-size` - Allows to set the number of series rows to be displayed in each page on applying the paging.

`categorical-current-page` - Allows to set the page number to be loaded in the categorical axis by default.

`series-current-page` - Allows to set the page number to be loaded in the series axis by default.

{% highlight html %}

    <ej-pivot-grid id="PivotGrid1" load="onload" enable-paging="true">
        <e-data-source>
            <e-pivot-rows>
                <e-row-field field-name="Country" field-caption="Country"></e-row-field>
                <e-row-field field-name="State" field-caption="State"></e-row-field>
            </e-pivot-rows>
            <e-pivot-columns>
                <e-column-field field-name="Date" field-caption="Date"></e-column-field>
            </e-pivot-columns>
            <e-pivot-values>
                <e-value-field field-name="Amount" field-caption="Amount"></e-value-field>
                <e-value-field field-name="Quantity" field-caption="Quantity"></e-value-field>
            </e-pivot-values>
            <e-pager-options categorical-page-size="3" categorical-current-page="1" series-page-size="3" series-current-page="1"></e-pager-options>
        </e-data-source>
    </ej-pivot-grid>
    <ej-pivot-pager id="Pager1" target-control-id="PivotGrid1" mode="Both"></ej-pivot-pager>

{% endhighlight %}
