---
layout: post
title: Dimension | RadialSlider | ASP.NET MVC | Syncfusion
description: dimension
platform: ejmvc
control: RadialSlider
documentation: ug
---

# Dimension

## Stroke Width

**Radial Slider** StrokeWidth property specifies the width of the outline . By default, the **Radial slider** StrokeWidth is set as 2. Refer to the following code example.

{% highlight CSHTML %}

    @Html.EJ().RadialSlider("slider").StrokeWidth(4).InnerCircleImageUrl("../images/radialslider/chevron-right.png")
    
{% endhighlight %}

The following screenshot illustrates the output of the above code.

![](dimension_images\dimension_img1.png)

## Setting radius

The **RadialSlider** property **Radius**  indicates the radius of the RadialSlider's circle ant its allow to change radius value.  By default, the **Radial Slider** Radius is set to 200. Refer to the following code example.

{% highlight CSHTML %}

    @Html.EJ().RadialSlider("slider").Radius(250)

{% endhighlight %}



