---
layout: post
title: XHTML Validation in RichTextEditor widget for Syncfusion Essential ASP.NET Core
description: XHTML Validation to format the RichTextEditor widget's content
platform: aspnet-core
control: RTE
documentation: ug
keywords: RichTextEditor, XHTML Validation

---
# XHTML Validation

The editor provides option to validate its content through the EnableXHTML property. When you set or modify the content into the editor, it continuously checks whether the HTML source of the content that you are creating is valid. The editor examines the HTML markup and then removes the elements or attributes that are not valid. 

{% highlight CSHTML %}

<ej-rte id="Rte" width="820px" enable-xhtml="true">
    <e-content-template>
        <div>
            The Rich Text Editor (RTE) control is an easy to render in client side.
            Customer easy to edit the contents and get the HTML content for the displayed content.
            A rich text editor control provides users with a toolbar that helps them to apply rich text formats to the text entered in the text area.
        </div>
    </e-content-template>
</ej-rte>

{% endhighlight %}

The editor checks the following settings on validation:

* **Attributes** 
  * Must be specified in lowercase 
  * Proper use of quotation marks around the attributes
  * Must be valid attributes for corresponding HTML element
  * All the required attributes must be included in the HTML element
  * Accepts the allowed values alone such as true or false.
* **HTML** **Elements** 
  * Must be in lowercase 
  * All opening tags must be closed
  * Allows only the valid HTML elements