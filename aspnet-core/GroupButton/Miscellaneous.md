---
layout: post
title: Miscellaneous | GroupButton | ASP.NET Core | Syncfusion
description: miscellaneous
platform: aspnet-core
control: GroupButton
documentation: ug
---

# Miscellaneous

## Text

You can display your own text for Button. By using the text property, you can easily set text content for button. This text property overwrites the text that is provided on input button element.

In the view page, add the following button elements to configure Button with text



{% highlight html %}

<%--Set the text for button control as follows--%>

 @Html.EJ().GroupButton("GroupButton").Items(item =>
                   {
                       item.Add().Text("Save");
                       item.Add().Text("Open");
                       item.Add().Text("Delete");
                   })

{% endhighlight %}

![](Miscellaneous_images/text.png)


## Show Rounded Corner

Customizes the corners of Groupbutton control to be rendered with Rounded corners.

In the view page, add the following button elements to get rounded Button

{% highlight html %}

<%--Enable the rounded corner for button control as follows--%>

    <ej-group-button id="GroupButton" show-rounded-corner="true"  width="500px">
        <e-group-button-items>
            <e-group-button-item text="Save"></e-group-button-item>
            <e-group-button-item text="Open"></e-group-button-item>
            <e-group-button-item text="Delete"></e-group-button-item>
        </e-group-button-items>
    </ej-group-button>


{% endhighlight %}

![](Miscellaneous_images/roundedcorner.png)


