---
layout: post
title: How To? | Dialog  | ASP.NET Core| Syncfusion
description: How to achieve specific requirements in Dialog widget.
platform: aspnet-core
control: Dialog
documentation: ug
keywords : dialog
---

# How To?

## Create Multiple Dialogs

Essential Studio for ASP.NET Core library supports multiple Dialog widgets in the same web page with different contents and different functionalities.

Initialize the Dialog widgets by configuring as below.

{% highlight cshtml %}

        <ej-dialog id="firstdialog" title="Dialog" width="250">
            <e-dialog-position x-value="20" y-value="20" />
            <e-content-template>
                <div>
                    <p>This is a simple dialog</p>
                </div>
            </e-content-template>
        </ej-dialog>
        <ej-dialog id="seconddialog" title="Window" width="250">
            <e-dialog-position x-value="300" y-value="20" />
            <e-content-template>
                <div>
                    <p>This is a different dialog</p>
                </div>
            </e-content-template>
        </ej-dialog>
        <ej-dialog id="thirddialog" title="Popup" width="250">
            <e-dialog-position x-value="150" y-value="150" />
            <e-content-template>
                <div>
                    <p>This is an another dialog</p>
                </div>
            </e-content-template>
        </ej-dialog>

{% endhighlight %}


N> If the position of the dialog is not set as above, all the three dialogs will be overlapped with each other.

![](how-to_images\create-multiple-dialogs_img1.png)


## Create Nested Dialog

A Dialog widget can be nested within another Dialog widget.

Create a div element to render the child Dialog widget and use it as a content of parent Dialog widget.

{% highlight cshtml %}

    <ej-button id="outerbutton" text="Open Dialog" click="openDialog" />
    <ej-dialog id="outerdialog" title="Dialog" width="500" height="400" show-on-init="false">
        <e-dialog-position x-value="20" y-value="20" />
        <e-content-template>
            <ej-button id="innerbutton" text="Open Nested Dialog" click="openNestedDialog" />
        </e-content-template>
    </ej-dialog>
    <ej-dialog id="seconddialog" title="Window" width="400" height="300" show-on-init="false">
        <e-dialog-position x-value="300" y-value="20" />
        <e-content-template>
            <p>This is a nested dialog</p>
        </e-content-template>
    </ej-dialog>

{% endhighlight %}


Add the below script to the view page

{% highlight js %}


    <script>
        function openDialog() {
            $("#outerdialog").ejDialog("open");
        }
        function openNestedDialog() {
            $("#seconddialog").ejDialog("open");
        }
    </script>



{% endhighlight %}

