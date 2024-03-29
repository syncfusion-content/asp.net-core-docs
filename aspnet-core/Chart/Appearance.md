---
layout: post
title: Customizing Chart appearance |Chart  | ASP.NET CORE | Syncfusion
description: Learn how to customize the appearance of Chart using palettes, themes, color, background and animation. 
platform: aspnet-core
control: Chart
documentation: ug
---

# Appearance

## Custom color palette

The chart displays different series in different colors, by default. You can customize the color of each series by providing a custom color palette by using the **Palette** property. 

{% highlight cshtml %}

    @{
        List<string> palette = new List<string> { "Grey", "Skyblue", "Yellow" };
    }
    <ej-chart id="container" palette="palatte">
    </ej-chart>

{% endhighlight %}


![Custom color palette in ASP.NET Core Chart](appearance_images/aspnetcore-chart-custom-color-palette.png)


N> The color palette is applied to the points in accumulation type of series

## Built-in themes

The built-in themes available in the chart are follows:

* Azure
* Azure dark
* Flat dark
* Flat light
* Gradient dark
* Gradient light
* Lime
* Lime dark
* Saffron
* Saffron dark

You can set the desired theme by using the **Theme** property. The default theme is **FlatLight**.

{% highlight cshtml %}

    <ej-chart id="container" theme="GradientLight">
    </ej-chart>

{% endhighlight %}

![Themes in ASP.NET Core Chart](appearance_images/aspnetcore-chart-themes.png)


## Point level customization

Marker, data label, and fill color of each point in a series can be customized individually by using the **Points** collection.

{% highlight cshtml %}

<ej-chart id="container">
        //..
    <e-series name="Silver"><e-marker visible="true"></e-marker>
            <e-points>
                <e-point x="USA" y="50" fill="#E27F2D"></e-point>
             </e-points>
        </e-series>
        //..
</ej-chart>

{% endhighlight %}

![Point level customization in ASP.NET Core Chart](appearance_images/aspnetcore-chart-point-level-customization.png)


## Series border customization

To customize the series border color, width, and dash array, use **Series.Border** option. The series border styles can be applied only to the column, bar, and area type of series.

{% highlight cshtml %}

<ej-chart id="container">
        //..
        <e-series name="Silver"><e-border color="blue" width="2" dash-array="5,3"></e-border>
        
        //..
        </e-series>
        //..
</ej-chart>

{% endhighlight %}

![Series border customization in ASP.NET Core Chart](appearance_images/aspnetcore-chart-series-border-customization.png)


## Chart area customization

### Customize chart background

The chart background can be customized by using the **Background** property. To customize the chart border, use **Border** option of the chart. 

{% highlight cshtml %}

<ej-chart id="container" background="skyblue"><e-border color="#FF0000" width="2" opacity="0.35"></e-border>
//..
</ej-chart>

{% endhighlight %} 

![Customize chart background in ASP.NET Core Chart](appearance_images/aspnetcore-chart-customization-background.png)


**Chart Margin**

**Margin** property is used to add margin to the chart area at the Left, Right, Top, and Bottom positions.

{% highlight cshtml %}

<ej-chart id="container"><e-margin left="40" right="40" top="40" bottom="40"></e-margin>
//..
</ej-chart>


{% endhighlight %} 

![Chart margin in ASP.NET Core](appearance_images/aspnetcore-chart-margin.png)


**Setting background image**

Background image can be added to the chart by using the **BackGroundImageUrl** property.

{% highlight cshtml %}

<ej-chart id="container" back-ground-image-url="images/chart/wheat.png">
//..
</ej-chart>

{% endhighlight %} 

![Setting background image in ASP.NET Core Chart](appearance_images/aspnetcore-chart-setting-background-image.png)


**Chart area background**

The chart area background can be customized by using the **Background** property. 

{% highlight cshtml %}

<ej-chart id="container">
//..
    <e-chart-area background="skyblue"></e-chart-area>
//..

</ej-chart>

{% endhighlight %} 

![Chart area background in ASP.NET Core](appearance_images/aspnetcore-chart-area-background.png)


### Customize chart area grid bands

You can provide different color for alternate grid's rows and columns formed by the grid lines in the chart area by using the **AlternateGridBand** property of the axis. The properties **Odd** and **Even** are used to customize the grid bands at odd and even positions, respectively. 

{% highlight cshtml %}

<ej-chart id="container">
//..
    <e-primary-y-axis><e-alternate-grid-band><e-even fill="#A7A9AB" opacity="0.1"></e-even></e-alternate-grid-band>
//..

</ej-chart>

{% endhighlight %} 

![Customize chart area grid bands in ASP.NET Core Chart](appearance_images/aspnetcore-chart-customize-chart-area-grid-bands.png)


### Animation

You can enable animation by using the **EnableAnimation** property of the series. This animates the chart series on two occasions – when the chart is loaded for the first time or whenever you change the series type by using the **type** property.

{% highlight cshtml %}

<ej-chart id="container">
//..
<e-chart-series>
    <e-series enable-animation="true"> </e-series>
</e-chart-series>
//..
</ej-chart>

{% endhighlight %}

However, you can force the chart to animate series by calling the animate method as illustrated in the following code example,

{% highlight cshtml %}

<ej-chart id="container">
//..
<e-chart-series>
    <e-series enable-animation="true"> </e-series>
</e-chart-series>
//..
</ej-chart>

{% endhighlight %}

{% highlight js %}

//Dynamically animating chart
function animateChart(){

    //Calling the animate method for dynamic animation
    $("#chartContainer").ejChart("animate");      

}

{% endhighlight %}

### Control the speed of animation

To control the speed of animation, use the **AnimationDuration** property in the series. 

{% highlight cshtml %}

<ej-chart id="container">
//..
<e-chart-series>
    <e-series enable-animation="true" animation-duration="2000"> </e-series>
</e-chart-series>
//..
</ej-chart>

{% endhighlight %}