---
layout: post
title: Getting Started | ASP.NET Core | Syncfusion
description: Getting Started.
platform: aspnet-core 
control: Ribbon 
documentation: ug
---

# Getting Started

To run Ribbon sample in ASP.NET Core 1.0.1, Please refer the [`ASP.NET Core`](https://help.syncfusion.com/aspnet-core/getting-started) documentation to initially configure the common specifications. 

## Control Initialization

Ribbon can be initialized with `e-application-tab` and UL list is needed for binding Menu to application Menu which can be specified through `menu-item-id` which denotes `id` of UL.

Define the Application Tab with `type` as `Menu` to render simple Ribbon control.

{% highlight html %}

    <ul id="ribbonmenu">
        <li>
            <a>FILE</a>
            <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
                <li><a>Save</a></li>
                <li><a>Save as</a></li>
                <li><a>Print</a></li>
            </ul>
        </li>
    </ul>

{% endhighlight  %}

{% highlight CSHTML %}

    <ej-ribbon id="defaultRibbon" width="400px" allow-resizing="true">
    <e-application-tab type=Menu menu-item-id="ribbonmenu">
        <e-menu-settings open-on-click="false">
        </e-menu-settings>
    </e-application-tab>
    </ej-ribbon>

{% endhighlight  %}

{% highlight html %}

    @*To load Ribbon sample level icons*@

    @section StyleSection{
        <link href="@Url.Content("~/css/ejthemes/ribbon-css/ej.icons.css")" rel="stylesheet" />

    }

{% endhighlight  %}

![](getting-started-images/Ribbon_img.png)

## Adding Tabs

RibbonTab is a set of related groups which are combined into single item. For creating Tab,`id` and `text` properties should be specified.

{% highlight html %}

    <ul id="ribbonmenu">
        <li>
            <a>FILE</a>
            <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
                <li><a>Save</a></li>
                <li><a>Save as</a></li>
                <li><a>Print</a></li>
            </ul>
        </li>
    </ul>

{% endhighlight  %}

{% highlight CSHTML %}

    <ej-ribbon id="defaultRibbon" width="500px" allow-resizing="true" >
    <e-application-tab type=Menu menu-item-id="ribbonmenu">
        <e-menu-settings open-on-click="false">
        </e-menu-settings>
    </e-application-tab>
    <e-tabs>
        <e-tab id="home" text="HOME">
        </e-tab> 
    </e-tabs>
    </ej-ribbon>


{% endhighlight  %}

{% highlight html %}

    @*To load Ribbon sample level icons*@

    @section StyleSection{
        <link href="@Url.Content("~/css/ejthemes/ribbon-css/ej.icons.css")" rel="stylesheet" />

    }

{% endhighlight  %}

![](getting-started-images/Ribbon_img1.png)

## Configuring Groups

List of controls are combined as logical `e-content-group` into Ribbon Tabs. `e-group` alignment type as “Rows/Columns”, Default is `Rows`.
Create `e-group` item with `text` specified and add `e-content-group` to `e-content-group` collection with `e-button-settings `.

{% highlight html %}

    <ul id="ribbonmenu">
        <li>
            <a>FILE</a>
            <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
                <li><a>Save</a></li>
                <li><a>Save as</a></li>
                <li><a>Print</a></li>
            </ul>
        </li>
    </ul>

{% endhighlight  %}

{% highlight CSHTML %}

    <ej-ribbon id="defaultRibbon" width="500px" allow-resizing="true">
        <e-application-tab type=Menu menu-item-id="ribbonmenu">
            <e-menu-settings open-on-click="false">
            </e-menu-settings>
        </e-application-tab>
        <e-tabs>
            <e-tab id="home" text="HOME">
                <e-groups>
                    <e-group text="New" align-type=Rows>
                        <e-content>
                            <e-contents>
                                <e-content-groups>
                                    <e-content-group id="new" text="New">
                                        <e-button-settings content-type=ImageOnly image-position=ImageTop prefix-icon="e-icon e-ribbon e-new">
                                        </e-button-settings>
                                    </e-content-group>
                                </e-content-groups>
                                <e-defaults type=Button width="60px" height="70px" is-big="false"></e-defaults>
                            </e-contents>
                        </e-content>
                    </e-group>
                </e-groups>
            </e-tab>
        </e-tabs>
    </ej-ribbon>
 
{% endhighlight  %}

{% highlight html %}

    @*To load Ribbon sample level icons*@

    @section StyleSection{
        <link href="@Url.Content("~/css/ejthemes/ribbon-css/ej.icons.css")" rel="stylesheet" />

    }

{% endhighlight  %}

![](getting-started-images/Ribbon_img2.png)

## Adding Controls to Group

Syncfusion ASP.NET Core Controls can be added to TabGroup’s content with corresponding `type` specified like Button, SplitButton, ToggleButton, DropDownList, Gallery, Custom, etc. Default type is `Button`.

{% highlight html %}

    <ul id="ribbonmenu">
        <li>
            <a>FILE</a>
            <ul>
                <li><a>New</a></li>
                <li><a>Open</a></li>
                <li><a>Save</a></li>
                <li><a>Save as</a></li>
                <li><a>Print</a></li>
            </ul>
        </li>
    </ul>
    <ul id="pasteul">
         <li><a>Paste</a></li>
    </ul>


{% endhighlight  %}

{% highlight CSHTML %}

    <ej-ribbon id="defaultRibbon" width="500px" allow-resizing="true">
    <e-application-tab type=Menu menu-item-id="ribbonmenu">
        <e-menu-settings open-on-click="false">
        </e-menu-settings>
    </e-application-tab>
    <e-tabs>
        <e-tab id="home" text="HOME">
            <e-groups>
                <e-group text="SplitButton & Button" align-type=Columns>
                    <e-content>
                        <e-contents>
                            <e-defaults width="50" height="75" type=SplitButton></e-defaults>
                            <e-content-groups>
                                <e-content-group id="paste" tool-tip="Paste">
                                    <e-split-button-settings button-mode="Dropdown" arrow-position="Bottom" target-id="pasteul" content-type="TextAndImage" prefix-icon="e-icon e-ribbon e-ribbonpaste">
                                    </e-split-button-settings>
                                </e-content-group>
                            </e-content-groups>
                        </e-contents>
                        <e-contents>
                            <e-defaults width="60" height="25" is-big="false" type=Button />
                            <e-content-groups>
                                <e-content-group id="cut" tool-tip="Cut" text="Cut">
                                    <e-button-settings content-type="TextAndImage" type=Button prefix-icon="e-icon e-ribbon e-ribboncut" />
                                </e-content-group>
                                <e-content-group id="copy" tool-Tip="Copy" text="Copy">
                                    <e-button-settings content-type="TextAndImage" type=Button prefix-icon="e-icon e-ribbon e-ribboncopy" />
                                </e-content-group>
                                <e-content-group id="clear" tool-Tip="Clear All " text="Clear">
                                    <e-button-settings content-type="TextAndImage" Type=Button prefix-icon="e-icon e-ribbon clearAll" />
                                </e-content-group>
                            </e-content-groups>
                        </e-contents>
                    </e-content>
                </e-group>
            </e-groups>
        </e-tab>

    </e-tabs>
</ej-ribbon>
 
{% endhighlight  %}

{% highlight html %}

    @*To load Ribbon sample level icons*@

    @section StyleSection{
        <link href="@Url.Content("~/css/ejthemes/ribbon-css/ej.icons.css")" rel="stylesheet" />

    }

{% endhighlight  %}

![](getting-started-images/Ribbon_img3.png)