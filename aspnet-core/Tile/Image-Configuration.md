---
layout: post
title: Image Configuration | Tile | ASP.NET MVC | Syncfusion
description: image configuration
platform: ejmvc
control: Tile
documentation: ug
---

# Image Configuration

ImagePosition property is used to adjust the position of Tile image at the Center on initialization. The possible values for the ImagePosition are as follows

1. Center
2. TopCenter
3. BottomCenter
4. RightCenter
5. LeftCenter
6. TopLeft
7. TopRight
8. BottomRight
9. BottomLeft 
10. Fill

ImageUrl property is used to set the background image for Tile, where the image is given in the path specified by ImageUrl property.

Refer to the following code examples.

{% highlight CSHTML %}

@Html.EJ().Tile("tile").Text("Weather").ImagePosition(TileImagePosition.Center).TileSize(TileSize.Wide).ImageUrl("http://js.syncfusion.com/UG/web/Content/tile/Weather_2.png ")

{% endhighlight %}



![](Image-Configuration_images/Image-Configuration_img1.png)



You can give images for each tile through CSS classes by using ImageClass property. You can define your desired styles in the specified class.

Refer to the following code examples.

{% highlight CSHTML %}

@Html.EJ().Tile("tile").Text("Pictures").ImagePosition(TileImagePosition.Center).TileSize(TileSize.Medium).ImageClass("pictures")

       <style>

        .pictures

         {

            background: url("http://js.syncfusion.com/UG/web/Content/tile/pictures.png ");

            background-size:30px 30px;

         }

    </style>

{% endhighlight %}

![](Image-Configuration_images/Image-Configuration_img2.png)



