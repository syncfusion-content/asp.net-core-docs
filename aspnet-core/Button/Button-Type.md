---
layout: post
title: Button Type in ASP.NET Core Button Control | Syncfusion
description: Learn here all about button type support in Syncfusion Essential ASP.NET Core Button control, its elements, and more.
platform: aspnet-core
control: Button
documentation: ug
---

# Button Type in ASP.NET Core Button

Button is used as normal clickable button, submitting form data, resetting the form data to its initial value. According to the usage of button, you can render the button in three types. Using the Type property, you can easily render the button in following types.

_List of Button types_

<table>
<tr>
<td>
Button</td><td>
The button is a clickable button </td></tr>
<tr>
<td>
Submit</td><td>
The button is a submit button (submits form-data) </td></tr>
<tr>
<td>
Reset</td><td>
The button is a reset button (resets the form-data to its initial values)</td></tr>
</table>


The following steps explains you the details about rendering the Button with above mentioned button types.

1. In the CSHTML page, configure the Button widget as follows.

{% highlight CSHTML %}

/*ej-Tag Helper code to render Button*/

@*Add the code in CSHTML page to configure and initialize the control*@


@* Set the different types for button control as follows.*@

<div class="control">

        <ej-button id="button_button" text="button" show-rounded-corner="true" size="Mini" type="Button">

        <br />

        <br />

        <ej-button id="button_submit" text="submit" show-rounded-corner="true" size="Mini" type="Submit">

        <br />

        <br />

        <ej-button id="button_reset" text="reset" show-rounded-corner="true" size="Mini" type="Reset">
</div>

{% endhighlight  %}

{% highlight html %}

/*Razor code to render Button*/

<div class="control">

        @{ Html.EJ().Button("button_button").Text("button").ShowRoundedCorner(true).Size(ButtonSize.Mini).Type(ButtonType.Submit).Render(); }
     <br />
     <br />
        @{ Html.EJ().Button("button_submit").Text("submit").ShowRoundedCorner(true).Size(ButtonSize.Mini).Type(ButtonType.Submit).Render(); }
     <br />
     <br />
        @{ Html.EJ().Button("button_reset").Text("reset").ShowRoundedCorner(true).Size(ButtonSize.Mini).Type(ButtonType.Reset).Render(); }

</div>


{% endhighlight %}

N> To render the Button Control you can use either Razor or Tag helper code as given in the above code snippet.

Execute the above code to render the following output.

![Button Type in ASP.NET Core Button.](button-type_images/aspnet-core-button-type.png)

Different button types
{:.caption}
