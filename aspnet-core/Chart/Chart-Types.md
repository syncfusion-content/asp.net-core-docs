---
layout: post
title: Chart types |Chart  | ASP.NET CORE | Syncfusion
description: What are the different types of Charts available in Essential JavaScript Chart.
platform: aspnet-core
control: Chart
documentation: ug
---

# ChartTypes

## Line Chart

To render a Line Chart, set the series **Type** as **Line** in the chart series. To change the line segment color, you can use the **Fill** property of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Line" fill="#E94649"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img1.png)


### Change the line width

To change the width of the line segment, you can use the **Width** property in the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series width="3"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img2.png)


### Dashed lines

To render the line series with dotted lines, you can use the **DashArray** option of the series.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series dash-array="5,5"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img3.png)


### Changing the line cap

For customizing the start and end caps of the line segment, you can use the **LineCap** property.  

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series line-cap="Square"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img4.png)


### Changing the line join

You can use the **LineJoin** property to specify how two intersecting line segments should be joined.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series line-join="Round"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}


![](Chart-Types_images/Chart-Types_img5.png)


### MultiColor Line

You can change the color of the line segments by using the *Fill* property of the each *Points* in the series.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-points><e-point fill="red"></e-point></e-points>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img81.png)

 
## Step Line Chart

To render a Step Line Chart, set the series Type as **StepLine"** in the chart series. To change the StepLine segment color, you can use the Fill property of the series.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="StepLine" fill="#E94649">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img6.png)


### Changing the line width

To change the line width, you can use the **Width** property.  

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series width="3"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img7.png)


### Dashed lines

To render the step line series with dotted lines, you can use the DashArray option of the series.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series dash-array="5,5"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img8.png)


### Changing the line cap

For customizing the start and end caps of the line segment, you can use the LineCap property.  

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series line-cap="Square"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img9.png)


### Changing the line join

You can use the LineJoin property to specify how two intersecting line segments should be joined.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series line-join="Round"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img10.png)


## Area Chart

To render an Area chart, you can specify the series Type as **Area** in the chart series. To change the Area color, you can use the Fill property of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    <e-chart-series>
        <e-series type="Area" fill="#69D2E7">
        </e-series>
    </e-chart-series>
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img11.png)


## Range Area Chart

To render a Range Area Chart, set the Type as **RangeArea** in the chart series. To change the RangeArea color, you can use the Fill property of the series.

Since the RangeArea series requires two y values for a point, you have to add the **High** and **Low** value. High and Low value specifies the maximum and minimum range of the points.

* When you are using the Points option, specify the high and low values by using the High and Low option of the point.

* When you are using the DataSource option to assign the data, map the fields from the dataSource that contain High and Low values by using the Series.High and Series.Low options. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    <e-chart-series>
      <e-series type="RangeArea" fill="Indigo">
            <e-points><e-point x="1935" high="80" low="70"></e-point></e-points>
        </e-series>
    </e-chart-series>
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img12.png)

## Step Area Chart

To render a Step Area Chart, set the Type as **StepArea** in the chart series. To change the StepArea color, you can use the Fill property of the series.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="StepArea" fill="#69D2E7"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img13.png)

## Spline Area Chart

To render a Spline Area Chart, set the Type as **SplineArea** in the chart series. To change the SplineArea color, you can use the Fill property of the series.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="SplineArea" fill="#C4C24A"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img14.png)


## Stacked Area Chart

To render a Stacked Area Chart, set the Type as **StackingArea** in the chart series. To change the StackingArea color, you can use the Fill property of the series.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="StackingArea" fill="#69D2E7"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img15.png)


## 100% Stacked Area Chart  

To render a 100% Stacked Area Chart, set the Type as **StackingArea100** in the chart series. To change the StackingArea100 color, you can use the Fill property of the series.   

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="StackingArea100" fill="#C4C24A"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img16.png)


## Stacked Spline Area Chart

To render a Stacked Spline Area Chart, set the Type as **StackingSplineArea** in the chart series. 

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="StackingSplineArea"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}


![](Chart-Types_images/Chart-Types_img97.png)


## 100% Stacked Spline Area Chart  

To render a 100% Stacked Spline Area Chart, set the Type as **StackingSplineArea100** in the chart series. 

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="StackingSplineArea100"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}


![](Chart-Types_images/Chart-Types_img98.png)


## Column Chart

To render a Column Chart, set the Type as **Column** in the chart series. To change the color of the column series, you can use the Fill property.  

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Column" fill="#E94649"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img17.png)


