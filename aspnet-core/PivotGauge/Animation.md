---
layout: post
title: Animation
description: animation
platform: aspnet-core
control: PivotGauge
documentation: ug
---

# Animation

The animation option makes the pointer to rotate from minimum value to actual value with animation effects.  Animation could be enabled/disabled by using the `EnableAnimation` property.  Speed of the pointer could be controlled by using the `AnimationSpeed` property. Time is represented in milliseconds.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1" enable-animation="true" animation-speed="1000"></ej-pivot-gauge>

{% endhighlight %}

