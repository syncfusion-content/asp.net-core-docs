---
layout: post
title: Customize Position | NavigationDrawer | ASP.NET MVC | Syncfusion
description: customize position
platform: ejmvc
control: NavigationDrawer
documentation: ug
---

# Customize Position

Position property is used to specify the position whether it is in fixed or relative to the page. When you set a normal value to position property, it appears within the container. Otherwise, it appears in the whole body .The possible position values are fixed and normal. The Default value is normal.



{% highlight CSHTML %}

@Html.EJ().NavigationDrawer("navpane").Width(300).Position(NavigationDrawerPosition.Fixed).ContentTemplate(@<div>

        @Html.EJ().ListView("list").Width(300).Items(items =>

         {

             items.Add().Text("Home");

             items.Add().Text("Profile");

             items.Add().Text("Photos");

             items.Add().Text("Location");

         })

    </div>) 



{% endhighlight %}



The following screenshot illustrates the output by swiping from left to right at the left end of the screen.

![](Customize-Position_images/Customize-Position_img1.png)



