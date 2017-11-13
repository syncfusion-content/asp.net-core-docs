---
layout: post
title: How To | Tooltip | ASP.NET Core | Syncfusion
description: How To section of Tooltip widget
platform: aspnet-core
control: Tooltip
documentation: ug
keywords : Dotnetcore Tooltip,ASP Dotnet Core Tooltip, core Tooltip,aspnetcore Tooltip widget,Dotnetcore Tooltip AJAX content,Dotnetcore Tooltip Integration with Slider
---

# How To

## Use AJAX to generate the Tooltip’s content

Use jQuery’s built-in AJAX functionality to retrieve remote content and set the content to the Tooltip as follows.

Define three employee’s JSON Array as given below(an array of 3 employees records)

{% highlight Js %}

    [
        {
            "EmployeeID": 1,
            "LastName": "Davolio",
            "Title": "Sales Representative",
            "TitleOfCourtesy": "Dr.",
            "Address": "507 - 20th Ave. E.Apt. 2A",
            "City": "Seattle",
            "Region": "WA",
            "PostalCode": "98122",
            
        },
        {
            "EmployeeID": 2,
            "LastName": "Buchanan",
            "Title": "Sales Representative",
            "TitleOfCourtesy": "Dr.",
            "Address": "908 W. Capital Way",
            "City": "Tacoma",
            "Region": "WA",
            "PostalCode": "98401",
            
        },
        {
            "EmployeeID": 3,
            "LastName": "Leverling",
            "Title": "Sales Representative",
            "TitleOfCourtesy": "Dr.",
            "Address": "722 Moss Bay Blvd.",
            "City": "Kirkland",
            "Region": "WA",
            "PostalCode": "98033",
            
        }
    ]

{% endhighlight %}

Render the employees table and create the tooltip. Once the tooltip created, the data will be fetched using AJAX method as follows.

{% highlight CSHTML %}

    <div class="frame">
        <table id="details">
            <tr>
                <th>EmployeeID</th>
                <th>Name</th>
                <th>Designation</th>
            </tr>
            <tr>
                <td>SF6089</td>
                <td><a href="#" class="e-info" title="Davolio">Davolio</a></td>
                <td>Software Engineer</td>
            </tr>
            <tr>
                <td>SF6073</td>
                <td> <a href="#" class="e-info" title="Leverling">Leverling </a> </td>
                <td>Tester</td>
            </tr>
            <tr>
                <td>SF6073</td>
                <td> <a href="#" class="e-info" title="Suyama"> Suyama </a> </td>
                <td>Content Writer</td>
            </tr>
            <tr>
                <td>SF7896</td>
                <td> <a href="#" class="e-info" title="Buchanan"> Buchanan </a> </td>
                <td>Graphics Designer</td>
            </tr>
        </table>
    </div>

    <ej-tooltip id="details" target=".e-info" width="350px" height="128px" before-open="onOpen">
        <e-tooltip-position>
            <e-stem horizontal="left" vertical="top" />
            <e-target horizontal="right" vertical="bottom" />
        </e-tooltip-position>
    </ej-tooltip>

    <script type="text/javascript">
        var content;
        var target = $("#details").data("ejTooltip");
        function onOpen(args) {
            proxy = args;
            $.ajax({
                dataType: "json",
                url: "tooltipData.js",
                success: function (result) {
                    var employee = [
                        { photo: "http://aspnetcore.syncfusion.com/images/Employees/2.png" },
                        { photo: "http://aspnetcore.syncfusion.com/images/Employees/4.png" },
                        { photo: "http://aspnetcore.syncfusion.com/images/Employees/8.png" },
                        { photo: "http://aspnetcore.syncfusion.com/images/Employees/3.png" },
                        { photo: "http://aspnetcore.syncfusion.com/images/Employees/1.png" },
                        { photo: "http://aspnetcore.syncfusion.com/images/Employees/6.png" },
                    ];
                    for (i = 0; i < result.length ; i++) {
                        if (result[i].LastName == $(proxy.event.target).attr("data-content"))
                            content = '<div class="main"> <img src=' + employee[i].photo + ' class="logo"/><div class="des"><table> <tr> <th> ' + result[i].TitleOfCourtesy + ' ' + result[i].LastName + '</th> </tr> <tr> <td> Title </td> <td>&nbsp;&nbsp;: ' + result[i].Title + '</td> </tr> <tr><td> Address</td><td>&nbsp;&nbsp;: ' + result[i].Address + '</td> </tr><tr> <td> City </td> <td>&nbsp;&nbsp;: ' + result[i].City + '</td> </tr> <tr> <td> PostalCode </td> <td>&nbsp;&nbsp;: ' + result[i].PostalCode + '</td> </tr> </table></div></div>';
                    }
                    target.setModel({ content: content });
                }
            });
            target.show(args.event.target);
            args.cancel = true;
        }
    </script>
        