### Change a point color

You can change the color of a column by using the Fill property of the point.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-points><e-point fill="skyblue"></e-point></e-points>
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img18.png)

### Column width customization

Width of any column type series can be customized by using the **ColumnWidth** property. Default value of *ColumnWidth* is 0.7. Value ranges from 0 to 1. Here 1 corresponds to 100% of available width and 0 corresponds to 0% of available width.

N> Width of a column also depends upon the *ColumnSpacing* property, because *ColumnSpacing* will reduce the space available for drawing a column. This is also applicable for StackingColumn, StackingColumn100, Bar, StackingBar, StackingBar100, RangeColumn, HiLo, HiLoOpenClose, Candle and Waterfall charts.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series column-width="0.8">
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img88.png)

### Column with rounded corners
Corners of the column chart can be customized by setting value to the **CornerRadius** property.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-common-series-options corner-radius="20"></e-common-series-options>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img90.png)   

### Spacing between column series

Spacing between column type series can be customized using the **ColumnSpacing** property. Default value of *ColumnSpacing* is 0. Value ranges from 0 to 1. Here 1 corresponds to 100% available space and 0 corresponds to 0% available space.

N> Space between columns will also affect the width of the column. For example, setting 20% spacing and 100% width will render columns with 80% of total width. This is also applicable for StackingColumn, StackingColumn100, Bar, StackingBar, StackingBar100, RangeColumn, HiLo, HiLoOpenClose, Candle and Waterfall charts.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series column-spacing="0.2">
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img89.png)


### Cylindrical Chart

To render a cylindrical chart, set the **ColumnFacet** property as "Cylinder" in the chart series along with the series type. 

The following chart types can be rendered as cylinder in both 2D and in 3D view.

* Column Chart, Bar Chart, Stacked Column Chart, Stacked Bar Chart, 100% Stacked Column Chart, 100% Stacked Bar Chart.


{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Line" column-facet="Cylinder">
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img91.png)

## RangeColumn Chart

To render a Range Column Chart, set the Type as **RangeColumn** in the chart series. To change the RangeColumn color, use the Fill property of the series.

Since, the RangeColumn series requires two y values for a point, add the High and Low value. High and Low value specifies the maximum and minimum range of the points.

* When you are using the Points option, specify the high and low values by using the High and Low option of the point.

* When you are using the DataSource option to assign the data, you have to map the fields from the dataSource that contains high and low values by using the Series.High and Series.Low) options.  

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="RangeColumn" fill="#E94649">
            <e-points><e-point high="6.1" low="0.7"></e-point></e-points>
        </e-series> 
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img19.png)


### Change a point color 

To change the color of a range column, you can use the Fill property of point. 

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-points><e-point fill="skyblue"></e-point></e-points>
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img20.png)


## Stacked Column Chart

To render a Stacked Column Chart, set the Type as **StackingColumn** in the chart series. To change the StackingColumn color, you can use the Fill property of the series.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="StackingColumn" fill="#E94649">
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img21.png)


### Cluster / Group stacked columns

You can use the **StackingGroup** property to group the stacked columns. Columns with same group name are stacked on top of each other.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        // For grouping stacked columns
        <e-series stacking-group="GroupOne">
        </e-series>
        // For grouping stacked columns
        <e-series stacking-group="GroupOne">
        </e-series>  
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img22.png)


### Change a point color

To change the color of a stacking column, you can use the Fill property of the point. 

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-points><e-point fill="skyblue"></e-point></e-points>
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img23.png)


## 100% Stacked Column Chart    

To render a 100% Stacked Column Chart, set the Type as **StackingColumn100** in the chart series. To change the StackingColumn100 color, you can use the Fill property of the series.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="StackingColumn100" fill="#E94649">
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img24.png)


### Cluster / Group 100% stacked columns

By using the **StackingGroup** property, you can group the 100% stacking columns. Columns with same group name are stacked on top of each other. 

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        // For grouping stacked columns
        <e-series stacking-group="GroupOne">
        </e-series>
        // For grouping stacked columns
        <e-series stacking-group="GroupOne">
        </e-series>  
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img25.png)


### Change a point color

To change the color of a 100% stacking column, you can use the Fill property of the point. 

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-points><e-point fill="skyblue"></e-point></e-points>
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img26.png)


## Bar Chart

To render a bar Chart, set the Type as **Bar** in the chart series. To change the bar color, you can use the Fill property of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Bar" fill="#E94649">
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img27.png)


