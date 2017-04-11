---
layout: post
title: How To | Signature | ASP.NET Core | Syncfusion
description: How To
platform: aspnet-core
control: Signature
documentation: ug
keywords: save, signature
---

# How To

## Save signature image with user defined format

By default, the downloaded image form the signature canvas will be in **png** format. We can define our own format to download the image with **save-image-format** property. And we can also save the image along with the background by using the **save-with-background** property.

In the View page, define the following code.

{% highlight CSHTML %}


<ej-signature id="mysign" height="400px" width="500" stroke-width="3" background-image="../images/water.png" is-responsive="true" save-with-background="true" />

<a id="download">
    <input id="signsave" class="e-btn" type="button" value="Save" />
</a>

{% endhighlight %}

Add the following script to define the download format for the canvas.

{% highlight js %}

<script type="text/javascript">
        $(function () {
            
            $("#signsave").ejButton({
                size: "normal",
                showRoundedCorner: true,
            });
            var client = document.getElementById('download');
            if (client.addEventListener)
                client.addEventListener('click', downloadClient, false);
            else
                client.attachEvent('onclick', downloadClient, false);

            function downloadClient(e) {
                var sign = $("signature").ejSignature("instance");
                sign.option("saveImageFormat", "jpg")                   // set the save image format dynamically
                this.download = "Signature." + sign.model.saveImageFormat + "";
                var div = $("signature");
                var canvas = div["children"]()[0];
                this.href = canvas.toDataURL("image/" + sign.model.saveImageFormat + "", 1.0);
            }
        });

    </script>

{% endhighlight %}


The following screenshot illustrates the Signature with saving (downloading) the drawn image along with its background.

![](how_to_images\savesignatureimagewithuserdefinedformat_img1.png)

## Make signature as responsive

When the signature control is resized or even the window is resized the strokes drawn in the signature will be disappeared. To make the strokes visible even after resizing the window, we must set the **is-responsive** property as true.

In the View page, define the following code to render signature with responsive.

{% highlight CSHTML %}

<ej-signature id="mysign"  is-responsive="true"/>

{% endhighlight %}


The following screenshot illustrates the Signature with responsiveness.

Before Responsiveness:

![](how_to_images\makesignatureasresponsive_img1.png)

After giving the Responsiveness:

![](how_to_images\makesignatureasresponsive_img2.png)

