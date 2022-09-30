---

layout: post
title: Load on demand | DropDownList | ASP.NET Core | Syncfusion
description: Learn here all about Load on Demand support in Syncfusion Essential ASP.NET Core DropDownlist control, its elements, and more.
platform: aspnet-core
control: DropDownList, loadOnDemand
documentation: ug

---

# Load On Demand in ASP.NET Core DropDownlist

Load on demand feature allows the DropDownList items load on request from the service/database, during only on click the DropDown icon or DropDownList. This functionality helps to improve performance on control initial rendering time. Because data items load on request. 

The loadOnDemand property is used to enable or disable the load on demand functionality of the DropDownList.

{% highlight html %}

     <ej-drop-down-list id="selectCar" target-id="carsList" width="100%" watermark-text="Select a Car" load-on-demand=”true”></ej-drop-down-list>
            <div id="carsList">
                <ul>
                    <li>Audi A4</li>
                    <li>Audi A5</li>
                    <li>Audi A6</li>
                    <li>Audi A7</li>
                    <li>Audi A8</li>
                </ul>
            </div>

     
{% endhighlight %}


![ASP.NET Core DropDownlist load on demand](LoadOnDemand_images/loadondemand.png)