### Change the color of a bar

By using the Fill property of the point, you can change the specific point of the series. 

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-points><e-point fill="skyblue"></e-point></e-points>
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img28.png)


## Stacked Bar Chart

To render a Stacked Bar Chart, set the Type as **StackingBar** in the chart series. To change the StackingBar color, you can use the Fill property of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="StackingBar" fill="#E94649">
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img29.png)


### Cluster / Group stacked bars

You can use the **StackingGroup** property to group the stacking bars with the same group name. 

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        // For grouping stacked columns
        <e-series stacking-group="GroupOne">
        </e-series>
        // For grouping stacked columns
        <e-series stacking-group="GroupOne">
        </e-series>  
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img30.png)


### Change a point color

You can change the color of a stacking bar by using the Fill property of the point.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-points><e-point fill="skyblue"></e-point></e-points>
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img31.png)


## 100% Stacked Bar Chart

To render a 100% Stacked Bar Chart, set the Type as **StackingBar100** in the chart series. To change the StackingBar100 color, you can use the Fill property of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series type="StackingBar100" fill="#E94649">
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>
 
{% endhighlight %}

![](Chart-Types_images/Chart-Types_img32.png)

By using the StackingGroup property, you can group the 100% stacking bars with the same group name. 

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        // For grouping stacked columns
        <e-series stacking-group="GroupOne">
        </e-series>
        // For grouping stacked columns
        <e-series stacking-group="GroupOne">
        </e-series>  
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img33.png)


### Change a point color

To change the color of a 100% stacking bar, you can use the Fill property of the point. 

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-points><e-point fill="skyblue"></e-point></e-points>
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img34.png)

## Spline Chart

To render a Spline Chart, set the Type as **Spline** in the chart series. To change the Spline segment color, you can use the Fill property of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series type="Spline" fill="#E94649">
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img35.png)


### Spline Types

Spline series supports four types of curves, namely natural, monotonic, cardinal and clamped. To change the spline type, you can use the **SplineType** property in the series. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series type="Spline" spline-type="Natural">
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}


### Change the cardinal spline tension

To change cardinal spline tension, you can use the [`cardinalSplineTension`](../api/ejchart#members:series-cardinalsplinetension) property in the series. The default value of cardinalSplineTension is **0.5**. Its value ranges from 0 to 1.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series type="Spline" spline-type="Cardinal" cardinal-spline-tension="0.7">
        </e-series>    
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}


### Change the spline width

To change the spline segment width, you can use the Width property of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series width="3"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img36.png)


### Dashed lines

To render the spline series with dotted lines, you can use the DashArray option of the series.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series dash-array="5,5"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img37.png)


## Pie Chart

You can create a pie chart by setting the series Type as **Pie** in the chart series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Pie"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img38.png)


### Change the pie size

You can use the **PieCoefficient** property to change the diameter of the Pie chart with respect to the plot area. It ranges from 0 to 1 and the default value is **0.8**.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series pie-coefficient="0.4f"></e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img39.png)


### Explode a pie segment

You can explode a pie segment on the chart load by using the **ExplodeIndex** of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series explode-index="1">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img40.png)


### Explode all the segments

To explode all the segments of the Pie chart, you can enable the **ExplodeAll** property.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series explode-all="true">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img41.png)


### Explode a pie segment on mouse over

To explode a pie segment on a mouse over, you can enable the **Explode** property of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series explode="true">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img42.png)


### Sector of Pie

EjChart allows you to render all the data points/segments in the semi-pie, quarter-pie or in any sector by using the **StartAngle** and **EndAngle** options.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series type="Pie" start-angle="-90" end-angle="90">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img43.png)


## Doughnut Chart

To create a Doughnut chart, you can specify the series Type as **Doughnut** in the chart series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series type="Doughnut">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img44.png)


### Change Doughnut inner radius

You can change the doughnut chart inner radius by using the **DoughnutCoefficient** with respect to the plot area. It ranges from 0 to 1 and the default value is **0.4**.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series doughnut-coefficient="0.6f">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img45.png)


### Change the doughnut size

You can use the **DoughnutSize** property to change the diameter of the Doughnut chart with respect to the plot area. It ranges from 0 to 1 and the default value is **0.8**.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series doughnut-size="0.4f">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img46.png)


### Explode a doughnut segment

To explode a specific doughnut segment, set the index to be exploded by using the **ExplodeIndex** option of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series explode-index="1">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img47.png)


