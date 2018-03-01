---
layout: post
title: Responsive Layout
description: responsive layout
platform: aspnet-core
control: PivotClient
documentation: ug
---

# Responsive layout

The pivot client widget supports responsive rendering based on the target device (desktop and tablet) resolution. It supports resolution up to 1024x600. You can enable responsiveness in the pivot client by setting the `is-responsive` property to true.

{% highlight CSHTML %}

<ej-pivot-client id="PivotClient1" is-responsive="true">
   //..
</ej-pivot-client>

{% endhighlight %}

![](Responsive-Layout_images/responsive.png)
