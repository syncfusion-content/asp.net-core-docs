---
layout: post
title: Custom labels
description: custom labels
platform: aspnet-core
control: PivotGauge
documentation: ug
---

# Custom labels

## Adding Custom Label Collection

You can apply custom custom label Collection by using `CustomLabelCollection` which can be directly added to the scales option within the PivotGauge control.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>
            <e-custom-label-collections>
                <e-circular-custom-labels>
                    <e-custom-position x="180" y="290"></e-custom-position>
                </e-circular-custom-labels>
            </e-custom-label-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight %}

## Appearance Customization

The appearance of the custom labels can be changed through the following properties.

* **Position** – used to set the position of the labels.
* **Font** – sets the font size, font style and font family of the label text.
* **Color** – sets the color of the label text.
* **TextAngle** – rotates the label to a specified angle. By default, the value is 0.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>
            <e-custom-label-collections>
                <e-circular-custom-labels color="blue" text-angle="20">
                    <e-custom-position x="180" y="320"></e-custom-position>
                    <e-custom-font size="12px" font-family="Segoe UI" font-style="Normal"></e-custom-font>
                </e-circular-custom-labels>
            </e-custom-label-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight %}

![](Custom-Label_images/AppearanceCustomization.png) 

## Multiple Custom Labels

Multiple ranges can be added in `CustomLabelCollection` to the scales option within the PivotGauge control.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>
            <e-custom-label-collections>
                <e-circular-custom-labels color="red">
                    <e-custom-position x="180" y="150"></e-custom-position>
                    <e-custom-font size="12px" font-family="Segoe UI" font-style="Normal"></e-custom-font>
                </e-circular-custom-labels>
                <e-circular-custom-labels color="green">
                    <e-custom-position x="180" y="320"></e-custom-position>
                    <e-custom-font size="10px" font-family="Segoe UI" font-style="Normal"></e-custom-font>
                </e-circular-custom-labels>
                <e-circular-custom-labels color="blue">
                    <e-custom-position x="180" y="290"></e-custom-position>
                    <e-custom-font size="10px" font-family="Segoe UI" font-style="Normal"></e-custom-font>
                </e-circular-custom-labels>
            </e-custom-label-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight %}

![](Custom-Label_images/MultipleCustomLabels.png) 