### Explode all the segments

To explode all the segments, you can enable the **ExplodeAll** property of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series explode-all="true">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img48.png)


### Explode a doughnut segment on mouse over

To explode a doughnut segment on a mouse over, you can enable the **Explode** property of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series explode="true">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img49.png)


### Sector of Doughnut

EjChart allows you to render all the data points/segments in the semi-doughnut, quarter- doughnut or in any sector by using the **StartAngle** and **EndAngle** options.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
       <e-series type="Doughnut" start-angle="-90" end-angle="90">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img50.png)


## Multiple Pie Chart

EjChart provides support to render more than one series in pie and in doughnut chart. Radius of each series is calculated based on the radius of the previous series. And in addition legend is displayed according to the list of chart series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Pie">
        </e-series>
        <e-series type="Pie">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

**Multiple Pie** 

![](Chart-Types_images/Chart-Types_img82.png)


**Multiple Doughnut** 

![](Chart-Types_images/Chart-Types_img83.png)


### Start and End Angle Support

In the Multiple Pie chart, the start and end angle property is also supported.

**Sector of Multiple Pie**

![](Chart-Types_images/Chart-Types_img84.png)


**Sector of Multiple Doughnut**

![](Chart-Types_images/Chart-Types_img85.png)


## Pyramid Chart

To create a Pyramid chart, you can specify the series Type as **Pyramid** in the chart series.  

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Pyramid">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img51.png)


### Pyramid Mode

Pyramid mode has two types, *Linear* and *Surface* respectively. The default **PyramidMode** type is "Linear".

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series pyramid-mode="Surface">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img52.png)

### Gap between the segments

You can control the gap between the segments by using the **GapRatio** option of the series. Its ranges from 0 to 1.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series gap-ratio="0.1f">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img53.png)


### Explode a pyramid segment

You can explode a pyramid segment on the chart load by using the **ExplodeIndex** of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series explode-index="4">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img54.png)


## Funnel Chart

You can create a funnel chart by setting the series Type as **Funnel** in the chart series.  

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Funnel">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img55.png)

### Change the funnel width and height

Funnel segments height and width is calculated from the chart size, by default. You can change this height and width directly without changing the chart size by using the **FunnelHeight** and **FunnelWidth** property of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series funnel-height="22%" funnel-width="25%">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img56.png)


### Explode a funnel segment

You can explode a funnel segment on the chart load by using the **ExplodeIndex** of the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series explode-index="3">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img57.png)


## Bubble Chart

To create a Bubble chart, you can set the series Type as **Bubble** in the chart series. Bubble chart requires 3 fields (*X, Y and Size*) to plot a point. Here, **Size** is used to specify the size of each bubble segment. 

{% highlight csharp %}

// Create dataSource to bubble chart
    List<ChartData> data =new List<ChartData>();
    data.Add(new ChartData("Jan", 35, 1.34));
    data.Add(new ChartData("Feb", 28, 1.05));
    data.Add(new ChartData("Mar", 34, 0.45));
    data.Add(new ChartData("Apr", 32, 1.10));
    ViewBag.ChartData = data;


{% endhighlight %}

           
{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Bubble" x-name="Month" y-name="Sales" size="Profit" datasource="ViewBag.ChartData">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img58.png)

## Scatter

To create a Scatter chart, you can set the series Type as **Scatter** in the chart series. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Scatter">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img59.png)


### Customize the scatter chart

You can change the scatter size by using the **Size** property of the series marker. And you can change the scatter color by using the series Fill property. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series><e-marker><e-Size height="15" width="15"></e-Size></e-marker>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img60.png)


## HiLoOpenClose Chart 

To create a HiLoOpenClose chart, you can set the series Type as **HiloOpenClose** in the chart series. HiLoOpenClose chart requires 5 fields *(X, High, Low, Open and Close)* to plot a segment.  


{% highlight csharp %}

// Create dataSource to chart
    List<ChartData> data =new List<ChartData>();
    data.Add(new ChartData("Jan", 38, 10,38, 29));
    data.Add(new ChartData("Feb", 28, 15, 18, 27));
    data.Add(new ChartData("Mar", 54, 35, 38, 49));
    data.Add(new ChartData("Apr", 52, 21, 35, 29));
    ViewBag.ChartData = data;
{% endhighlight %}


{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="HiloOpenClose" x-name="Month" high="High" low="Low" open="Open" close="Close" datasource="ViewBag.ChartData">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img61.png)


### DrawMode

