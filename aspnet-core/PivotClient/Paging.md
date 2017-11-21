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

You can enable Pager in PivotClient by setting the `enable-paging` property to true. You can provide the page size and current page details for each axis through `pagerOptions` property.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" title="OLAP Browser" enable-paging="true" load="onLoad">
  //..
</ej-pivot-client>

<script type="text/javascript">
    function onLoad(args) {
         //You can set the pager options here.
         args.model.dataSource.pagerOptions= {
                    categoricalPageSize: 3,
                    seriesPageSize: 3,
                    categoricalCurrentPage: 1,
                    seriesCurrentPage: 1
                };
    }
</script>

@Html.EJ().Pivot().PivotClient("PivotClient1").DataSource(dataSource => dataSource.PagerOptions(pagerOptions => { pagerOptions.CategoricalPageSize(3).SeriesPageSize(3).CategoricalCurrentPage(1).SeriesCurrentPage(1); })).EnablePaging(true)

{% endhighlight %}

Following are the navigation option available in Pager.

* Move First - Navigates to the first page.
* Move Last - Navigates to the last page. 
* Move Previous - Navigates to the previous page from the current page.
* Move Next - Navigates to the next page from the current page.
* Numeric Box - Navigates to the desired page by entering an appropriate page number in numeric value.

![](Paging_images/paging.png)


## Using Virtual Scrolling

Virtual Scrolling is a technique that allows user to view the PivotClient information page by page with the use of vertical and horizontal scrollbar. You can enable Virtual Scrolling option in PivotClient by setting the `enable-virtual-scrolling` property to true. You can provide the page size and current page details for each axis through `pagerOptions` property. 

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" title="OLAP Browser" enable-virtual-scrolling="true"  load="onLoad">
  //..
</ej-pivot-client>

<script type="text/javascript">
    function onLoad(args) {
         //You can set the pager options here.
         args.model.dataSource.pagerOptions= {
                    categoricalPageSize: 3,
                    seriesPageSize: 3,
                    categoricalCurrentPage: 1,
                    seriesCurrentPage: 1
                };
    }
</script>

{% endhighlight %}

![](Paging_images/virtual-scrolling.png)

## Page Settings

The properties associated to paging are:
* EnablePaging – This property is used to enable/disable paging in PivotClient control.
* PagerOptions.CategoricalPageSize - Specifies the number of categorical columns to be displayed within a page of the PivotClient control.
* PagerOptions.SeriesPageSize - Specifies the number of series rows to be displayed within a page of the PivotClient control.
* PagerOptions.CategoricalCurrentPage - Sets the current page of the categorical axis in PivotClient control.
* PagerOptions.SeriesCurrentPage - Sets the current page of the series axis in PivotClient control.

The page setting for categorical and series axes are mandatorily needed to be set in data source property by using the following properties.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" title="OLAP Browser" enable-paging="true"  load="onLoad">
  //..
</ej-pivot-client>

<script type="text/javascript">
    function onLoad(args) {
         //You can set the pager options here
         args.model.dataSource.pagerOptions= {
                    categoricalPageSize: 3,
                    seriesPageSize: 3,
                    categoricalCurrentPage: 1,
                    seriesCurrentPage: 1
                };
    }
</script>

{% endhighlight %}
