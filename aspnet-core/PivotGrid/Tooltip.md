---
layout: post
title:  ToolTip
description: ToolTip
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Tooltip

Allows you to display the details of cell on hovering the value cells. By default, the tooltip is enabled. You can disable the tooltip in pivot grid by setting the `enable-tool-tip` property to false.

{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1" enable-tool-tip="false" ></ej-pivot-grid>

{% endhighlight %}


## Tooltip animation

The pivot grid provides option to animate tooltip that is displayed in the grid. The animation enhances the appearance of the tooltip by displaying it slowly. You can enable the animation in tooltip by setting the `enable-tool-tip-animation` property to true.


{% highlight cshtml %}

<ej-pivot-grid id="PivotGrid1" enable-tool-tip-animation="false" ></ej-pivot-grid>

{% endhighlight %}

![](ToolTip_images/ToolTip.png)
