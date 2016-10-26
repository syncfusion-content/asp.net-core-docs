---
layout: post
title: Getting-Started
description: getting started
platform: aspnet-core
control: TimePicker
documentation: ug
---

# Getting Started

This section explains briefly about how to create  and customize a TimePicker in an ASP.net Core application.

## Create your first TimePicker

Essential TimePicker provides support to display the time in your web page and allows you to pick a time from the dropdownlist. In this section you can learn how to customize TimePickers in a real-time application. The following example shows you how to use the TimePicker control to book a hotel dining table booking application, within a limited time, in any day.

![](Getting-Started_images/Getting-Started_img1.png)

The above screenshot illustrates the functionality of a TimePicker, with a time range from morning to evening. You can select the time to book a table ranging from 9.00 AM to 10.00 PM in the current day. This avoids selecting a time prior to that day.


### Create a TimePicker

Essential TimePicker widget has built-in features such as keyboard navigation, other time navigation with animations, and flexible APIs. You can easily create the TimePicker widget using simple TimePicker element as follows.

1. [Getting Started](/aspnet-core/getting-started) section explains about basic system requirements and the steps to configure the Syncfusion Components in an ASP.net core application.

    After successfuly adding the neccessary dependencies in your solution, make sure to build the solution, so that the neccessary assembly files are compiled properly before using it in your project.

2. Add the following code to the corresponding view page to render the TimePicker.

   {% highlight CSHTML %}


	@*Add the following code example to the corresponding CSHTML page to render TimePicker widget*@

	<table>

            <tr>

                <td class="tdclass">Date</td>

                <td class="tdclass">Time</td>

                <td class="tdclass">Person</td>

            </tr>

            <tr>

                <td class="tdclass">

                    <span class="innerdp">

                        <ej-date-picker id="startDate"></ej-date-picker>

                    </span>

                </td>

                <td class="tdclass">

                    <span class="innerdp">

                        <ej-time-picker id="timestart"></ej-time-picker>

                    </span>

                </td>

                <td class="tdclass">

                    <span class="innerdp">

                        <ej-numeric-text-box id="NumericTextbox" value="0" />

                    </span>

                </td>

            </tr>

            <tr>

                <td></td>

                <td></td>

                <td class="tdclass">

                    <span class="innerdp">

                        <ej-button id="Submit" width="100px" size="Small" text="Submit" click="Confirm" />

                    </span>

                </td>

            </tr>

        </table>

   {% endhighlight %}
   
3. Add the following styles to show the TimePicker control in horizontal order in the Content folder.

   ~~~ css


	<style type="text/css" class="cssStyles">

		.tdclass 
		{

		width: 70px;

		height: 10px;

		font-weight: bold;

		padding: 10px;

		}

		.innerdp 
		{

		display: inline-block;

		}

	</style>

   ~~~
   
4. Add the following code to the Layout page for DatePicker and TimePicker initialization.

   ~~~ js


	<script type="text/javascript">

		function Confirm()

		{

		alert("You have Successfully booked");

		}

	</script>

   ~~~
   



5. The following screenshot displays the output for the above code.

   ![](Getting-Started_images/Getting-Started_img2.png)





6. Click the submit button in the application to get the following output.

   ![](Getting-Started_images/Getting-Started_img3.png)


### Set Min and Max Date

In a real-time scenario, the booking is open only for a limited time. You can select a date and time from the given range using the properties MinDate, MinTime and MaxDate, MaxTime that enables only the dates and times ranging between the MinDate, MinTime and MaxDate, MaxTime in the DatePicker and TimePicker.

1. Add the following code to the corresponding view page to render the TimePicker.

   {% highlight CSHTML %}

	@*Add the following code example to the corresponding CSHTML page to render TimePicker widget*@

	<table>

            <tr>

                <td class="tdclass">Date</td>

                <td class="tdclass">StartTime</td>

                <td class="tdclass">EndTime</td>

                <td class="tdclass">Person</td>

            </tr>

            <tr>

                <td class="tdclass">

                    <span class="innerdp">

                        <ej-date-picker id="startDate" value="DateTime.Now" min-date="DateTime.Now" max-date="DateTime.Now.AddDays(1)"></ej-date-picker>

                    </span>

                </td>

                <td class="tdclass">

                    <span class="innerdp">

                        <ej-time-picker id="timeStart" min-time="9:00 AM" max-time="10:00 PM" interval="60" select="selectedStartTime"></ej-time-picker>
                    </span>

                </td>

                <td class="tdclass">

                    <span class="innerdp">

                        <ej-time-picker id="timeEnd" min-time="9:00 AM" max-time="10:00 PM" interval="60"></ej-time-picker>

                    </span>

                </td>

                <td class="tdclass">

                    <span class="innerdp">

                        <ej-numeric-text-box id="NumericTextbox" value="0" />

                    </span>

                </td>

            </tr>

            <tr>

                <td></td>

                <td></td>

                <td></td>

                <td class="tdclass">

                    <span class="innerdp">

                        <ej-button id="Submit" width="100px" size="Small" text="Submit" click="Confirm" />

                    </span>

                </td>

            </tr>

        </table>

   {% endhighlight %}
   

2. Add the following styles to show the TimePicker control in horizontal order in the Content folder.

   {% highlight css %}

	<style type="text/css" class="cssStyles">

		.tdclass {

        width: 70px;

        height: 10px;

        padding: 10px;
        
        color: #333;

        font-family: Segoe UI;
        
        font-weight: 500;

        font-size: 14px;

        }

		.innerdp 
		{

		display: inline-block;

		}


	</style>

   {% endhighlight %}
   




3. Add the following code to the Layout page for DatePicker and TimePicker initialization.

   ~~~ js


		<script type="text/javascript">

		    function selectedStartTime(sender) {

			var selDate = sender.value; // mentions the selected time.

			minTimepicker = $("#timeend").data("ejTimePicker");// creating TimePicker object

			minTimepicker.setModel({ "minTime": selDate });// setting minTime property through setModel of TimePicker object.

		    }

		    function Confirm()

		    {

			alert("You have Successfully booked");

		    }

		</script>

   ~~~
   





4. The following screenshot displays the output for the above code. 

![](Getting-Started_images/Getting-Started_img4.png)





You can select the Start time in the first TimePicker and select the End time within the given range. The second TimePicker start value is based on the first TimePicker’s selected value. This is illustrated in the following screenshots.



![](Getting-Started_images/Getting-Started_img5.png)


![](Getting-Started_images/Getting-Started_img6.png)



### Display Reserved Time 

An acknowledgment message appears when you click the Submit button. 

You can specify the alert message in the script as follows.

{% highlight js %}

<script type="text/javascript">

        function button()

            {



                    var a = $('#startDate').val();



                    var b = $('#timestart').val();



                    var d = $('#timeend').val();



                    var c = $('#NumericTextbox').val();



                    alert("You have successfully booked\nDate    : " + a + "\nStartTime: " + b + "\nEndTime: " + d + " \nPerson   :  " + c);



            }

</script>

{% endhighlight %}


![](Getting-Started_images/Getting-Started_img7.png)



