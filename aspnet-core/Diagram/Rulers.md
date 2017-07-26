---
layout: post
title: Ruler is used to measure the distance of nodes and connectors from origin of the page.
description:  how to measure the distance of Nodes and Connectors?
platform: aspnet-core
control: Diagram
documentation: ug
---


# Rulers

The Ruler provides a Horizontal and Vertical guide for measuring in the Diagram control. The Ruler can be used to measure the Diagram objects, indicate positions, and align Diagram elements. This is especially useful in creating scale models. 

## Adding Rulers to the Diagram
Use the following code example to add the ruler to the Diagram.

{% highlight razor %}

     <ej-diagram id="diagram" width="1000px" height="600px" enable-context-menu="false">
         <e-ruler-settings show-rulers="true">
         </e-ruler-settings>
     </ej-diagram>

{% endhighlight %}

![](/aspnet-core/Diagram/Rulers_images/Rulers_images1.png)

## Customizing the Ruler

By default, ruler segments are arranged based on measurement units.

Segment width, the textual description of the ruler segment, and the appearance of the ruler ticks can be customized. Use the following code example to customize the ruler.
 {% tabs %}
{% highlight razor %}

     <ej-diagram id="diagram" width="1000px" height="600px" enable-context-menu="false">
         <e-ruler-settings show-rulers="true">
             <e-horizontal-ruler interval="6" marker-color="blue" segment-width="100" thickness="25" tick-alignment="LeftOrTop" arrange-tick="arrangeTick"></e-horizontal-ruler>
             <e-vertical-ruler interval="6" marker-color="blue" segment-width="100" thickness="25" tick-alignment="LeftOrTop" arrange-tick="arrangeTick"></e-vertical-ruler>
         </e-ruler-settings>
     </ej-diagram>


{% endhighlight %}

{% highlight js %}

function arrangeTick(args) {
	// Customizing the Ruler ticks.
    if (args.tickInterval % 100 == 0) {
    }
    else if (args.tickInterval % 50 == 0) {
        args.tickLength = 12.5
    }
}

{% endhighlight %}

{% endtabs %}

![](/aspnet-core/Diagram/Rulers_images/Rulers_images2.png)

