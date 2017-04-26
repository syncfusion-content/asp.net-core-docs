---
layout: post
title: Levels
description: Learn how to customize various levels in SunburstChart
platform: aspnet-core
control: SunburstChart
documentation: ug
---

## Levels

Sunburst chart is used to display hierarchical data. You can add more than one hierarchical data by using the **e-sunburstchart-levels** property of Sunburst chart. Each level of the hierarchy is represented by circle.
The following code snippet illustrates 

{% highlight cshtml %}

<ej-sunburstchart id="SunburstChart" >
  <e-sunburstchart-levels>
               // to add heirarchical levels of data
            </e-sunburstchart-levels>
<ej-sunburstchart>

{% endhighlight %}

## GroupMemberPath

It is the string property that is used to map the group category value in the dataSource .
You can define the levels as shown in the below code example

{% highlight cshtml %}

<ej-sunburstchart id="SunburstChart" >
<e-sunburstchart-levels>
<e-sunburstchart-level group-member-path="Level1"></e-sunburstchart-level>
<e-sunburstchart-level group-member-path="Level2"></e-sunburstchart-level>
<e-sunburstchart-level group-member-path="Level3"></e-sunburstchart-level>
</e-sunburstchart-levels>
<ej-sunburstchart>

 {% endhighlight %}

The following screenshot illustrates the Sunburst Chart with different levels

![](Levels_images/Levels_img1.png)
