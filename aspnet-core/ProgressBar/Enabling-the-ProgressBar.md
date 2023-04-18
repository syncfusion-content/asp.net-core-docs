---
layout: post
title: Enabling the ProgressBar | Progress Bar | ASP.NET Core | Syncfusion
description: Learn here about enabling the progressbar in Syncfusion Essential ASP.NET Core Progress Bar Control, its elements, and more.
platform: aspnet-core
control: Progress Bar
documentation: ug
---

# Enabling the ProgressBar in ASP.NET Core

The ProgressBar is enabled by using the ‘Enabled’ Property. When this property is set to ‘false’, it disables the ProgressBar widget. By default, ‘Enabled’ property is set to ‘true’ in the ProgressBar widget.

The following steps explain how to disable the ProgressBar widget when ‘Enabled’ property is set to ‘false’.

1. In the VIEW page, add the below code to render the ProgressBar widget.

{% highlight CSHTML  %}

// Add the following code example to the corresponding CSHTML page to disable the ProgressBar control.

<ej-progress-bar id="progressBar" value="70" text="70%" enabled="false" height="20" width="500"/>

{% endhighlight %}

The following screenshot displays the output for the above code.

![ASP.NET Core Progress Bar enable](Enabling-the-ProgressBar_images/Enabling-the-ProgressBar_img1.png)

Disabled Progress Bar
{:.caption}