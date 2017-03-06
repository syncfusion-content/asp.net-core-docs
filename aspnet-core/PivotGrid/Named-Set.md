---
layout: post
title: Named Set
description: named set
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Named Set

Named set is a multidimensional expression (MDX) that returns a set of dimension members, which can be created by combining cube data, arithmetic operators, numbers and functions.

## Client Mode

You can bind the Named Sets in PivotGrid by setting it's unique name in the `field-name` property either in row or column axis and `is-named-sets` boolean property to "true".

{% highlight CSHTML %}

<ej-pivot-grid id="PivotGrid1">
    <e-data-source catalog="Adventure Works DW 2008 SE" cube="Adventure Works" data="//bi.syncfusion.com/olap/msmdpump.dll">
        <e-pivot-rows>
            <e-row-field field-name="[Date].[Fiscal]"></e-row-field>
        </e-pivot-rows>
        <e-pivot-columns>
            <e-column-field field-name="[Core Product Group]"></e-column-field>
        </e-pivot-columns>
        <e-pivot-values>
            <e-value-field axis="Column">
                <e-measures>
                    <e-measure-items field-name="[Measures].[Internet Sales Amount]" is-named-sets="true"></e-measure-items>
                </e-measures>
            </e-value-field>
        </e-pivot-values>
    </e-data-source>
</ej-pivot-grid>

{% endhighlight %}

![](KPI_images/namedset.png)
