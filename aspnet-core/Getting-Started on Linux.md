---
layout: post
title: Getting Started on Linux| ASP.NET Core | Syncfusion
description: Getting Started on Linux.
platform: aspnet-core 
control: Common 
documentation: ug
---


# Getting Started on Linux

The below guidelines demonstrate how to create an ASP.NET Core application and configure with our Essential Studio MVC Components.

## Prerequisites:

* Visual Studio [Code](https://code.visualstudio.com/).

* Mono

* .NET Core [SDK](https://dotnetcli.blob.core.windows.net/dotnet/Sdk/rel-1.0.0/dotnet-sdk-ubuntu-x64.latest.deb)

Set up the apt-get feeds, then install .NET Core on Ubuntu or Linux Mint. Execute the below commands in terminal window to set up the apt-get feeds for Ubuntu 14.04 and 16.04.

### Ubuntu 14.04 / Linux Mint 17

Open your terminal window and execute the following commands
{% highlight text %}
sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ trusty main" > /etc/apt/sources.list.d/dotnetdev.list'

sudo apt-key adv --keyserver apt-mo.trafficmanager.net --recv-keys 417A0893

sudo apt-get update
{% endhighlight %}
### Ubuntu 16.04

Open your terminal window and execute the following commands
{% highlight text %}
sudo sh -c 'echo "deb [arch=amd64] https://apt-mo.trafficmanager.net/repos/dotnet-release/ xenial main" > /etc/apt/sources.list.d/dotnetdev.list'

sudo apt-key adv --keyserver apt-mo.trafficmanager.net --recv-keys 417A0893

sudo apt-get update

{% endhighlight %}

### Mono Installation

The [Mono Project](http://www.mono-project.com/) (powered by Xamarin) is a project that tends to make the .NET Framework available to Microsoft's foreign platforms. To run our ASP.NET Core 1.0 web application on Linux, install the Mono by executing the below commands.

* Execute this command to add the Mono's GPG key to the packages manager.
{% highlight text %}
apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF

{% endhighlight %}
* Then need to add the required repositories to the configuration file.
{% highlight text %}
echo "deb http://download.mono-project.com/repo/debian wheezy main" | sudo tee /etc/apt/sources.list.d/mono-xamarin.list

echo "deb http://download.mono-project.com/repo/debian wheezy-apache24-compat main" | sudo tee -a /etc/apt/sources.list.d/mono-xamarin.list

{% endhighlight %}

* Before the Mono installation, execute the below command to download the packages list from the repositories and update the packages with new version.
{% highlight text %}
sudo apt-get update
{% endhighlight %}

* Finally install the Mono.
{% highlight text %}
sudo apt-get install mono-complete
{% endhighlight %}

### .NET Core SDK installation

Before you start, please ensure any previous .NET Core version installed on your machine. If its exists remove the previous version by using this [script](https://github.com/dotnet/cli/blob/rel/1.0.0/scripts/obtain/uninstall/dotnet-uninstall-debian-packages.sh).

* Executing the following command automatically install the .Net Core SDK.
{% highlight text %}
sudo apt-get install dotnet-dev-1.0.0-preview2-003121
{% endhighlight %}

## Configuration

To configure an ASP.NET Core application and utilize our Essential Studio MVC components, follow the below guidelines.

* Create an ASP.NET Core Project.
* Configuring Syncfusion Components.

### Create an ASP.NET Core Application
ASP.NET Core Web application can be created in any one of the following ways.
* Terminal (Command Line).
* Yeoman.

#### Building Projects with Command Line
The following steps helps to create a ASP.NET Core web application using terminal window.
* Open a terminal window to create a new directory for your project creation.

{% highlight text %}
mkdir Sample
{% endhighlight %}


* Then navigate to your folder directory in your terminal window.
* In terminal window, you have an option to develop a below listed types of ASP.NET Core projects. The default project type as console application. If you want to create any other specific type project, need to specify the **-t** (**template**) key in command before the project type name. To know more about the project options and its syntax declarations refer the dotnet link.


{% highlight text %}
* console
* web
* lib
* xunittest
{% endhighlight %}



* Then run the below mentioned command to create a new web application. After this command execution the project will be created within your folder.

{% highlight text %}
dotnet new -t web
{% endhighlight %}

#### Building Projects with Yeoman
Yeoman is a scaffolding tool for modern web apps and helps us to quick start a new web project. The following steps helps to create an ASP.NET Core 1.0 application using [yeoman](http://yeoman.io/) tool.
Since **Visual Studio Code** uses folder structure for storing files of application, create a folder of the name **ASP.NET**.

* Open the Terminal window and execute the below mentioned command  to install the Node.js.
{% highlight text %}
curl -sL https://deb.nodesource.com/setup_4.x | sudo -E bash -

sudo apt-get install -y nodejs

{% endhighlight %}
* Install Yeoman and aspnet generator.
{% highlight text %}
sudo npm install -g yo generator-aspnet

{% endhighlight %}




* Once Yeoman generator installed successfully, run the below command to invoke a ASP.NET Core project creation wizard.

{% highlight text %}
yo aspnet

{% endhighlight %}

![](getting-started_images_linux/img1.jpg)

* From the list of available projects, select the *Web Application Basic* [without Membership and Authorization] by using arrow keys.

![](getting-started_images_linux/img2.jpg)

* And then provide the project name or simply press the ‘Enter’ key to create the project with default name.

![](getting-started_images_linux/img3.jpg)

### Configuring Syncfusion Components

* Open Visual Studio Code and open your Sample application folder using **Open Folder** option. Now your project folder is loaded in Visual Studio Code application.

![](getting-started_images_linux/img4.jpg)

* Click the Extension icon in the Visual Studio Code left side pane, in the search window type the command *bower*. The bower related extensions are listed out. Now select the Bower extension and click the install button.

![](getting-started_images_linux/img5.jpg)

* In **bower.json** file specify our Syncfusion packages with our latest version, or else specify the **`*`** symbol will automatically loads our latest version scripts and CSS files.

![](getting-started_images_linux/img6.jpg)

* Then open quick window to enter the *`>bower`* command and press ‘Enter’ key, from the below list of suggestions select the **bower install** option to restored our scripts and CSS into your application **wwwroot -> lib** folder.

![](getting-started_images_linux/img7.jpg)

* Now refer our Syncfusion package **Syncfusion.EJ.MVC** into your application for our components deployment. The packages configuration & installation guidelines will be documented [here]
(https://help.syncfusion.com/extension/syncfusion-nuget-packages/nuget-install-and-configuration#confuguring-syncfusion-nuget-packages-from-command-line-in-linuxmac).

* Once the NuGet packages installation gets completed, open your **Project.json** file to include our **Syncfusion.EJ.MVC** package reference.

![](getting-started_images_linux/img8.jpg)

* Open **_viewimports.cshtml** file from the views folder and add the following namespace for components references and Tag Helper support.

{% highlight cshtml %}
@using Syncfusion.JavaScript
@addTagHelper *, Syncfusion.EJ
{% endhighlight %}

* Open Terminal window and navigate to your project folder then execute the following command to restore the packages which are all specified in your **project.json** file.

{% highlight text %}
dotnet restore
{% endhighlight %}

![](getting-started_images_linux/img9.jpg)

* Now refer the necessary scripts and CSS files in your **_layout.cshtml** page.

{% highlight cshtml %}
<html>

<head>

<environment names="Development">

<link rel="stylesheet" href="~/lib/bootstrap/dist/css/bootstrap.css" />

<link rel="stylesheet" href="~/css/site.css" />

<link href="~/lib/syncfusion-javascript/Content/ej/web/bootstrap-theme/ej.web.all.min.css" rel="stylesheet" />

<link href="~/lib/syncfusion-javascript/Content/ej/web/responsive-css/ej.responsive.css" rel="stylesheet" />

</environment>

</head>

<body>

<environment names="Development">

<script src="~/lib/jquery/dist/jquery.js"></script>

<script src="~/lib/bootstrap/dist/js/bootstrap.js"></script>

<script src="~/js/site.js" asp-append-version="true"></script>

<script src="~/lib/jquery.easing/js/jquery.easing.min.js"></script>

<script src="~/lib/syncfusion-javascript/Scripts/jsrender.min.js"></script>

<script src="~/lib/syncfusion-javascript/Scripts/ej/web/ej.web.all.min.js"></script>

</environment>

</body>

</html>

{% endhighlight %}

* Add **ScriptManager** to the bottom of the **layout.cshtml** page. The **ScriptManager** used to place our control initialization script in the page.
{% highlight cshtml %}
   
    <ej-script-manager></ej-script-manager>
	
{% endhighlight %}

* Now open your view page to render our Syncfusion components in Tag Helper syntax.

 {% highlight cshtml %}
   
	<ej-date-picker id="datepicker" value="@DateTime.Now"></ej-date-picker>
	
{% endhighlight %}

* Finally execute the **dotnet run** command to run your sample browser.

* Then open your browser and paste the listening port **localhost:5000** to view your sample in browser.

![](getting-started_images_linux/img10.jpg)