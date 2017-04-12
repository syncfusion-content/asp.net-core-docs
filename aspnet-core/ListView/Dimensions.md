---
layout: post
title: Dimensions | ListView | ASP.NET Core | Syncfusion
description: dimensions
platform: aspnet-core
control: ListView
documentation: ug
keywords: listview, dimensions
---

# Dimensions

To customize the ListView dimensions, width and height properties are used.

Refer to the following code examples.


{% highlight CSHTML %}

@Html.EJMobile().ListView("lb").Height(600).Width(300).Items(items =>

{

    items.Add().Text("ArtWork");

    items.Add().Text("Abstract");

    items.Add().Text("2 Acrylic Mediums");

    items.Add().Text("Creative Acrylic");

    items.Add().Text("Canvas Art");

    items.Add().Text("Black white");

    items.Add().Text("Children");

    items.Add().Text("Preschool Crafts");

    items.Add().Text("School-age Crafts");

})


{% endhighlight %}



### Screenshot:

![](Dimensions_images/Dimensions_img1.png)

Height
{:.caption}