You can change the HiLoOpenClose chart **DrawMode** to *Open, Close* or *Both*. The default value of DrawMode is **Both**. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series draw-mode="Open">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img62.png)


### Bull and Bear Color	

HiLoOpenClose chart **BullFillColor** is used to specify a fill color for the segments that indicates an increase in stock price in the measured time interval and **BearFillColor** is used to specify a fill color for the segments that indicates a decrease in the stock price in the measured time interval. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series bear-fill-color="#FF6600" bull-fill-color="#336600">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img63.png)


## Candle

You can create a Candle chart by specifying the series Type as **Candle** in the chart series. Candle chart requires 5 fields *(X, High, Low, Open and Close)* to plot a segment.


{% highlight csharp %}

// Create dataSource to chart
    List<ChartData> data =new List<ChartData>();
    data.Add(new ChartData("Jan", 38, 10,38, 29));
    data.Add(new ChartData("Feb", 28, 15, 18, 27));
    data.Add(new ChartData("Mar", 54, 35, 38, 49));
    data.Add(new ChartData("Apr", 52, 21, 35, 29));
    ViewBag.ChartData = data;

{% endhighlight %}


{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Candle" x-axis-name="Month" high="High" low="Low" open="Open" close="Close" datasource="ViewBag.ChartData">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img64.png)


### Bull and Bear Color

Candle chart **BullFillColor** is used to specify a fill color for the segments that indicates an increase in the stock price in the measured time interval and **BearFillColor** is used to specify a fill color for the segments that indicates a decrease in the stock price in the measured time interval.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series bear-fill-color="#FF6600" bull-fill-color="#336600">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img65.png)


## HiLo

HiLo chart is created by setting the series Type as **Hilo** in the chart series. HiLo chart requires 3 fields *(X, High and Low)* to plot a segment.  

{% highlight csharp %}

// Create dataSource to chart
    List<ChartData> data =new List<ChartData>();
    data.Add(new ChartData("Jan", 38, 10));
    data.Add(new ChartData("Feb", 28, 15));
    data.Add(new ChartData("Mar", 54, 35));
    data.Add(new ChartData("Apr", 52, 21));
    ViewBag.ChartData = data; 

{% endhighlight %}

            
{% highlight cshtml %}
 
<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Hilo" x-axis-name="Month" high="High" low="Low">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img66.png)


## Polar

Polar chart is created by setting the series Type as **Polar** in the chart series. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Polar">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img67.png)


### DrawType

Polar **DrawType** property is used to change the series plotting type to *Line*, *Column* or *Area*. The default value of DrawType is **Line**.  

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series draw-type="Column">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img68.png)


### Stack columns in Polar chart

By using the **IsStacking** property, you can specify whether the column has to be stacked when the DrawType is column. Its default value is **false**.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series is-stacking="true">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img69.png)


## Radar Chart  

To create a Radar chart, you can specify the series Type as **Radar** in the chart series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Radar">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}


![](Chart-Types_images/Chart-Types_img70.png)

### DrawType

Radar **DrawType** property is used to change the series plotting type to *Line*, *Column* or *Area*. The default value of DrawType is **Line**.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series draw-type="Column">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}


![](Chart-Types_images/Chart-Types_img71.png)


### Stack columns in Radar chart

By using the **IsStacking** property, you can specify whether the column has to be stacked when the DrawType is set as Column. Its default value is set to *false*.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series is-stacking="true">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}


![](Chart-Types_images/Chart-Types_img72.png)


## Waterfall Chart 

For rendering a Waterfall chart, set series *Type* as **Waterfall** in the chart series. To change the waterfall series segment color use *Fill* option of series and use *PositiveFill* property to differentiate the positive segments.

N> The inline property of the **Series.PositiveFill** has the first priority and override the **Series.Fill**.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="Waterfall" fill="#C64E4A" positive-fill="#93C952">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}


![](Chart-Types_images/Chart-Types_img73.png)


**ShowIntermediateSum**

To display the summary of values since the last intermediate point of the waterfall series, set **ShowIntermediateSum** property as true in the specific point.


{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-points>
                <e-point show-intermediate-sum="true" x="Intermediate sum"></e-point>
            </e-points>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}


**ShowTotalSum**

The sum of all previous point in the waterfall series is displayed on enabling the **ShowTotalSum** property for a specific point.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-points>
                <e-point show-total-sum="true" x="Total sum"></e-point>
            </e-points>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

### ConnectorLine

