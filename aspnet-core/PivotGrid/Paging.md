---
layout: post
title: Paging
description: paging
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Paging

Paging helps to improve the rendering performance of the PivotClient control by dividing large amount of data into sections and displaying one section at a time. You can enable paging in PivotClient by setting the `enable-paging` property to true.

## Using Pager

The page size and current page details for each axis can be provided through `e-pager-options` property within the `e-data-source` property of PivotGrid. The following properties are available to customize the pager options:

* `categorical-page-size` - Specifies the number of categorical columns to be displayed in each page on applying the paging.
* `series-page-size` - Specifies the number of series rows to be displayed in each page on applying the paging.
* `categorical-current-page` -Specifies the page number to be loaded in the categorical axis by default.
* `series-current-page` - Specifies the page number to be loaded in the series axis by default.

The `mode` property of **ej-pivot-pager** is used to specify whether the categorical pager or series pager or both pager should be displayed.

The following code snippet shows that how to display both categorical and series pager:

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

### Pager Options

The following are the options available in Pager for navigating pages at run-time.

* Move First - Navigates to the first page.
* Move Last - Navigates to the last page.
* Move Previous - Navigates to the previous page from the current page.
* Move Next - Navigates to the next page from the current page.
* Numeric Box - Navigates to the desired page by entering an appropriate page number in the numeric box.

![](Paging_images/paging.png)

## Using virtual scrolling

Virtual scrolling is a technique that allows user to view the PivotGrid information page by page with the use of vertical and horizontal scrollbar. You can enable virtual scrolling in PivotGrid by setting the `enable-virtual-scrolling` property to true. You can also provide the page size and current page details for each axis through `e-pager-options` property.

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