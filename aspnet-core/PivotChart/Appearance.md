---
layout: post
title: Appearance
description: appearance
platform: aspnet-core
control: PivotChart
documentation: ug
---

# Appearance

## Built-in themes

Following are the built-in themes available in the pivot chart:

* flatlight
* gradientlight
* gradientdark
* azure
* azuredark
* lime
* limedark
* saffron
* saffrondark
* gradientlight
* gradientdark
* highcontrast01
* highcontrast02
* material
* office365
* bootstrap

By using the `theme` property, you can set the desired theme in the pivot chart. By default, the **"FlatLight"** theme is applied to the pivot chart.

{% highlight cshtml %}

//Using gradient theme
<ej-pivot-chart id="PivotChart1" theme="LimeDark"></ej-pivot-chart>

{% endhighlight %}

![](Appearance_images/themes.png)

## Pivot chart - area customization

### Border customization

To customize the pivot chart border, use `border` property in the pivot chart.

{% highlight cshtml %}

//Customize the chart border and opacity
<ej-pivot-chart id="PivotChart1" border-width="2" border-color="#FF0000"></ej-pivot-chart>

{% endhighlight %}

![](Appearance_images/bordercustomize.png)

### Animation

You can enable the animation by using the `enable-animation` property under `e-common-series-options` of the pivot chart control. This animates the chart series on two occasions - when the chart is loaded for the first time and when the series type is changed by using the `type` property.

{% highlight cshtml %}

<ej-pivot-chart id="PivotChart1">
    <e-common-series-options enable-animation="true"></e-common-series-options>
    //Enabling animation in series
    <e-size width="100%" height="460px"></e-size>
</ej-pivot-chart>

{% endhighlight %}   
