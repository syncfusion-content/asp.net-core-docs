---
layout: post
title: Appearance and Styling | Tab  | ASP.NET Core | Syncfusion
description: appearance and styling
platform: ASP.NET Core
control: Tab 
documentation: ug
---

# Appearance and Styling

## Header Image Customization

To set the Tab header image for each Tab item you need to specify image in “ImageCssClass” property during the TabItem declaration.

The following code example is used to add the header image for the root Tab header element. 

1. Add the following code in your view page to render Tab with header image.

{% highlight CSHTML %}

   <div id="dishtab" style="width:550px">

        <ul>

            <li><span class="dish pizzaImg"></span><a href="#pizzatype">Pizza Type</a></li>

            <li><span class="dish sandwichImg"></span><a href="#sandwichtype">Sandwich Type</a></li>

        </ul>

        <div id="pizzatype" style="background-color: #F5F5F5">

            <p>Pizza cooked to perfection tossed with milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</p>

        </div>

        <div id="sandwichtype" style="background-color: #F5F5F5">

            <p>Sandwich cooked to perfection tossed with bread, milk, vegetables, potatoes, poultry, 100% pure mutton, and cheese - and in creating nutritious and tasty meals to maintain good health.</p>

        </div>

        <ej-tab id="dishtab"></ej-tab>

    </div>

{% endhighlight %}

2. Add following CSS for header image customization.

{% highlight CSHTML %}

	<style type="text/css" class="cssStyles">

		.dish 
		{

			display: inline-block;

			vertical-align: middle;

			margin: 0px -9px 0px 9px;           

		}

		.pizzaImg 
		{

			background: url("http://js.syncfusion.com/UG/Web/Content/rsz_chicken-delite.png") no-repeat;

			height: 25px;

			width: 25px;

		}

		.sandwichImg, .pastaImg {

			height: 25px;

			width: 25px;

		}

		.sandwichImg 
		{

			background: url("http://js.syncfusion.com/UG/Web/Content/rsz_garden-fresh.png") no-repeat;

		}

	</style> 

{% endhighlight %}
   
3. The following screenshot illustrates the Tab with the customized header image. 

![](Appearance-and-Styling_images/Appearance-and-Styling_img1.png)

Header Image Customization
{:.caption}

## Rounded corner

By enabling ‘ShowRoundedCorner’ property, you can customize the shape of the Tab widget from regular rectangular shape to rounded rectangle shape that is set to ‘false’ by default. 

The following code example is used to render the Tab widget with rounded corner.

1. Add the following code in your view page to render Tab with rounder corner.

{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Tab with rounded corner.
<div style="width: 550px">

	<ej-tab id="tabSample" show-rounded-corner="true">
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

2. The following screenshot illustrates the Tab with Rounded corner.

![](Appearance-and-Styling_images/Appearance-and-Styling_img2.png)

Tab with rounded corner
{:.caption}

## Enable/Disable

You can enable or disable the Tab widget by ‘Enabled’ property. By default, the property set to ‘true’.

The following code example is used to render the Tab widget with enable/disable.

1. Add the following code in your view page to render Tab with enable/disable.

{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Tab with Enable/Disable format.

<div style="width: 550px">

<ej-tab id="tabSample" enabled="false">
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

2. The following screenshot illustrates the Tab with disabled format.

![](Appearance-and-Styling_images/Appearance-and-Styling_img3.png)

Tab with disabled format
{:.caption}


## Enabling Reload Icon

Without refresh/reload the whole page, you can reload a particular Tab using Reload icon. The Reload icon is appeared at right corner of the Tab by enabling the property ‘ShowReloadIcon’ to ‘true’. When you move cursor over the Tab headers, the Reload icon is displayed. By default the property value is set to ‘false’.   

The following code example is used to render the Tab widget with Reload icon.

1. Add the following code in your view page to render Tab with Reload icon.

{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Tab with reload icon.
<div style="width: 550px">

<ej-tab id="tabSample" show-reload-icon="true">
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

2. The following screenshot illustrates the Tab with Reload icon.

![](Appearance-and-Styling_images/Appearance-and-Styling_img4.png)

Tab with reload icon

{:.caption}

## Collapsible Tabs

You can collapse the Tab content by enabling the ‘Collapsible’ property to ‘true’. When the property is set to ‘true’ then click the active Tab header, the Tab contents are hided. By default, the property value is set to ‘false’.

The following code example is used to render the Tab widget with customized collapsible mode.

1. Add the following code in your view page to render Tab with customized collapsible mode.

{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Tab with collapsible mode.

<div style="width: 550px">

<ej-tab id="tabSample" collapsible="true">
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

2. The following screenshot illustrates the Tab with customized collapsible mode.

![](Appearance-and-Styling_images/Appearance-and-Styling_img5.png)

Tab with customized collapsible mode
{:.caption}


## Adjusting Tab Size

### Height Adjust Mode and Height

The height of the Tab widget is customized by ‘height’ property. The Tab widget height depends on ‘HeightAdjustMode’ property. Using the HeightAdjustMode property, you can adjust height by “Content”, “Auto”, “Fill”. By default the HeightAdjustMode is set as content.

The following code example is used to render the Tab widget with customized height and height adjust mode.

1. Add the following code in your view page to render Tab with customized height and height adjust mode.

{% highlight CSHTML %}

	// Add the following code example to the corresponding CSHTML page to render Tab with customized height and height adjust mode.
    <div style="width: 550px">

        <ej-tab id="tabSample" height="300px" height-adjust-mode="@HeightAdjustMode.Fill">
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

2. The following screenshot illustrates the Tab with customized height and height adjust mode.

![](Appearance-and-Styling_images/Appearance-and-Styling_img6.png)


Tab with customized height and height adjust mode
{:.caption}

### Width

The width of the Tab widget is customized by using ‘Width’ property that accepts only the pixel values.

The following code example is used to render the Tab widget with customized width.

1. Add the following code in your view page to render Tab with customized width.

{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Tab with customized width.
<div>

<ej-tab id="tabSample" width="450">
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
   
2. The following screenshot illustrates the Tab with customized width.

![](Appearance-and-Styling_images/Appearance-and-Styling_img7.png)' 

Tab with customized width
{:.caption}

## Theme

Tab control’s style and appearance are controlled based on CSS classes. In order to apply styles to the Tab control, you can refer 2 files namely, ej.widgets.core.min.css and ej.theme.min.css. When the file ej.widgets.all.min.css is referred, then it is not necessary to include the files ej.widgets.core.min.css and ej.theme.min.css in your project, as ej.widgets.all.min.css is the combination of these two. 

By default, there are 13 themes support available for Tab control namely

* default-theme
* bootstrap-theme
* flat-azure-dark
* fat-lime
* flat-lime-dark
* flat-saffron
* flat-saffron-dark
* gradient-azure
* gradient-azure-dark
* gradient-lime
* gradient-lime-dark
* gradient-saffron
* gradient-saffron-dark

## Custom styles

The style of the Tab widget is customized by ‘CssClass’ property. 

The following code example is used to render the Tab widget with customized style.

1. Add the following code in your view page to render Tab with customized style.

{% highlight CSHTML %}

// Add the following code example to the corresponding CSHTML page to render Tab with customized style.

<div style="width: 550px">

<ej-tab id="tabSample" css-class="custom">
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

2. Add the following styles

{% highlight css %}

	<style type="text/css">

		.custom 
		{
			width:650px;
		}

	</style>

	{% endhighlight %}

3. The following screenshot illustrates the Tab with customized style.

![](Appearance-and-Styling_images/Appearance-and-Styling_img8.png)

Tab with customized style
{:.caption}