{% endhighlight %}

Defines the style for the tooltip layout and table as follows.

{% highlight css %}

    <style>
        .frame {
            width: 100%;
            box-sizing: border-box;
        }

        .frame table {
            border-collapse: collapse;
            width: 100%;
        }

        .frame th, .frame td {
            text-align: left;
            padding: 8px;
        }

        .logo {
            float: left;
            width: 100px;
            height: 114px;
        }

        .frame tr:nth-child(even) {
            background-color: #f2f2f2;
        }

        .frame th {
            background-color: #4CAF50;
            color: white;
        }
        
        .des {
            width: 230px;
            float: right;
            line-height: 24px;
        }
    </style>
    
{% endhighlight %}

![](HowTo_images/ajax.png)

## Integration with the Slider control

Tooltip can also be integrated with various other jQuery plugin. Tooltip shows the slider value above the handle.

Render the slider control and finds its handle to render the Tooltip as follows

{% highlight CSHTML %}

    <div class="frame">
        <div id="loanheading">
            Details of Loan
        </div>

        <span class="ColumnLeft">
            <span class="loan">Loan Amount</span>
        </span>
        <span class="ColumnRight">
            <span class="value">1000</span><span id="loantext">$ </span>
        </span>

       <ej-slider id="loanSlider" height="16px" value="100" min-value="10" max-value="1000" increment-step="10" change="onSlide" slide="onSlide" stop="onStop" />

    </div>

    <ej-tooltip id="loanSlider" target=".e-handle" show-rounded-corner="true" is-balloon="true" ></ej-tooltip>

    <script>

        $(function () {
            var loanObj = $('#loanSlider').data("ejSlider"); 
            var loadTip = $('#loanSlider').data("ejTooltip"); 
            loadTip.setModel({content : "$ " + loanObj.getValue().toString() });
        });

    </script>
    
{% endhighlight %}

Once the handler in the slider, start its sliding the below function will be triggered

{% highlight CSHTML %}

function onSlide(args) {
    
    this.wrapper.prev().children('span.value').html(args.value);
    var  value = args.value.toString();
    if(args.id == "loanSlider")
        value =  "$ " +value;
    var tipWidth = (value < 10) ? "13px" : (10 <= value >= 100) ? "25px" : "auto";
    var tipObj = $('#loanSlider').data("ejTooltip");
    tipObj.setModel({content : value, width : tipWidth});
    tipObj.show($("div" + target).find(".e-handle"));
} 

{% endhighlight %}

Once the sliding is stopped, the Tooltip will be shown for the particular period of time then it will be closed. 

{% highlight CSHTML %}

function onStop(args){
    setTimeout( function(){ 
        var tipObj = $('#loanSlider').data("ejTooltip");
        tipObj.hide();
    }, 1000);
}
        
{% endhighlight %}

![](HowTo_images/slider.png)

## Tip(arrow) customization

Styling the Tip's background and border colors is done using "cssClass" API of Tooltip. Change the size of the tip using the property name called "Tip" and CSS as follows.

