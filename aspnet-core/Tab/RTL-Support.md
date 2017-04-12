---
layout: post
title: RTL Support | Tab  | ASP.NET Core | Syncfusion
description: rtl support
platform: aspnet-core
control: Tab 
documentation: ug
---

# RTL Support

Tab control provides support for load contents in right to left format. This is achieved by setting ‘EnableRTL’ property to “true”.

The following code example is used to render the Tab element in RTL format. 

1. Add the following code in your view page to render Tab with RTL format.

{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Tab in Rtl format.
<div style="width: 500px">

    <ej-tab id="tabSample" enable-rtl="true">
        <e-tab-items>
            <e-tab-item id="pizzatype" text="Pizza Type">
                <e-content-template>
                    <div>
                        Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.
                    </div>
                </e-content-template>
            </e-tab-item>
            <e-tab-item id="sandwichtype" text="Sandwich Type">
                <e-content-template>
                    <div>
                        Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.
                    </div>
                </e-content-template>
            </e-tab-item>
        </e-tab-items>
    </ej-tab>

</div>

{% endhighlight %}

2. The following screenshot illustrates the Tab with RTL format.

![](RTL-Support_images/RTL-Support_img1.png)