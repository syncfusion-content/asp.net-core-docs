---
layout: post
title: Interaction and Animation | CircularGauge | Syncfusion
description: interaction and animation
platform: aspnet-core
control: CircularGauge
documentation: ug
---

# Interaction and Animation

## Interaction

* Circular Gauge control contains Interaction feature. You can use this interaction feature to change the pointer values manually. You can achieve this by clicking and dragging the pointer over the Gauge and you can see the value of pointer changes dynamically while dragging.
* To Enable/Disable the user interaction you can use the Boolean property called `read-only`. The user interaction option is enabled when you set the value as false for the property readOnly.By default it holds the true value.That is by default it does not support interaction. 

{% highlight CSHTML %}

<ej-circular-gauge id="circulargauge" read-only="false" >
</ej-circular-gauge>

{% endhighlight  %}

Execute the above code to render the following output.



![](Interaction-and-Animation_images/Interaction-and-Animation_img1.png)

Circular Gauge with basic interaction property
{:.caption}

## Animations

* Circular Gauge contains an attractive concept called Animation. The animation option enables the pointer to rotate from the minimum value to the current value with animation effects. By using this animation you can change the pointer value dynamically.You can apply the animation on  pointer either by clockwise or counterclockwise based on the scale direction. 
* You can enable / disable it using the property `enable-animation`. Animation is enabled when you set enable-animation as ‘true’. By default it holds the true value. You can control the speed of the pointer during animating by using the property `animation-speed`. It is a numerical value that holds the time in milliseconds. That is when the value is given as 1000, it is considered as 1 second.

{% highlight CSHTML %}

<ej-circular-gauge id="circulargauge" enable-animation=true animation-speed="1000" >
</ej-circular-gauge>

{% endhighlight  %}

Execute the above code to render the following output.



![](Interaction-and-Animation_images/Interaction-and-Animation_img2.png)

Circular Gauge with basic Animation property
{:.caption}




