---
layout: post
title: Button Type | GroupButton | ASP.NET Core | Syncfusion
description: Groupbutton
platform: aspnet-core
control: GroupButton
documentation: ug
---

# Behavior settings

Groupbutton provides options through which you can customize the default behavior of Groupbutton control.

## Groupbutton Mode

The default behavior of Groupbutton is like Radiobutton, i.e., only one item can be selected at a time.

{% highlight html %}

    <ej-group-button id="GroupButton" group-button-mode="@GroupButtonMode.RadioButton" width="500px">
        <e-group-button-items>
            <e-group-button-item text="Save"></e-group-button-item>
            <e-group-button-item text="Open"></e-group-button-item>
            <e-group-button-item text="Delete"></e-group-button-item>
        </e-group-button-items>
    </ej-group-button>

{% endhighlight %}

![](Behavior-Settings_images/Radiobutton.png)


To enable selection of one or more Groupbutton items at a time, you can set the Groupbutton mode to Checkbox. With this, you can toggle the each button’s state to perform actions, since all the button will behave like individual buttons.

{% highlight html %}

    <ej-group-button id="GroupButton" group-button-mode="@GroupButtonMode.CheckBox" width="500px">
        <e-group-button-items>
            <e-group-button-item text="Save"></e-group-button-item>
            <e-group-button-item text="Open"></e-group-button-item>
            <e-group-button-item text="Delete"></e-group-button-item>
        </e-group-button-items>
    </ej-group-button>
    
{% endhighlight %}

![](Behavior-Settings_images/Checkbox.png)

