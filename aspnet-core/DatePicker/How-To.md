---
layout: post
title: How-to
description: How-to section - The frequently used options with DatePicker 
platform: aspnet-core
control: DatePicker
documentation: ug
---
# How to?

## Customizing template with range selection between two DatePicker. 

You can customize the date field to emphasize the particular dates in Essential ASP.NET Core  DatePicker calendar with help of [SpecialDates](http://help.syncfusion.com/js/api/ejdatepicker#members:specialdates) and set the date range using [MinDate](http://help.syncfusion.com/js/api/ejdatepicker#members:mindate) and [MaxDate](http://help.syncfusion.com/js/api/ejdatepicker#members:maxdate) property. 

## Validating the date value in server side
	
The Essential ASP.NET Core DatePicker control, is a form control which  allows us to validate the date value in client side and server side actions. Please refer from the [validation](https://www.syncfusion.com/kb/5433/how-to-achieve-the-required-field-validation-for-datepicker-control-in-asp-net-mvc) to know more about this with EJMVC DatePicker control.

## Localize DatePicker with browser specific culture

You can get the browser culture name at page load or document ready state. Based on the culture name, The Essential ASP.NET Core DatePicker can be initiated with that specific culture value by assigning to [Locale](http://help.syncfusion.com/js/api/ejdatepicker#members:locale) property. 

## Disable specific dates to restrict user

Essential ASP.NET Core DatePicker allows you to restrict date selection in specific range by using date range option. But you can also restrict selective date in DatePicker calendar by utilizing [BeforeDateCreate](http://help.syncfusion.com/js/api/ejdatepicker#events:beforedatecreate) event. This event will get triggered at each date creation. So you can disable the selective date in this event to restrict the user.

{% highlight cshtml %}

    @*handler to listen each date create*@

    <ej-date-picker id="datepick" before-date-create="restrictDate"></ej-date-picker>

    <script>   
   
    //event get triggered for each date create.
    function restrictDate(args) {
       //date to disable in calendar to restrict selection.
       var disableDate = new Date("09/22/2015"); 
       //compares two and adds the disable class.
       if (+args.date === +disableDate)                
           args.element.addClass('e-disable');  
           // args contains current date and its element.          
    }
         
    </script>


{% endhighlight %}

## How to integrate with bootstrap grid system? 

Essential ASP.NET Core  DatePicker is responsive control, you have to just set the input element width as 100%. In Bootstrap grid layout use the below code example to get responsive textbox 

{% highlight cshtml %}

    @*sets the width to 100%*@

     <ej-date-picker id="datepick" width="100%"></ej-date-picker>


{% endhighlight %}
