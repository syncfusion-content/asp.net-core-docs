---
layout: post
title: PivotGrid Elements
description: pivotGrid elements
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# PivotGrid: Elements

## Hyperlink
The PivotGrid control supports hyperlink option to link data for each individual cell. Hyperlink can be enabled separately for row header, column header, value and summary cells. Following are the respective properties:

* **EnableColumnHeaderHyperlink** - Enables hyperlink for column headers.
* **EnableRowHeaderHyperlink** - Enables hyperlink for row headers.
* **EnableSummaryCellHyperlink** - Enables hyperlink for summary cell.
* **EnableValueCellHyperlink** - Enables hyperlink for value cell.

Also hyperlink option provides separate events for row header, column header, value and summary cells as mentioned below.
 
* **ColumnHeaderHyperlinkClick** - Returns column header information through event on hyperlink click.
* **RowHeaderHyperlinkClick** - Returns row header information through event on hyperlink click.
* **SummaryCellHyperlinkClick** - Returns summary cell information through event on hyperlink click.
* **ValueCellHyperlinkClick** - Returns value cell information through event on hyperlink click.

{% highlight CSHTML %}

<ej-pivot-grid id="PivotGrid1" value-cell-hyperlink-click="CellClickEvent" row-header-hyperlink-click="CellClickEvent" column-header-hyperlink-click="CellClickEvent" summary-cell-hyperlink-click="CellClickEvent">
    <e-hyperlink enable-column-header-hyperlink="true" enable-value-cell-hyperlink="true" enable-row-header-hyperlink="true" enable-summary-cell-hyperlink="true"></e-hyperlink>
</ej-pivot-grid>

<script type="text/javascript">
    CellClickEvent = function (evt) {
        alert("Cell Click event is fired");
    }
</script>

{% endhighlight %}

![](PivotGrid-Elements_images/hyperlink.png)

## Selection
You can select a particular range of value cells from PivotGrid and manipulate/display them. Cell selection is applicable only for value cells and you can enable this functionality by setting `enableCellSelection` property to true.

The **"cellSelection"** event would be triggered as soon as the selection process is over, that is, when the mouse left click is released. The event argument contains a collection of JSON records and header values, which contains information about the selected cells.

{% highlight CSHTML %}

<ej:PivotGrid ID="PivotGrid1" runat="server" EnableCellSelection="true" >
    <ClientSideEvents CellSelection="valueCellClick"/>
</ej:PivotGrid> 

<ej-pivot-grid id="PivotGrid1" enable-cell-selection="true" cell-selection="valueCellClick">
</ej-pivot-grid>

<script type="text/javascript">
    valueCellClick = function(evt) {
        // The event lets you to perform required operation with the selected set of cells. The details of the selected range can be obtained in the parameter of the event.
        cellvalue = evt.JSONRecords;
        rowheaders = evt.rowHeader;
        colheaders = evt.columnHeader;
    }
</script>

{% endhighlight %}

![](PivotGrid-Elements_images/cellselection.png)

## Cell Context
Cell context allows user to perform any custom operation on cell right-click. For example, you can create and display context menu on cell right-click.

Cell context is enabled by setting the `EnableCellContext` property to true. The **"cellContext"** event would be raised as soon as right-click is done providing cell information through event argument.

{% highlight CSHTML %}

<ej-pivot-grid id="PivotGrid1" enable-cell-context="true" cell-context="cell_RightClick">
</ej-pivot-grid>

<script type="text/javascript">
    cell_RightClick = function(evt) {
        //Write your Cell Context code here
    }
</script>

{% endhighlight %}

## Conditional Formatting
Conditional formatting allows user to highlight particular cells with certain color, font-style, font-family etc. based on the condition they have met. It is enabled by setting `EnableConditionalFormatting` property to true and the formatting dialog is launched when **"createConditionalDialog"** method is invoked.

{% highlight CSHTML %}

<ej-pivot-grid id="PivotGrid1" enable-conditional-formatting="true"></ej-pivot-grid>
<ej-button id="button" text="Conditional" size="@ButtonSize.Normal" show-rounded-corner="true" click="btnClick" />

<script type="text/javascript">
    function btnClick(e) {
        var pivotGridObj = $('#PivotGrid1').data("ejPivotGrid");
        if (pivotGridObj.model.enableConditionalFormatting) {
            pivotGridObj.createConditionalDialog();
        }
    }
</script>

{% endhighlight %}

![](PivotGrid-Elements_images/conditional.png)

### Export

We can export the PivotGrid with highlighted particular cells along with its formatting styles. 

LIMITATIONS FOR WORD:

The following border styles are not supported

* Solid
* Groove
* Ridge

LIMITATIONS FOR PDF:

Border styles are not applicable.

LIMITATIONS FOR EXCEL:

The following border styles are alone supported

* Dashed
* Dotted
* Double

Also border size is not supported.

![](PivotGrid-Elements_images/conditional_export.png)