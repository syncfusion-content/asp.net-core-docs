---
layout: post
title: Getting Started | GroupButton | ASP.NET Core | Syncfusion
description: getting started
platform: aspnet-core
control: GroupButton
documentation: ug
---

# Getting Started

## GroupButton initialization

This section explains you briefly on how to create a GroupButton in your application with ASP.NET Core. You can easily create the Button control by using Tag helper as follows.

1. You can create a .NetCore Project with the help of the given [ASP.NET Core-Getting Started](https://help.syncfusion.com/aspnet-core/getting-started) documentation.
2. Add the following code example to the corresponding view page to render GroupButton.


~~~ html

<ej-group-button id="GroupButton" width="100%" group-button-mode="@GroupButtonMode.RadioButton" show-rounded-corner="true">
    <e-group-button-items>
        <e-group-button-item text="Day"></e-group-button-item>
        <e-group-button-item text="Week"></e-group-button-item>
        <e-group-button-item text="Month"></e-group-button-item>
    </e-group-button-items>
</ej-group-button>

~~~

{% highlight js %}

         <script>

            $("#groupButton").ejGroupButton();// initialize the group button control

         </script>

{% endhighlight %}

Also we can use the dataSource, to create the GroupButton which is explained under the dataSource section in this documentation.

