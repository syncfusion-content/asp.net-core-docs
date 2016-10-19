---
layout: post
title: Getting-Started
description: getting started
platform: aspnet-core
control: ListBox
documentation: ug
---

# Getting Started

This section explains briefly on how to create a ListBox control in your ASP.NET Core application.

## Create your first ListBox

1. Refer the [Getting Started](https://help.syncfusion.com/aspnet-core/getting-started) page of the Introduction part to know more about the basic system requirements and the steps to configure the Syncfusion components in an ASP.NET Core application.
2. Create your first Listbox by using the below mentioned code.

    {% highlight cshtml %}
    
        <ej-list-box id="list1"></ej-list-box>

    {% endhighlight %}

3. After executed the above code you can get the following output.

![](Getting-Started_Images/default.png)

## Data binding

We can also populate data in the listbox using “datasource” and “e-list-box-fields” properties. To achieve this we need to create and assign Datasource to the Listbox as given below.

{% highlight cshtml %}

        Select a bike:
        <ej-list-box id="bikeList" datasource="ViewBag.datasource">
            <e-list-box-fields id="empid" text="text" value="text" />
        </ej-list-box> 
            
{% endhighlight %}

Add this code in to your controller.

{% highlight c# %}

        List<Bikes> bike = new List<Bikes>();
        public ActionResult LocalData()
        {
            bike.Add(new Bikes { empid = "bk1", text = "Aache RTR" });
            bike.Add(new Bikes { empid = "bk2", text = "CBR 150-R" });
            bike.Add(new Bikes { empid = "bk3", text = "CBZ Xtreme" });
            bike.Add(new Bikes { empid = "bk4", text = "Discover" });
            bike.Add(new Bikes { empid = "bk5", text = "Dazzler" });
            bike.Add(new Bikes { empid = "bk6", text = "Flame" });
            bike.Add(new Bikes { empid = "bk7", text = "Fazzer" });
            bike.Add(new Bikes { empid = "bk8", text = "FZ-S" });
            bike.Add(new Bikes { empid = "bk9", text = "Pulsar" });
            bike.Add(new Bikes { empid = "bk10", text = "Shine" });
            bike.Add(new Bikes { empid = "bk11", text = "R15" });
            bike.Add(new Bikes { empid = "bk12", text = "Unicorn" });
            ViewBag.datasource = bike;
            return View();
        }
        public class Bikes(){
            public string empid { get; set; }
            public string text { get; set; }
        }

{% endhighlight %}

Run this code and you can get output like this

![](Getting-Started_Images/datasource.png)

## Selection

The ListBox control supports item selection in different way. In this example we are selected the items by its index value using selected-index property.

{% highlight cshtml %}
        
        Select a bike:
        <ej-list-box id="bikeList" datasource="ViewBag.datasource" selected-index="2">
            <e-list-box-fields id="empid" text="text" value="text" />
        </ej-list-box> 

 {% endhighlight %}
 
 Your output will be as given below.

![](Getting-Started_Images/selectedIndex.png)
 
 