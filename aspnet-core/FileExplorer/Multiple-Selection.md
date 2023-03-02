---
title: Multiple Selection | FileExplorer | ASP.NET Core | Syncfusion
description: Learn here about Multiple selection support in Syncfusion ASP.NET Core FileExplorer Control, its elements, and more.
platform: Asp.Net Core
control: FileExplorer
documentation: UG
keywords: FileExplorer,  Syncfusion, Asp.Net Core FileExplorer, UG document, Multiple selection
---
# Multiple Selection in ASP.NET Core FileExplorer



The [select](https://help.syncfusion.com/api/js/ejfileexplorer#events:select) event will be triggered when the items of FileExplorer control is selected.
Also [unselect](https://help.syncfusion.com/api/js/ejfileexplorer#events:unselect) event will be triggered when the items of FileExplorer control is unselected.

N>  For selecting files by mouse down and drag method, set the `AllowMultiSelection` property as true.

In the view page, add FileExplorer helper and specify the multi selection as true.
    
{% highlight CSHTML %}

<ej-file-explorer id="file" path="wwwroot/images/FileExplorer" ajax-action="@Url.Content("FileActionDefault")" allow-multi-selection="true">
    <e-file-ajax-settings>
        <e-download url="/FileExplorer/Download{0}"></e-download>
        <e-get-image url="/FileExplorer/GetImage{0}"></e-get-image>
        <e-upload url="/FileExplorer/Upload{0}"></e-upload>
    </e-file-ajax-settings>
</ej-file-explorer>

@*AllowMultiSelection property is true by default*@

{% endhighlight %}
    
## Checkbox option

You can enable or disable the checkbox using the “ShowCheckbox” API of FileExplorer.

In the view page, add FileExplorer helper and disable the checkbox as shown in the following.

{% highlight CSHTML %}

<ej-file-explorer id="file" path="wwwroot/images/FileExplorer" ajax-action="@Url.Content("FileActionDefault")" show-checkbox="false">
    <e-file-ajax-settings>
        <e-download url="/FileExplorer/Download{0}"></e-download>
        <e-get-image url="/FileExplorer/GetImage{0}"></e-get-image>
        <e-upload url="/FileExplorer/Upload{0}"></e-upload>
    </e-file-ajax-settings>
</ej-file-explorer>

{% endhighlight %}
