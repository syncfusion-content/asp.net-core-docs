---
layout: post
title: Getting Started with ASP.NET Core RadialMenu control | Syncfusion
description: Learn here about getting started with Syncfusion Essential Studio ASP.NET Core RadialMenu control, its elements, and more.
platform: aspnet-core
control: RadialMenu 
documentation: ug
---

# Getting Started with ASP.NET Core RadialMenu

This section explains briefly about how to create a RadialMenu in ASP.NET Core application.

## Creating your first RadialMenu in ASP.NET Core application

1.	Refer the [Getting Started]( https://help.syncfusion.com/aspnet-core/gettingstarted/getting-started-1-1-0 ) page of the Introduction part to know more about the basic system requirements and the steps to configure the Syncfusion components in an ASP.NET Core application.

2. Add the following code to render RadialMenu in your ASP.NET Core application. You can set the images for each item by giving the image url with the **image-url** attribute in the RadialMenuItems and text with Text attribute. Refer the following code example.Initialize Radial Menu control and set its target content as follows.

{% highlight cshtml %}

    <ej-radial-menu id="defaultradialmenu" image-class="imageclass" auto-open="true">
            <e-radial-menu-items >
                   <e-radial-menu-item image-url="http://mvc.syncfusion.com/demos/web/Images/RadialMenu/font.png" text ="Bold" enabled="true">
                    </e-radial-menu-item>
                <e-radial-menu-item image-url="http://mvc.syncfusion.com/demos/web/Images/RadialMenu/f1.png" text="Italic" >
                   </e-radial-menu-item>
                <e-radial-menu-item image-url="http://mvc.syncfusion.com/demos/web/Images/RadialMenu/redo.png" text="Redo" >
                   </e-radial-menu-item>
                <e-radial-menu-item image-url="http://mvc.syncfusion.com/demos/web/Images/RadialMenu/undo.png" text="Undo">
                </e-radial-menu-item>
            </e-radial-menu-items>
    </ej-radial-menu>

{% endhighlight %}

Refer to the following code example to add target content to the Radial Menu.

{% highlight cshtml %}

    <div id="radialtarget1" class="content-container-fluid">
            <div class="row">
                <div class="cols-sample-area">
                    <textarea id="rteSample1" rows="10" cols="70" style="height: 440px">
                        <p>
                            Model???view???controller (MVC) is a software architecture pattern which separates the representation of information from the user's interaction with it.
                            The model consists of application data, business rules, logic, and functions. A view can be any output representation of data, such as a chart or a diagram.
                            Multiple views of the same data are possible, such as a bar chart for management and a tabular view for accountants.
                            The controller mediates input, converting it to commands for the model or view.The central ideas behind MVC are code reusability and in addition to dividing the application into three kinds of components, the MVC design defines the interactions between them.
                        </p>

                        <p>A controller can send commands to its associated view to change the view's presentation of the model (e.g., by scrolling through a document). It can also send commands to the model to update the model's state (e.g., editing a document).</p>

                        <p>A model notifies its associated views and controllers when there has been a change in its state. This notification allows the views to produce updated output, and the controllers to change the available set of commands. A passive implementation of MVC omits these notifications, because the application does not require them or the software platform does not support them.</p>

                        <p>A view requests from the model the information that it needs to generate an output representation to the user.</p>
                    </textarea>
                    <ej-rte id="rteSample1" show-context-menu="false" create="rteCreate" change="rteChange" select="radialShow" show-toolbar="false">
                    </ej-rte>
                </div>
            </div>
    </div>

{% endhighlight %}

To display the **Radial Menu** by performing desired action on the target content while selecting the text inside the target. Therefore, call the **radialShow** method in the select action of the content. Refer the following code example and add it to the script.

{% highlight javascript %}

    <script type="text/javascript">
        var rteObj, radialEle = $('#defaultradialmenu');
        $(function () {
            if (!(ej.browserInfo().name == "msie" && ej.browserInfo().version < 9)) {
                $("#radialtarget1").parent().css("position", "relative");
            }
            else {
                $("#contentDiv").html("Radial Menu is only supported from Internet Explorer Versioned 9 and above.").css({ "font-size": "20px", "color": "red" });
            }
            $(window).resize(function () {
                if (ej.isMobile() && ej.isPortrait())
                    $('#defaultradialmenu').css({ "left": 25 })
            });
        });
        function rteCreate(e) {
            rteObj = this;
        }
        function radialShow(e) {
            var target = $("#radialtarget1"), radialRadius = 150, radialDiameter = 2 * radialRadius,
            // To get Iframe positions
                iframeY = e.event.clientY, iframeX = e.event.clientX,
            // To set Radial Menu position within target
                x = iframeX > target.width() - radialRadius ? target.width() - radialDiameter : (iframeX > radialRadius ? iframeX - radialRadius : 0),
                y = iframeY > target.height() - radialRadius ? target.height() - radialDiameter : (iframeY > radialRadius ? iframeY - radialRadius : 0);
            radialEle.ejRadialMenu("setPosition", x, y);
            $('iframe').contents().find('body').blur();
        }
    </script>

{% endhighlight %}

Add the following in style section,

{% highlight css %}

    <style type="text/css" class="cssStyles">
        .e-radialmenu .imageclass {
            background-image: url("http://mvc.syncfusion.com/demos/web/Images/RadialMenu/settings.png");
        }
    </style>

{% endhighlight %}

Run the above code and select any text inside the target. The settings icon is displayed. Click that icon you will get the following output.



![Getting-Started_images](getting-started_images\img.png)