{% highlight CSHTML %}

    <div class="frame">
        <div class="img" id="custom">
            <img src="http://aspnetcore.syncfusion.com/images/tooltip/template-04.png" alt="Roslyn Succinctly" >
            <div class="desc">Roslyn Succinctly</div>
        </div>
    </div>
    
    <ej-tooltip id="custom" content="Learn to use the Python language to create programs of all kinds to creating practical applications." width="200px">
        <e-tooltip-position>
            <e-stem horizontal="left" vertical="top" />
            <e-target horizontal="right" vertical="bottom" />
        </e-tooltip-position>
        <e-tip>
            <e-size height="12" width="25" />
        </e-tip>
    </ej-tooltip>

    <script type="text/javascript">
        $(function () {
            target = $("#custom").data("ejTooltip");
        });
    </script>
    
{% endhighlight %}

Defines the style for the tip as follow as

{% highlight css %}
    
    <style>
        div.img {
            border: 1px solid #ccc;
            width: 159px;
            height: 213px;
            left: 35%;
            position: relative;
            top: 20%;
        }
        div.img img{
            width: 159px;
            height: 179px;
        }
        div.desc {
            padding: 8px;
            text-align: center;
        }
    </style>
    
{% endhighlight %}

![](HowTo_images/tip.png)

## Initialize Tooltip for the target element

Tooltips are also useful for input elements, to show hint in the context of each field.

Rather than using multiple Tooltips, a single Tooltip can be used to show the information of each and every field of the form/table element. This can be achieved using “target” API. Target property Specifies a selector for elements, within the container, for which the Tooltip will be displayed.

The example below demonstrates how to create a Tooltip for multiple targets element. 

{% highlight CSHTML %}

    <form id="details" role="form">
        <fieldset>
            <table>
                <tr>
                    <td class="info"> User Name:</td>
                    <td> <input type="text" class="e-info" name="firstname" title="Please enter your name"> </td>
                </tr>
                <tr>
                    <td class="info"> Email Address:</td>
                    <td> <input type="text" class="e-info" name="email" title="Enter a valid email address"></td>
                </tr>

                <tr>
                    <td class="info"> Password:</td>
                    <td> <input type="password" class="e-info" name="password" title="Be at least 8 characters length"></td>
                </tr>
                <tr>
                    <td class="info"> Confirm Password:</td>
                    <td> <input type="password" class="e-info" name="Cpwd" title="Re-enter your password"></td>
                </tr>
            </table>
            
            <ej-button id="sample" text="Submit" typeof="@ButtonType.Submit" size="@ButtonSize.Medium" show-rounded-corner="true"   />
            <ej-button id="clear" text="Reset" typeof="@ButtonType.Reset" size="@ButtonSize.Medium" show-rounded-corner="true" />
                    
        </fieldset>
    </form>

    <ej-tooltip id="details" target=".e-info" height="30px" width="180px" create="onCreate" before-open="onOpen">
        <e-tooltip-position>
            <e-stem horizontal="left" vertical="center" />
            <e-target horizontal="right" vertical="center" />
        </e-tooltip-position>
    </ej-tooltip>

{% endhighlight %}

![](Target_images/target.png)

Apply the following styles to the form element.

{% highlight css %}

    <style>

        th, td {
            padding: 15px;
            text-align: left;
        }
        #form {
            position: absolute;
            left: 200px;
        }
        fieldset {
            border: 1px solid #D9DEDD;
            padding: 15px;
            width: 400px;
        }
        .info {
            font-weight: bold;
        }
        #sample {
            margin-right: 50px;
        }
        .e-button {
            margin: 10px;
        }

    </style>
    
{% endhighlight %}

## Interact with the Tooltip

Give users, the possibility to interact with the tooltip. If the tooltip is interactive and activated by a hover event, set the amount of time (milliseconds)allowed for a user to hover off of the tooltip activator on to the tooltip itself – keeping the tooltip from closing using “autoCloseTimeout”  property.

Using this property, Links can be provided in Tooltip content where user can navigate to some other page. This is handy for situations where you need to grab the user attention.

{% highlight CSHTML %}

    <div class="control">
        TypeScript lets you write <a id="test"><u> JavaScript</u> </a>the way you really want to.
    </div>

    <ej-tooltip id="test" content="JavaScript is the programming language of HTML and the Web." close-mode="Auto" auto-close-timeout="2000">
    </ej-tooltip>

{% endhighlight %}
