---
layout: post
title: Getting-Started
description: getting started
platform: aspnet-core
control: ComboBox
documentation: ug
keywords: allowCustom, ComboBox, dataSource, popupHeight, popupWidth
---

# Getting Started

This section explains how to create a simple **ComboBox** component and configure its available functionalities in TypeScript, using [`ASP.NET Core`](https://help.syncfusion.com/aspnet-core/getting-started) documentation.

{% highlight CSHTML %}
  
   /*ej-Tag Helper code to render ComboBox*/

            <ej-ComboBox id="selectCar"></ej-ComboBox>

       
  {% endhighlight  %}

  {% highlight Razor %}
  
       /*Razor code to render DropDownList*/

          @{Html.EJ().ComboBox("id").Render();}

  {% endhighlight  %}

N> To render the ComboBox Control, you can use either Razor or Tag helper code as given in the above code snippet.

## Initialize the ComboBox

The ComboBox can be initialized as:

{% highlight html %}

<div class="frame">
        <div class="control"> 
        <ej-combo-box id="select" datasource="(IEnumerable<Flowers>)ViewBag.datasource" placeholder="Select">
            <e-combo-box-fields text="text"/>
        </ej-combo-box>
        </div>
    </div>

{% endhighlight %}

{% highlight c# %}

  public class Flowers
    { 
        public string text { get; set; }
        public static List<Flowers> GetFlowers()
        {
            List<Flowers> flower = new List<Flowers>();
            flower.Add(new Flowers { text = "Anemone Galilee" });
            flower.Add(new Flowers { text = "Allium drumstick" });
            flower.Add(new Flowers { text = "Artichoke thistle" });
            flower.Add(new Flowers { text = "Boronia" });
            flower.Add(new Flowers { text = "Bouvardia" });
            flower.Add(new Flowers { text = "Blue lace flower" });
            flower.Add(new Flowers { text = "Bird of paradise" });
            flower.Add(new Flowers { text = "Cone flower" });
            flower.Add(new Flowers { text = "Cosmos" });
            ...
            return flower;
        }
    }
       
  {% endhighlight  %}

![](Combobox_getting_started_images/Getting-Started.png)

## Binding data source

After initializing, populate the ComboBox with data using the **dataSource** property. Here, an array of string values is passed to the ComboBox component.

{% highlight CSHTML %}

 @{string[] datasource = new string[] { "Badminton", "Cricket", "Football", "Golf", "Tennis" };
    }
    <div class="frame">
        <div class="control"> 
        <ej-combo-box id="selectCar" datasource="datasource" placeholder="Select">
            <e-combo-box-fields text="text"/>
        </ej-combo-box>
        </div>
    </div>

{% endhighlight %}


![](Combobox_getting_started_images/Getting-Started1.png)


## Custom values

The ComboBox allows the user to give input as custom value which is not required to present in predefined set of values. By default, this support is enabled by the **allowCustom** property. In this case, both text field and value field are considered as same. The custom value will be sent to post back handler when a form is about to be submitted.

{% highlight CSHTML %}

<div class="frame">
        <div class="control"> 
        <ej-combo-box id="select" datasource="(IEnumerable<Flowers>)ViewBag.datasource" allow-custom="true" placeholder="Select">
            <e-combo-box-fields text="text" value="id"/>
        </ej-combo-box>
        </div>
    </div>

{% endhighlight %}

{% highlight c# %}

  public class Flowers
    { 
        public string text { get; set; }
        public static List<Flowers> GetFlowers()
        {
            List<Flowers> flower = new List<Flowers>();
            flower.Add(new Flowers { text = "Anemone Galilee" });
            flower.Add(new Flowers { text = "Allium drumstick" });
            flower.Add(new Flowers { text = "Artichoke thistle" });
            flower.Add(new Flowers { text = "Boronia" });
            return flower;
        }
    }
  {% endhighlight  %}

![](Combobox_getting_started_images/Combobox_data_binding_img1.png)

## Configure the popup list

By default, the width of the popup list automatically adjusts according to the ComboBox input element's width, and the height of the popup list has '300px'.

The height and width of the popup list can also be customized using the **popupHeight** &nbsp;and **popupWidth** properties respectively.

In the following sample, popup list's width and height are configured.

{% highlight CSHTML %}

<div class="frame">
        <div class="control"> 
        <ej-combo-box id="select" datasource="(IEnumerable<Flowers>)ViewBag.datasource" popup-height="100px" popup-width="200px" placeholder="Select">
            <e-combo-box-fields text="text" value="id"/>
        </ej-combo-box>
        </div>
    </div>

{% endhighlight %}

{% highlight c# %}

  
       public class Flowers
    { 
        public string text { get; set; }
        public static List<Flowers> GetFlowers()
        {
            List<Flowers> flower = new List<Flowers>();
            flower.Add(new Flowers { text = "Anemone Galilee" });
            flower.Add(new Flowers { text = "Allium drumstick" });
            flower.Add(new Flowers { text = "Artichoke thistle" });
            flower.Add(new Flowers { text = "Boronia" });
            flower.Add(new Flowers { text = "Bouvardia" });
            flower.Add(new Flowers { text = "Blue lace flower" });
            flower.Add(new Flowers { text = "Bird of paradise" });
            flower.Add(new Flowers { text = "Cone flower" });
            flower.Add(new Flowers { text = "Cosmos" });
            ...
            return flower;
        }
    }
  {% endhighlight  %}

![](Combobox_getting_started_images/popup.png)

