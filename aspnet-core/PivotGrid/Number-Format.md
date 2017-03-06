---
layout: post
title: Number format
description: number format 
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Number format 

I> This feature is applicable only for Relational datasource only at Client Mode.

Allow us to specify the required number format that PivotGrid should use in its values by setting the `format` option. Following number formats that are supported:

* number
* decimal
* currency
* percentage
* date
* time
* scientific
* accounting
* fraction

{% highlight CSHTML %}

<ej-pivot-grid id="PivotGrid1" load="onload">
    <e-data-source>
        <e-pivot-rows>
            <e-row-field field-name="State" field-caption="State"></e-row-field>
            <e-row-field field-name="Country" field-caption="Country"></e-row-field>
        </e-pivot-rows>
        <e-pivot-columns>
            <e-column-field field-name="Product" field-caption="Product"></e-column-field>
        </e-pivot-columns>
        <e-pivot-values>
            <e-value-field field-name="Amount" field-caption="Amount" format="currency"></e-value-field>
            <e-value-field field-name="Quantity" field-caption="Quantity" format="decimal"></e-value-field>
        </e-pivot-values>
    </e-data-source>
</ej-pivot-grid>

 {% endhighlight %}

![](Number-Format_images/Numberformat.png)

