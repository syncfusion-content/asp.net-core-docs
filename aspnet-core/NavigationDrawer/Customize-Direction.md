---
layout: post
title: Customize Direction | NavigationDrawer | ASP.NET MVC | Syncfusion
description: customize direction
platform: ejmvc
control: NavigationDrawer
documentation: ug
---

# Customize Direction

By using this property, you can set the drawer to be open from right to left direction or left to right direction. The possible direction values are Right, Left and the default value is Left. Refer to the following code example.



{% highlight CSHTML %}

@Html.EJ().NavigationDrawer("navpane").Width(300).Position(NavigationDrawerPosition.Fixed).Direction(NavigationDrawerDirection.Right).ContentTemplate(@<div>

@Html.EJ().ListView("list").Width(300).Items(items =>

{

	 items.Add().Text("Home");

	 items.Add().Text("Profile");

	 items.Add().Text("Photos");

	 items.Add().Text("Location");

})

</div>)


{% endhighlight %}



The following screenshot displays the output by swiping from right to left at the right side end of the screen.

![](Customize-Direction_images/Customize-Direction_img1.png)



