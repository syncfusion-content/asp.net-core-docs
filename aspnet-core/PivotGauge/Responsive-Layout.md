---
layout: post
title: Responsive Layout
description: responsive layout
platform: aspnet-core
control: PivotGauge
documentation: ug
---

# Responsive Layout

PivotGauge control supports responsive rendering based on the target device (desktop & tablet) resolution. It supports resolution upto 1024x600. You can enable responsiveness in PivotGauge by setting `IsResponsive` property to true.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1" is-responsive="true"></ej-pivot-gauge>

{% endhighlight %}

![](Responsive-Layout_images/Responsive1.png) 

_Normal View_


![](Responsive-Layout_images/Responsive2.png) 

_Responsive View_