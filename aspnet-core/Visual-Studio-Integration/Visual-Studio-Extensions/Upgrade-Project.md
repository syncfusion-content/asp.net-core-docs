---
layout: post
title: Upgrade Project | ASP.NET Core (Essential JS 1) | Syncfusion
description: Project Migration is a add-in that allows you to migrate existing Syncfusion ASP.NET Core Web Application from one Essential Studio version to another version
platform: aspnet-core
control: Syncfusion Extensions
documentation: ug
---

# Upgrade Project

Syncfusion Project Migration is a Visual Studio add-in that allows you to migrate the existing Syncfusion ASP.NET Core Web Application from one Essential Studio version to another.

I> The Syncfusion ASP.NET Core Web Application Project Migration utility is available from v15.2.0.40.

Use the following steps to migrate your existing Syncfusion ASP.NET Core Web Application: 

1. To open Migration Wizard, follow either one of the options below: 

   **Option 1**  
   Click **Syncfusion Menu** and choose **Essential Studio for ASP.NET Core (EJ1) > Migrate Project…** in **Visual Studio**.
   
   ![Syncfusion Essential JS 1 ASP.NET Core Project Migration via Syncfusion menu](Upgrade-Project_images/Syncfusion_Menu_Project_Migration.png)

   N> In Visual Studio 2019, Syncfusion menu is available under Extensions in Visual Studio menu.
   
   **Option 2**  
   Right-click the **Syncfusion ASP.NET Core Web Application** from Solution Explorer and select **Syncfusion Essential JS 1**. Choose **Migrate the Essential JS 1 Project to Another Version...**

   ![Syncfusion Essential JS 1 ASP.NET Core Project Migration add-in](Upgrade-Project_images/Project-Migration-img1.png)

2. The **Project Migration** window appears. You can choose the required Essential Studio version that is installed in the machine. 

   ![Syncfusion Essential JS 1 ASP.NET Core Project Migration window](Upgrade-Project_images/Project-Migration-img2.png)

3. The **Project Migration** window allows you to configure the following options:

   i. **Essential Studio Version:** Select any version from the list of installed versions.
   
   ii. **Assets From:** Load the Syncfusion assets to ASP.NET Core Project, either CDN or Installed Location.
   
4. Click the **Migrate** Button. The Project Backup dialog appears. In the dialog, if click **Yes**, it will backup the current project before migrating the Syncfusion project. If click **No**, it will migrate the project to required Syncfusion version without backup.
   
   ![Syncfusion Essential JS 1 ASP.NET Core Project Migration backup dialog](Upgrade-Project_images/Project-Migration-img3.jpeg)
      
5. The Syncfusion NuGet packages, Scripts, and CSS are updated to the corresponding version in the project.

