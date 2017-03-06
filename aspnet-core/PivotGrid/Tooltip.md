---
layout: post
title:  ToolTip
description: ToolTip
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# ToolTip

Allows you to display the details of the cell on hovering value cells. By default, tooltip is enabled.  You can disable tooltip in PivotGrid by setting the `enableToolTip` property to false.

{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1" enable-tool-tip="false" ></ej-pivot-grid>

{% endhighlight %}


## ToolTip Animation

The PivotGrid provides option to animate tooltip displayed in the grid.  The animation enhances the appearance of tooltip by displaying it slowly.  You can enable animation in tooltip by setting `EnableToolTipAnimation` property to true.


{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1" enable-tool-tip-animation="false" ></ej-pivot-grid>

{% endhighlight %}

![](ToolTip_images/ToolTip.png)
