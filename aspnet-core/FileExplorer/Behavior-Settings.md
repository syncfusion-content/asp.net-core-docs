---
title: Behavior Settings| FileExplorer | ASP.NET Core | Syncfusion
description: Customize the behavior of FileExplorer
platform: Asp.Net Core
control: FileExplorer
documentation: UG
keywords: FileExplorer, Syncfusion, Asp.Core FileExplorer, UG document, Behavior settings
---

# Behavior Settings

Here are the some properties to customize the behavior of FileExplorer.

## File type restriction

FileExplorer control showcase all the files from the filesystem, here you can customize the file types that what you want to show by using “[FileTypes](http://help.syncfusion.com/js/api/ejfileexplorer#members:filetypes)” property. It filter the files based on the file extensions.
By default it having the value " \*.\* ", so it allows all the file types. In case of image browser you can allow the image files only by setting “*.png, *.gif, *.jpg, *.jpeg”, so it doesn’t allow the other type of files.
In the view page, add FileExplorer helper and specify the file type restriction as shown below.

{% highlight CSHTML %}

<ej-file-explorer id="default" path="wwwroot/images/FileExplorer" ajax-action="@Url.Content("FileActionDefault")" width="100%" is-responsive="true" file-types="*Png,*docx" >
<e-file-ajax-settings>
    <e-download url="/FileExplorer/Download{0}"></e-download>
    <e-get-image url="/FileExplorer/GetImage{0}"></e-get-image>
    <e-upload url="/FileExplorer/Upload{0}"></e-upload>
</e-file-ajax-settings>
</ej-file-explorer>

{% endhighlight %} 

## Customize the AJAX request settings

As you already know FileExplorer is a client – server based control and each action performed in th e client sends an AJAX request to the server to perform the server side operations. While the AJAX request, the AJAX configurations can be customized through “[AjaxSettings](http://help.syncfusion.com/js/api/ejfileexplorer#members:ajaxsettings)” property.

You can see the following requests passed during the **client – server** actions:

* Read

* Create folder

* Remove

* Rename

* Paste

* Get details

* Upload

* Download

* Get Image

* Search

The actions “Read, CreateFolder, Remove, Rename, Paste, GetDetails, Search” are supported all the jQuery AJAX configurations. The remaining actions “Upload, Download, GetImage” are accepted the URL only.
If you want to customize read action alone, the AJAX “**Url**” and “**DataType**” are changed for the “Read” action.

In the view page, add FileExplorer and specify the AJAX settings for Read request as shown below.

{% highlight CSHTML %}

<ej-file-explorer id="default" path="wwwroot/images/FileExplorer" ajax-action="@Url.Content("FileActionDefault")" width="100%" is-responsive="true" >
<e-file-ajax-settings>
    <e-read url="/FileExplorer/Read{0}" datatype="jsonp"></e-read>
    <e-download url="/FileExplorer/Download{0}"></e-download>
    <e-get-image url="/FileExplorer/GetImage{0}"></e-get-image>
    <e-upload url="/FileExplorer/Upload{0}"></e-upload>
</e-file-ajax-settings>
</ej-file-explorer>

{% endhighlight %} 