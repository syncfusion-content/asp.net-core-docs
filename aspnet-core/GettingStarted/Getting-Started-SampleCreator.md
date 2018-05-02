---
layout: post
title: Getting Started | ASP.NET Core | Syncfusion
description: Getting Started.
platform: aspnet-core 
control: Common 
documentation: ug
---


# Getting Started

## Sample Creator

Sample Creator is the utility that allows you to create Syncfusion ASP.NET Core Projects along with the samples based on Controls and Features selection.

I> The Syncfusion ASP.NET Core Sample Creator utility is available from v15.2.0.40.

## Create Syncfusion ASP.NET Core Web Application from Sample Creator

The following steps help you to create the Syncfusion ASP.NET Core Web Application via the Sample Creator utility.

1. Launch the Syncfusion Essential Studio Dashboard and select the ASP.NET Core platform. Select the SAMPLE CREATOR button to launch the ASP.NET Core Sample Creator Wizard. Refer the following screenshot for more information.

   ![](getting-started-SampleCreator-images/SampleCreator_img1.jpeg)

2. Syncfusion Sample Creator Wizard displaying the **Controls and its Feature Selection** section

   ![](getting-started-SampleCreator-images/SampleCreator_img2.jpeg)


### Controls Selection

Listed here are the Syncfusion ASP.NET Core controls so you can choose the required controls.

   ![](getting-started-SampleCreator-images/SampleCreator_img3.jpeg)

### Feature Selection

Based on the controls, the Feature is enabled to choose the features of the corresponding controls.

   ![](getting-started-SampleCreator-images/SampleCreator_img4.jpeg)


### Project Configuration

1. You can configure the following project details in the Sample Creator.

   * Project Type – Select the type of ASP.NET Core Project, either .NET Core or .NET Framework.
   
   * ASP.NET Core Version - Select the version of ASP.NET Core Project, either ASP.NET Core 1.0 or ASP.NET Core 1.1.

   * VS Version – Choose the Visual Studio version.

   * .NET Framework – Choose the .NET Framework version.
   
   * Assets From – Load the Syncfusion assets to ASP.NET Core Project, either Bower, CDN or Installed Location.

   * Name – Name your Syncfusion ASP.NET Core Application.

   * Location – Choose the target location of your project.

   * Theme Selection – Choose the required theme.The Theme Preview section shows the controls preview before create the Syncfusion project.

   ![](getting-started-SampleCreator-images/SampleCreator_img6.jpeg)


2. When you click the Create button, the new Syncfusion ASP.NET Core project is created. The following resources are added in the project:

   * Added the required View(.cshtml) and Class files in the project.

     ![](getting-started-SampleCreator-images/SampleCreator_img7.jpeg)

   * Included the required Syncfusion scripts and themes files.

     ![](getting-started-SampleCreator-images/SampleCreator_img8.jpeg)

   * Restored the required Syncfusion NuGet/Bower packages for selected controls under dependencies.

     ![](getting-started-SampleCreator-images/SampleCreator_img9.png)

> The ASP.NET Core NuGet packages versioning has been streamlined as 16.1.0.32 in shorter than older versioning (16.1600.0.32) from Volume 1, 2018 service pack 1 release (16.1.0.32). Since all the framework version wise assemblies are grouped into a single package.

3. Once the project is created you can open the project by clicking the Yes button. If you click No button the corresponding location of the project will be opened. Refer the following screenshot for more information.

   ![](getting-started-SampleCreator-images/SampleCreator_img11.jpeg)