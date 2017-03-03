---
layout: post
title: Pointers
description: pointers
platform: aspnet-core
control: PivotGauge
documentation: ug
---

# Pointers

## Pointer Types

PivotGauge pointers has two types such as,

* Needle
* Marker

Needle type pointers are the default pointers which is always located at the center of the Gauge. Following shapes that are supported for the needle pointers are:

* Rectangle
* Triangle
* Trapezoid
* Arrow
* Image.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>
            <e-pointer-collections>
                <e-pointers type="Needle" marker-type="Trapezoid"></e-pointers>
            </e-pointer-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight %}

![](Pointers_images/NeedlePointer.png) 

For marker pointer, the available shapes are Rectangle, Triangle, Ellipse, Diamond, Pentagon, Circle, Slider, Pointer, Wedge, Trapezoid, RoundedRectangle and Image.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>
            <e-pointer-collections>
                <e-pointers type="Marker" marker-type="Diamond"></e-pointers>
            </e-pointer-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight %}

![](Pointers_images/MarkerPointer.png) 

## Adding Pointer Collection

Pointer collection can be directly added to the scales option within the PivotGauge control. 

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>
            <e-pointer-collections>
                <e-pointers type="Needle" marker-type="Triangle"></e-pointers>
                <e-pointers type="Marker" marker-type="Diamond"></e-pointers>
            </e-pointer-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight  %}

![](Pointers_images/AddingPointerCollection.png)

## Appearance Customization

The appearance of the pointer can be customized through the following properties.

* **Border** – sets the “Color” and “Width” of the pointer border.
* **BackgroundColor** – sets the background color of the pointer.
* **Length** – sets the length of the pointer.
* **Width** – sets the width of the pointer.
* **Opacity** – sets the opacity of the pointer.  By default, the value is 1.
* **Type** – sets the type of the pointer.  By default, the type is “Needle”.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>  
            <e-pointer-collections>
                //For customizing needle pointer
                <e-pointers type="Needle" marker-type="Triangle" background-color="yellow" length="120" width="7" opacity="60">
                    <e-border color="green" width="2"></e-border>
                </e-pointers>
                //For customizing marker pointer
                <e-pointers type="Marker" marker-type="Diamond" background-color="yellow" length="25" width="15" opacity="80">
                    <e-border color="green" width="2"></e-border>
                </e-pointers>
            </e-pointer-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight %}

![](Pointers_images/AppearanceCustomization.png) 

## Pointer Position

Pointer can be positioned with the help of below two properties.

* **DistanceFromScale** -  defines the distance between scale and pointer. By default, the value is 0.
* **Placement** -  defines the location of the pointer. By default, the value is “Center”.

N> Both the properties can be applied only if the pointer type is set to “Marker”. Needle pointer type appears only at the center of the control, which is its default position.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>  
            <e-pointer-collections>
                <e-pointers type="Marker" distance-from-scale="2" placement="Far"></e-pointers>
            </e-pointer-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight %}

![](Pointers_images/PointerPosition.png)

## Pointer Image

It is possible to replace the pointers with image. To view the pointers as image, we need to set the appropriate location in the `ImageUrl` property.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>  
            <e-pointer-collections>
               //For replacing needle pointer with image
                <e-pointers type="Needle" needle-type="Image" image-url="../image.png"></e-pointers>
                //For replacing marker pointer with image
                <e-pointers type="Marker" marker-type="Image" image-url="../image.png"></e-pointers>
            </e-pointer-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight %}

![](Pointers_images/PointerImage.png)

## Pointer Value Text

To display the current value of the pointers in PivotGauge control, **"PointerValueText"** option inside pointers is used.  Following are the properties used to enable and customize the pointer value text.
 
* **ShowValue** – enables the pointer value text by setting the property to “true”. By default, its value is “true”.
* **Distance** – sets the distance between pointer and text.
* **Color** – sets the color of the text.
* **Opacity** – sets the opacity of the text. By default, its value is 1.
* **Angle** – sets the rotation angle of the text. By default, its value is 0.
* **Font** – sets the font size, font style and font family of the text.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1">
    <e-scales>
        <e-circular-scales>  
            <e-pointer-collections>
                <e-pointers type="Needle">
                //For needle type
                    <e-pointer-value-text show-value="true" distance="10" color="red" opacity="70" angle="20">
                        <e-font font-family="Arial" font-style="Normal" size="15px"></e-font>
                    </e-pointer-value-text>
                </e-pointers>
                <e-pointers type="Marker">
                //For marker type
                    <e-pointer-value-text show-value="true" distance="40" color="red" opacity="70" angle="-40">
                        <e-font font-family="Arial" font-style="Normal" size="15px"></e-font>
                    </e-pointer-value-text>
                </e-pointers>
            </e-pointer-collections>
        </e-circular-scales>
    </e-scales>
</ej-pivot-gauge>

{% endhighlight %}

![](Pointers_images/PointerValueText.png)