To customize the connector line color, width, opacity and dashArray of the waterfall series, you can use **ConnectorLine** option of series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series width="3" opacity="1" dash-array="2,3">
            <e-connector-line color="#333000"></e-connector-line>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img74.png)


## ErrorBar Chart 

EjChart can generate Error bar for Cartesian type series *(Line, Column, Bar, Scatter, Area, Candle, HiLo, etc.)*. To render the Error bar for the series, set *Visibility* as *"visible"* to **ErrorBar** in the series.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-error-bar visibility="true"></e-error-bar>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img75.png)


### Changing Error Bar Type

You can change the error bar rendering type using **Type** *(like FixedValue, Percentage, StandardDeviation, StandardError and Custom)* option of errorBar. To change the error bar line length you can use **VerticalErrorValue** property.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-error-bar type="FixedValue" vertical-error-value="3"></e-error-bar>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img76.png)


#### Customizing error bar type              

To customize the error bar type, set error bar Type as **Custom** and then change the horizontal/vertical positive and negative value of error bar.

{% highlight cshtml %}

 <ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-error-bar type="Custom" vertical-positive-error-value="5" vertical-negative-error-value="5" horizontal-positive-error-value="1" horizontal-negative-error-value="1"></e-error-bar>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img77.png)


### Changing Error Bar Mode

Error bar mode is used to define whether the error bar line has to be drawn *Horizontally, Vertically* or in *Both* side.  To change the error bar mode use ErrorBar.Mode option.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-error-bar type="FixedValue" mode="Vertical"></e-error-bar>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img78.png)

### Changing Error Bar Direction

You can change the error bar direction to plus, minus or both side using ErrorBar.Directions option.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-error-bar type="FixedValue" mode="Vertical" direction="Minus"></e-error-bar>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img79.png)


### Customizing Error bar cap

To customize the errorBar cap visibility, length, width and fill color, you can use **Cap** option in the **Series.ErrorBar**.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series>
            <e-error-bar><e-cap visible="true" cap-length="20" cap-width="1" cap-fill="#000000"></e-cap></e-error-bar>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img80.png)


## Box and Whisker Chart 

To render a Box and Whisker Chart, set the series *type* as **boxAndWhisker** .Box and Whisker chart requires
2 fields (x and y) to plot a segment. The field y requires n number of data or it should  contain minimum of five values to plot a segment.

![](Chart-Types_images/Chart-Types_img90.png)

### BoxPlotMode
 
You can change the rendering mode of the  Box and Whisker series using the *BoxPlotMode* property .The default value of *BoxPlotMode* is **exclusive**.
The other boxPlotModes available are `inclusive` and `normal`. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series box-plot-mode="Inclusive">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

###  Customize the Outlier

Outlier symbol, width and height can be customized using outlierSettings through *outlierSettings* property. By default Outlier symbol is displayed as circle with a height and width of 6 pixels.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-size height="10" width="10"></e-size>
    <e-chart-series>
        <e-series>
            <e-outlier-settings shape="Triangle"></e-outlier-settings>
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img92.png)

## Pie Of Pie Chart
To render the pie of pie chart, set the series `Type` as **pieofpie**. Pie of pie chart is used for displaying the data of a pie slice as another pie chart. The values in the second pie is displayed based on the **splitMode**  property.

{% highlight cshtml %}
<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series type="pieofpie">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img93.png)


### Split Mode and Split Value 
The points to be displayed in the second pie is decided based on the `splitMode` property.**SplitMode** property takes the following values. 
* Position – Have to split the data points based on its position
* Value – Have to split the data points based on its Y value
* Percentage – Have to split the points based on the percentage value
* Indexes – The data points with the specified indexes are split separately 
 By default, the splitMode is set to  **Value**. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series split-mode="Position" split-value="3">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img94.png)

### Changing Pie Of Pie Size
The size of the second Pie can be customized by using the `PieOfPieCoefficient` property. The default value of pieOfPieCoefficient is **0.6**.Its value ranges from 0 to 1.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series pie-of-pie-coefficient="1">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

The following screenshot represents the pie of pie series with pieOfPieCoefficient as 1

![](Chart-Types_images/Chart-Types_img95.png)

#### Customizing the Gap

The distance between the two pies in the pie of pie chart can be controlled by using the `GapWidth` property. The default value is **50**.

 {% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series gap-width="150">
        </e-series>
    </e-chart-series>
    // ...
</ej-chart>

{% endhighlight %}

![](Chart-Types_images/Chart-Types_img96.png)
