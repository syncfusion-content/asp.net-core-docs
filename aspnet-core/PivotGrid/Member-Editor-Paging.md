---
layout: post
title: Member Editor Paging
description: memebr editor paging
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Member editor paging

The member editor paging helps to improve the rendering performance of the dialog by dividing the large amount of data into several sections and displaying them.

You can enable the member editor paging and set the member editor page size in the pivot grid control by setting the [`enable-member-editor-paging`] and [`member-editor-page-size`] properties.


{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1" load="onload" enable-member-editor-paging="true" member-editor-page-size=100>
    <e-data-source>
        <e-pivot-rows>
            <e-row-field field-name="Country" field-caption="Country"></e-row-field>
            <e-row-field field-name="State" field-caption="State"></e-row-field>
        </e-pivot-rows>
        <e-pivot-columns>
            <e-column-field field-name="Product" field-caption="Product"></e-column-field>
        </e-pivot-columns>
        <e-pivot-values>
            <e-value-field field-name="Amount" field-caption="Amount"></e-value-field>
            <e-value-field field-name="Quantity" field-caption="Quantity"></e-value-field>
        </e-pivot-values>
        <e-pivot-filters>
            <e-filter-field field-name="Date" field-caption="Date"></e-filter-field>
        </e-pivot-filters>
    </e-data-source>
</ej-pivot-grid>

{% endhighlight %}

Following are the navigation options available in the member editor pager:
* Move first: Navigates to the first page.
* Move previous: Navigates to the previous page from the current page.
* Move next: Navigates to the next page from the current page.
* Move last: Navigates to the last page.
* Numeric box: Navigates to the desired page by entering an appropriate page number in the numeric value.


![](Member_Editor_images/member_editor.png)