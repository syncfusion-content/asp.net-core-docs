---
layout: post
title:  Drill Through
description:  drill through
platform: aspnet-core
control: PivotClient
documentation: ug
---

# Drill Through

Drill-through retrieves the raw items that are used to create a specified cell. To enable drill-through support, set [`enable-drill-through`] property to true. Raw items are obtained through the [`drill-through`] event, using which user can bind them to an external widget for precise view. 

N> Drill-through is supported in PivotGrid only when we configure and enable drill-through action at the Cube. 

![](DrillThrough_images/pivotclient.png)

On clicking any value cell, the "Drill Through Information" dialog will be opened. It consists of Grid with data which are associated with the measure values of the clicked value cell. In this example, the measure behind the respective cell is “Sales Amount” and the values of the dimensions which are associated with this measure are alone displayed in the Grid. 

![](DrillThrough_images/DrillThroughData.png)

On clicking the "Hierarchy Selector" button which is displayed below the Grid, the "Hierarchy Selector" dialog will be opened. It consists of the dimensions which are associated with the measure of clicked value cell. In this example, the measure behind the respective cell is “Sales Amount” and the dimensions associated with this measure are alone displayed in the dialog.  

![](DrillThrough_images/hierarchy_selector.png)

By dragging and dropping the respective hierarchies and finally clicking “OK” button, Drill through MDX query will be framed and executed internally and provides back the raw items through "drillThrough" event. In this example, we have bound the raw items obtained to our ejGrid widget. Please refer the code sample and screen-shot below.

{% highlight cshtml %}

<ej-pivot-client id="PivotClient1" title="OLAP Browser" enable-drill-through="true" drill-through="drilledData">
//..
</ej-pivot-client>

<script type="text/javascript">
    function drilledData(args) {
       $(".e-dialog, .e-clientDialog, .e-tableDlg").remove();
        gridData = JSON.parse(args.data);
        var dialogContent = ej.buildTag("div#" + this._id + "_tableDlg.e-tableDlg", $("<div id=\"Grid1\"></div>"))[0].outerHTML;
        var dialogFooter = ej.buildTag("div", ej.buildTag("button#btnOK.e-dialogBtnOK", "Hierarchy Selector")[0].outerHTML, { "float": "right", "margin": "-5px 0 6px" })[0].outerHTML
        ejDialog = ej.buildTag("div#clientDialog.e-clientDialog", dialogContent + dialogFooter, { "opacity": "1" }).attr("title", "Drill Through Information")[0].outerHTML;
        $(ejDialog).appendTo("#" + this._id);
        $("#btnOK").ejButton().css({ margin: "30px 0 20px 0" });
        $("#Grid1").ejGrid({
            dataSource: gridData,
            allowPaging: true,
            allowTextWrap: true,
            pageSettings: { pageSize: 8 }
        });
        this.element.find(".e-clientDialog").ejDialog({ width: "70%", content: "#" + this._id, enableResize: false, close: ej.proxy(ej.Pivot.closePreventPanel, this) });
        var pivotClient = $("#" + this._id).data("ejPivotClient");
        $("#btnOK").click(function () {
            ej.Pivot.openHierarchySelector(pivotClient);
        });
    }
</script>

{% endhighlight %}

![](DrillThrough_images/drill_data.png)
