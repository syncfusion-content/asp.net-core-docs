---
layout: post
title: Scroll Support | Tab  | ASP.NET Core | Syncfusion
description: scroll support
platform: aspnet-core
control: Tab 
documentation: ug
---

# Scroll Support

Tab control provides you scrolling support on Tab items to display a larger number of tabs with scroll buttons to get rid of the extending page size. The enabled Scroll buttons can be used to traverse through the elements.

By default, Tab header is rendered without scroll button. You can add the scroll button by setting the "EnableTabScroll" property to "true". When you move the cursor over the Tab header the scroll button is displayed.   

You can use the following code example to render the Tab widget with scroll button.

1. Add the following code in your view page to create a simple Tab with scroll button.

{% highlight CSHTML %}

@*Add the following code example to the corresponding CSHTML page to render Tab with scroll button.*@

<div style="width: 500px">

    <ej-tab id="tabSample" enable-tab-scroll="true">
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
            <e-tab-item id="pastatype" text="Pasta Type">
                <e-content-template>
                    <div>
                        Pasta cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.
                    </div>
                </e-content-template>
            </e-tab-item>
            <e-tab-item id="burgertype" text="Burger Type">
                <e-content-template>
                    <div>
                        Burger cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.
                    </div>
                </e-content-template>
            </e-tab-item>
            <e-tab-item id="spaghettitype" text="Spaghetti Type">
                <e-content-template>
                    <div>
                        Spaghetti cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.
                    </div>
                </e-content-template>
            </e-tab-item>
            <e-tab-item id="ramentype" text="Ramen Type">
                <e-content-template>
                    <div>
                        Ramen cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.
                    </div>
                </e-content-template>
            </e-tab-item>
        </e-tab-items>
    </ej-tab>

</div>

{% endhighlight %}

The following screenshot illustrates you the Tab control with scroll button. 

![](Scroll-Support_images/Scroll-Support_img1.png)

Tab control with scroll support
{:.caption}