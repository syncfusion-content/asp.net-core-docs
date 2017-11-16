---
layout: post
title: Key-Performance-Indicator-KPI
description: key performance indicator (KPI)
platform: aspnet-core
control: PivotClient
documentation: ug
---

# KPI

Key Performance Indicators (KPIs) are business metric that help to figure out the progress of an enterprise in meeting its business goals.

The different indicators available in KPI are:

* KPI Value: A physical measure or a calculated measure.
* KPI Goal: Defines the target for the measure.
* KPI Status: Evaluates the current status of the value compared to the goal.
* KPI Trend: Evaluate the current trend of the value compared to the goal.

The **“KpiElements”** class in OLAP Base library holds the KPI name and when its object is added to an OlapReport, you can view the resultant information in PivotClient. You can enable KPI in PivotClient by setting the `enable-kpi` property to true.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" title="OLAP Browser" enable-kpi="true">
    <e-data-source catalog="Adventure Works DW 2008 SE" cube="Adventure Works" data="//bi.syncfusion.com/olap/msmdpump.dll">
        <e-pivot-rows>
            <e-row-field field-name="[Customer].[Customer Geography]"></e-row-field>
        </e-pivot-rows>
        <e-pivot-columns>
            <e-column-field field-name="[Product].[Product Categories]"></e-column-field>
        </e-pivot-columns>
        <e-pivot-values>
            <e-value-field axis="Column">
                <e-measures>
                    <e-measure-items field-name="[Measures].[Internet Sales Amount]"></e-measure-items>
                    <e-measure-items field-name="[Measures].[Growth in Customer Base Trend]"></e-measure-items>
                    <e-measure-items field-name="[Measures].[Growth in Customer Base Status]"></e-measure-items>
                </e-measures>
            </e-value-field>
        </e-pivot-values>
    </e-data-source>
</ej-pivot-client>

{% endhighlight %}

![](KPI_images/clientmode-kpi.png)

