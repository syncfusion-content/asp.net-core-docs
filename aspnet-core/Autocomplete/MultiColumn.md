---
layout: post
title: Multiple Columns | AutoComplete | ASP.NET Core | Syncfusion
description: multiple columns
platform: aspnet-core
control: AutoComplete
documentation: ug
---

# Multiple Columns

The Autocomplete allows list of data to be displayed in several columns and column collection can be defined and customized through the **MultiColumnSettings** property.

In AutoComplete Multiple Column search is based on **searchColumnIndices** property which allows user to search text for any number of fields in the suggestion list without modifying the selected text format.

N> if we use **searchColumnIndices** as “[0,1]” means search based on 0 and 1 columns data alone.

In AutoComplete Multiple Column searched value is updated to autocomplete input box based on **StringFormat** property which specifies values to updated.

N> **StringFormat** as “{0} ({1}) ({2})” means search based on 0, 1 and 2 columns data.

<table><tr><th>Name</th><th>Description</th></tr>
<tr><td>Enable</td><td>Allow list of data to be displayed in several columns.</td></tr>
<tr><td>ShowHeader</td><td>Allow header text to be displayed in corresponding columns.</td></tr>
<tr><td>StringFormat</td><td>Displayed selected value and autocomplete search based on mentioned column value specified in that format.</td></tr>
<tr><td>Columns</td><td>Field and Header Text collections can be defined and customized through this field.</td></tr>
<tr><td>Field</td><td>Get or set a value that indicates to display the columns in the autocomplete mapping with column name of the dataSource. </td></tr>
<tr><td>HeaderText</td><td>Get or set a value that indicates to display the title of that particular column.</td></tr></table>


## Configuring Multiple Columns

The following steps explain the configuration of the Multiple Columns for an AutoComplete textbox.

1.	In the View page, define the AutoComplete control and configure multicolumn.


{% highlight CSHTML %}

@*Refer to the DataSource defined in Local Data binding Step 1 *@

@{
    Syncfusion.JavaScript.Models.MultiColumnSettings val = new MultiColumnSettings();
    val.SearchColumnIndices = new List<int> { 0, 1 };
}

<div style="width: 600px">

    <div style="display:inline-block; float:left; margin-right:25px">

        <span style="display:block; margin-bottom:12px">Using Delimiter</span>
            <ej-autocomplete id="autocomplete" datasource="ViewBag.datasource">
                <e-multicolumnsettings enable="true" show-header="true" string-format="{0} ({1})" search-column-indices="@val.SearchColumnIndices">
                    <e-multi-columns>
                        <e-multi-column field="UniqueKey" header-text="Unique Key"></e-multi-column>
                        <e-multi-column field="Text" header-text="Text"></e-multi-column>
                    </e-multi-columns>
                </e-multicolumnsettings>
            </ej-autocomplete>

    </div>

</div>
{% endhighlight %}



The following image is the output for AutoComplete control with configured multiple column.



![](multicolumn_images/multicolumn_img1.png)



_AutoComplete with MultiColumn_

