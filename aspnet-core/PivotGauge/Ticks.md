---
layout: post
title: Ticks
description: ticks
platform: aspnet-core
control: PivotGauge
documentation: ug
---

# Ticks

## Adding Tick Collection

Tick collection can be directly added to the scales option within the PivotGauge control.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>
            <e-tick-collections>
                <e-ticks type="Major"></e-ticks>
            </e-tick-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight %}

## Tick Customization

The appearance of the tick can be customized through the following properties.

* **Type** – indicates whether ticks are for major or minor intervals. By default, the type is "Major".
* **Height** – sets the height of the ticks.
* **Width** – sets the width of the ticks.
* **Angle** – rotates the ticks to a specified angle. By default, the angle value is 0.
* **Color** – displays the ticks in specified color.
* **DistanceFromScale** – sets the distance between scale and ticks. By default, the values is 0.
* **Placement** – positions the ticks with respect to the scale.  By default, the value is set to "Far".

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>
            <e-tick-collections>
                <e-ticks type="Major" height="15" width="4" angle="0" placement="Near" distance-from-scale="2" color="green"></e-ticks>
            </e-tick-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight %}

![](Ticks_images/TickCustomization.png) 

