---
layout: post
title: Easy Customization | GroupButton | ASP.NET Core | Syncfusion
description: easy customization
platform: aspnet-core
control: GroupButton 
documentation: ug
---

# DataSource

GroupButton can populate the groupbutton items based on datasource and by specifying the associated fields. You can bind data from both remote and local sources.
Refer the below table to know about the available fields

Field is a property that includes the object type. Fields are used to bind the data source and it includes following field members to make binding easier.

_List of Field members_

<table>
<tr>
<th>
Name</th><th>
Description</th></tr>
<tr>
<td>
DataSource</td><td>
Datasource receives Essential DataManager object and JSON object. </td></tr>
<tr>
<td>
Id</td><td>
Specifies the id to Groupbutton item</td></tr>
<td>
Text</td><td>
Specifies the text of Groupbutton item</td></tr>
<tr>
<td>
SpriteCssClass</td><td>
Specifies the sprite CSS class to “LI” item list</td></tr>
<tr>
<td>
Url</td><td>
Specifies the href attribute of "A" tag in item list</td></tr>
<tr>
<td>
PrefixIcon</td><td>
Specifies the PrefixIcon class for Groupbutton item list</td></tr>
<tr>
<td>
SuffixIcon</td><td>
Specifies the SuffixIcon class for Groupbutton item list</td></tr>
<tr>
<td>
ImagePosition</td><td>
Specifies the position of Image in Groupbutton item list</td></tr>
<tr>
<td>
LinkAttribute</td><td>
Specifies the link attribute to “A” tag in item list</td></tr>
<tr>
<td>
HtmlAttribute</td><td>
Specifies the HTML attribute to “li” tag in item list</td></tr>
<tr>
<td>
ContentTemplate</td><td>
Specifies the template content for customizing the Groupbutton items</td></tr>
<tr>
<td>
Selected</td><td>
Specifies initial selection state of GroupButton item</td></tr>
<tr>
<td>
ContentType</td><td>
Specifies Content type of Groupbutton Item. The possible values are <br/>
1. TextOnly <br/>
2. ImageOnly <br/>
3. ImageBoth <br/>
4. TextAndImage <br/>
5. ImageTextImage <br/>
</td></tr>
</table>

## Local data

To populate the Groupbutton items with the local data, map the field names mentioned in the above table with the property names.

1. Add the following code in your view page to render GroupButton with local data


{% highlight CSHTML %}

// Add the following code in your CSHTML page.

    <ej-group-button id="GroupButton" datasource="ViewBag.Model" width="500px">
        <e-group-button-fields text="text" />
    </ej-group-button>
	   
{% endhighlight %}

{% highlight c# %}

using System;
using System.Collections.Generic;
using System.Web.Mvc;
using Groupbutton_mvc.Models;
namespace Groupbutton_mvc
{
    public class ButtonController: Controller
    {
        public class Groupbutton
        {
            public string text { get; set; }
        }

        public List<Groupbutton> model = new List<Groupbutton>();

        public ActionResult ButtonFeatures()
        {
            model.Add(new Groupbutton { text = "Item1" });
            model.Add(new Groupbutton { text = "Item2" });
            model.Add(new Groupbutton { text = "Item3" });
            ViewBag.Model = model;
            return View();
         } 
    }
}

{% endhighlight %}

The following screenshot displays the output of the above code.

![](Datasource_images/object.png)

Local data of GroupButton
{:.caption}

