---
layout: post
title: Miscellaneous | RadioButton | ASP.NET Core | Syncfusion
description: miscellaneous
platform: aspnet-core
control: RadioButton
documentation: ug
---

# Miscellaneous

## Radio Button ID

Radio Button id is not shown in the user interface. Here Id denotes the Id attribute of the root element of Radio Button control. This Id value is unique. You can give Id through element and through the Id property. When you use two ids for a single radio button at initialization, the element Id is considered.

Set Id for Radio Button control as follows.

{% highlight CSHTML %}

@*set new id value as follows*@

<ej-radio-button id="RadBtn_Male" name="Gender" />

<br />

<ej-radio-button id="RadBtn_female" name="Gender" />

{% endhighlight %}


## Radio Button Prefix id

Id prefix value is appended to the element id value. It is used to mention the prefix for the wrapper’s id attribute. When you assign a value for IdPrefix property, the older prefix id gets replaced by the new prefix id. 

Setting a new prefix id for Radio Button control is as follows.



{% highlight CSHTML %}

@*set new idPrefix  value as follows*@

<ej-radio-button id="RadBtn_Male" name="Gender" id-prefix="sync_"/>

<br />

<ej-radio-button id="Radio_Female" name="Gender" id-prefix="sync_"/>

{% endhighlight %}



## Radio Button Name

The Name setting tells you where a Radio Button belongs. When you select one button, all other buttons in the same group are unselected. You can have only one group of Radio Buttons on each page.

The Name attribute is also used to identify form data after it has been submitted to the server, or for reference of form data using JavaScript on the client’s side. Only form elements with a Name attribute have their values passed, when submitting a form.

## Radio Button Value

The Value setting defines what can be submitted when checked.

For Radio Buttons, the contents of the value property do not appear in the user interface. The Value property only has meaning when submitting a form. If a radio button is in the checked state when the form is submitted, the name of the Radio Button is sent along with the value of the value property, if the radio button is not checked, no information is sent.

To identify, on the server side, which one was checked, give different values for radio buttons in the same group, 

Set name and value for each radio button control as follows.


{% highlight CSHTML %}

@*set name and value for each radio button as follows*@

<ej-radio-button id="RadBtn_Female" name="Gender" value="male"/>

<br />

<ej-radio-button id="RadBtn_Male" name="Gender" value="female"/>

{% endhighlight %}