---
layout: post
title: Appearance and Styling | RangeNavigator | ASP.NET Core | Syncfusion
description: appearance and styling
platform: aspnet-core
control: RangeNavigator
documentation: ug
---

# Appearance and Styling

RangeNavigator is enriched with lots of customization options for labels, gridlines and slider to develop high quality graphic rich control.

## Label Placement:

Labels in RangeNavigator are placed inside or outside of the control. You can customize both the higher and lower level labels using LabelPlacement property in label setting of RangeNavigator. By default LabelPlacement is “outside” for the both higher and lower level labels.

The following screen shot illustrates both the lower and higher level labels that are placed outside the control with LabelPlacement specified as outside. 

{% highlight CSHTML %}

<div>
	<ej-range-navigator id="range" load="loadingdata">
		<e-chart-series>
			<e-series name="Product A" type="Line" fill="#69D2E7">
			</e-series>
		</e-chart-series>
		<e-selected-range-settings start="2010/5/1" end="2011/10/1"></e-selected-range-settings>
		<e-label-settings>
			<e-higher-level label-placement="Inside"></e-higher-level>
			<e-lower-level label-placement="Inside"></e-lower-level>
		</e-label-settings>
		</ej-range-navigator>
</div>

{% endhighlight  %}

The following screenshot illustrates a RangeNavigator with labels inside the control after specifying the LabelPlacement as inside.

![](Appearance-and-Styling_images/Appearance-and-Styling_img2.png)

## Customize RangeNavigator

RangeNavigator is customized using NavigatorStyleSettings properties. You can customize the selected and unselected region color using SelectedRegionColor, UnselectedRegionColor in NavigatorStyleSettings and the thumb of the slider using ThumbColor, ThumbRadius and ThumbStroke in NavigatorStyleSettings.  MajorGridLineStyle and MinorGridLineStyle are used to customize the grid line color and visibility. 

{% highlight CSHTML %}
 
<div>
    <ej-range-navigator id="range">
        <e-navigator-style-settings background="transparent" unselected-region-color="white" selected-region-color="#5EABDE" thumb-radius="10" thumb-color="white">
            <e-border color="Black" width="3"></e-border>
            <e-major-grid-line-style visible="true" color="transparent"></e-major-grid-line-style>
            <e-minor-grid-line-style visible="true" color="transparent"></e-minor-grid-line-style>
        </e-navigator-style-settings>
        <e-label-settings>
            <e-higher-level label-placement="Inside" interval-type="Years"></e-higher-level>
        </e-label-settings>
    </ej-range-navigator>
</div>

{% endhighlight  %}

![](Appearance-and-Styling_images/Appearance-and-Styling_img3.png)

## Themes

RangeNavigator theme is a set of pre-defined options that are applied to the control before each RangeNavigator is instantiated. Following predefined themes are available in RangeNavigator.

1. flatlight                  
2. flatdark                  
3. gradientlight           
4. gradientdark           
5. azure                      
6. azuredark               
7. lime 
8. limedark
9. saffron
10. saffrondark
11. gradientazure
12. gradientazuredark
13. gradientlime
14. gradientlimedark
15. gradientsaffron

### gradientsaffrondark

{% highlight CSHTML %}

<div>
	<ej-range-navigator id="range" load="loadingdata" theme="azuredark">
		<e-chart-series>
			<e-series name="Product A" type="Line">
			</e-series>
		</e-chart-series>
		<e-selected-range-settings start="2010/5/1" end="2011/10/1"></e-selected-range-settings>
		</ej-range-navigator>
</div>

{% endhighlight  %}

![](Appearance-and-Styling_images/Appearance-and-Styling_img4.png)