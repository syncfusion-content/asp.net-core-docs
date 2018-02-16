---
layout: post
title: Paging
description: paging
platform: aspnet-core
control: PivotClient
documentation: ug
---

# Paging

Paging helps to improve the rendering performance of the PivotClient control by dividing large amount of data into sections and displaying one section at a time.

## Using Pager 

You can enable Pager in PivotClient by setting the `enable-paging` property to true. You can provide the page size and current page details for each axis through `e-pager-options` property.

{% highlight CSHTML %}

    <ej-pivot-client id="PivotClient1" enable-complete-data-export="true" title="OLAP Browser" enable-paging="true" before-export="Export" render-success="setChartProperties" load-report="reportSettings" fetch-report="reportSettings" save-report="reportSettings">
        <e-size width="910px"></e-size>
        <e-data-source catalog="Adventure Works DW 2008 SE" cube="Adventure Works" data="//bi.syncfusion.com/olap/msmdpump.dll">
            <e-pivot-rows>
                <e-row-field field-name="[Date].[Date]"></e-row-field>
            </e-pivot-rows>
            <e-pivot-columns>
                <e-column-field field-name="[Customer].[Customer Geography]"></e-column-field>
            </e-pivot-columns>
            <e-pivot-values>
                <e-value-field axis="Column">
                    <e-measures>
                        <e-measure-items field-name="[Measures].[Internet Sales Amount]"></e-measure-items>
                    </e-measures>
                </e-value-field>
            </e-pivot-values>
            <e-pager-options categorical-page-size="3" categorical-current-page="1" series-page-size="3" series-current-page="1"></e-pager-options>
        </e-data-source>
    </ej-pivot-client>

{% endhighlight %}

Following are the navigation option available in Pager.

* Move First - Navigates to the first page.
* Move Last - Navigates to the last page. 
* Move Previous - Navigates to the previous page from the current page.
* Move Next - Navigates to the next page from the current page.
* Numeric Box - Navigates to the desired page by entering an appropriate page number in numeric value.

![](Paging_images/paging.png)


## Using Virtual Scrolling

Virtual Scrolling is a technique that allows user to view the PivotClient information page by page with the use of vertical and horizontal scrollbar. You can enable Virtual Scrolling option in PivotClient by setting the `enable-virtual-scrolling` property to true. You can provide the page size and current page details for each axis through `e-pager-options` property. 

{% highlight CSHTML %}

    <ej-pivot-client id="PivotClient1" title="OLAP Browser" enable-virtual-scrolling="true"  load="onLoad">
        <e-size width="910px"></e-size>
        <e-data-source catalog="Adventure Works DW 2008 SE" cube="Adventure Works" data="//bi.syncfusion.com/olap/msmdpump.dll">
            <e-pivot-rows>
                <e-row-field field-name="[Date].[Date]"></e-row-field>
            </e-pivot-rows>
            <e-pivot-columns>
                <e-column-field field-name="[Customer].[Customer Geography]"></e-column-field>
            </e-pivot-columns>
            <e-pivot-values>
                <e-value-field axis="Column">
                    <e-measures>
                        <e-measure-items field-name="[Measures].[Internet Sales Amount]"></e-measure-items>
                    </e-measures>
                </e-value-field>
            </e-pivot-values>
            <e-pager-options categorical-page-size="3" categorical-current-page="1" series-page-size="3" series-current-page="1"></e-pager-options>
        </e-data-source>
    </ej-pivot-client>

{% endhighlight %}

![](Paging_images/virtual-scrolling.png)

## Page Settings

The properties associated to paging are:
* EnablePaging – This property is used to enable/disable paging in PivotClient control.
* PagerOptions.CategoricalPageSize - Specifies the number of categorical columns to be displayed within a page of the PivotClient control.
* PagerOptions.SeriesPageSize - Specifies the number of series rows to be displayed within a page of the PivotClient control.
* PagerOptions.CategoricalCurrentPage - Sets the current page of the categorical axis in PivotClient control.
* PagerOptions.SeriesCurrentPage - Sets the current page of the series axis in PivotClient control.

The page setting for categorical and series axes are needed to be set in the data source property by using the following properties:

`categorical-page-size` - Allows to set the number of categorical columns to be displayed in each page on applying the paging.

`series-page-size` - Allows to set the number of series rows to be displayed in each page on applying the paging.

`categorical-current-page` - Allows to set the page number to be loaded in the categorical axis by default.

`series-current-page` - Allows to set the page number to be loaded in the series axis by default.

{% highlight CSHTML %}

    <ej-pivot-client id="PivotClient1" enable-complete-data-export="true" title="OLAP Browser" enable-paging="true" before-export="Export" render-success="setChartProperties" load-report="reportSettings" fetch-report="reportSettings" save-report="reportSettings">
        <e-size width="910px"></e-size>
        <e-data-source catalog="Adventure Works DW 2008 SE" cube="Adventure Works" data="//bi.syncfusion.com/olap/msmdpump.dll">
            <e-pivot-rows>
                <e-row-field field-name="[Date].[Date]"></e-row-field>
            </e-pivot-rows>
            <e-pivot-columns>
                <e-column-field field-name="[Customer].[Customer Geography]"></e-column-field>
            </e-pivot-columns>
            <e-pivot-values>
                <e-value-field axis="Column">
                    <e-measures>
                        <e-measure-items field-name="[Measures].[Internet Sales Amount]"></e-measure-items>
                    </e-measures>
                </e-value-field>
            </e-pivot-values>
            <e-pager-options categorical-page-size="3" categorical-current-page="1" series-page-size="3" series-current-page="1"></e-pager-options>
        </e-data-source>
    </ej-pivot-client>

{% endhighlight %}
