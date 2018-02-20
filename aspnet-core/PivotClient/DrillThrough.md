---
layout: post
title:  Drill Through
description:  drill through
platform: aspnet-core
control: PivotClient
documentation: ug
---

# Drill through

The drill-through retrieves raw items that are used to create a specified cell. To enable drill-through support, set [`enable-drill-through`] property to true. Raw items are obtained through the [`drill-through`] event, using which you can bind them to an external widget for a precise view.

N> The drill-through is supported in the pivot grid only when you configure and enable the drill-through action at the cube.

![](DrillThrough_images/pivotclient.png)

When any value cell is clicked, the Drill Through Information dialog will open. It consists of a grid with the data associated with the measure values of the clicked value cell. In this example, the measure behind the respective cell is “Sales Amount” and the values of the dimensions associated with this measure are displayed in the grid.

![](DrillThrough_images/DrillThroughData.png)

When the Hierarchy Selector displayed below the grid is clicked, the Hierarchy Selector dialog will open. It consists of dimensions associated with the measure of a clicked value cell. In this example, the measure behind the respective cell is “Sales Amount” and the dimensions associated with this measure are alone displayed in the dialog.

![](DrillThrough_images/hierarchy_selector.png)

Dragg and drop the respective hierarchies and click OK. The drill-through MDX query will be framed and executed internally and provides back raw items through the "drill-through" event. In this example, the obtained raw items are bound to the ejGrid widget. Refer to the following code sample and screenshot:

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
