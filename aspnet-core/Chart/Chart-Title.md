---
layout: post
title: Chart Title |Chart  | ASP.NET CORE | Syncfusion
description: How to customize the chart title.
platform: aspnet-core
control: Chart
documentation: ug
---

# Chart Title & Subtitle

## Title

By using the **Title** option, you can add the *Text* as well as customize its *Border, Background and Font*.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    <e-title text="Efficiency of oil-fired power production" background="lightblue">
        <e-Border color="blue" width="2" opacity="0.5" corner-radius="4.0"></e-Border>
        <e-Font opacity="1" font-family="Arial" color="#E27F2D" font-size="23px" font-style="Italic" font-weight="Regular"></e-Font>
    </e-title>
</ej-chart>

{% endhighlight %}

![](Chart-Title_images/Chart-Title_img1.png)

We can trim, wrap and wrapAndTrim to the chart title using textOverflow property. The original text will be displayed as tooltip on mouse hover.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    <e-title text="Efficiency of oil-fired power production" enable-trim="true" maximum-width="150" text-overflow="Trim">
    </e-title>
</ej-chart>

{% endhighlight %}

![](Chart-Title_images/Chart-Title_img5.png)

### Title Alignment

You can change the title alignment to *Center*, *Far* and *Near* by using the **TextAlignment** property of the chart title. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    <e-title text="Efficiency of oil-fired power production" text-alignment="Far">
    </e-title>
</ej-chart>

{% endhighlight %} 

![](Chart-Title_images/Chart-Title_img2.png)


## Add Subtitle to the chart

By using the **SubTitle** option, you can add the SubTitle to the chart title and customize its *Border, Background and Font*. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    <e-title text="Efficiency of oil-fired power production" background="lightblue">
        <e-SubTitle text="in a week"></e-SubTitle>
        <e-Border color="blue" width="2" corner-radius="4.0" opacity="0.2"></e-Border>
        <e-Font opacity="1" font-family="Arial" font-style="Italic" color="#E27F2D" font-size="12px" font-weight="Regular"></e-Font>
    </e-title>
</ej-chart>

{% endhighlight %}

![](Chart-Title_images/Chart-Title_img3.png)

We can trim, wrap and wrapAndTrim to the chart subtitle using textOverflow property. The original text will be displayed as tooltip on mouse hover.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    <e-title text="Efficiency of oil-fired power production" enable-trim="true" maximum-width="150" text-overflow="Wrap">
        <e-SubTitle text="In a Week"></e-SubTitle>
    </e-title>
</ej-chart>

{% endhighlight %}

![](Chart-Title_images/Chart-Title_img6.png)

### Subtitle Alignment

You can change the SubTitle alignment to *Center*, *Far* and *Near* by using the **TextAlignment** property of the SubTitle.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    <e-title>
        <e-SubTitle text-alignment="Center"></e-SubTitle>
    </e-title>
</ej-chart>

{% endhighlight %}

![](Chart-Title_images/Chart-Title_img4.png)