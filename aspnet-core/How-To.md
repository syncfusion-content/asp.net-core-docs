---
layout: post
title: How To | ASP.NET Core | Syncfusion
description: How To
platform: aspnet-core
control: Common 
documentation: ug
---

# How To

## Overcome model expression known issue in ASP.NET Core 2.0

The latest ASP.NET Core 2.0 SDK has below mentioned known [issue](https://github.com/aspnet/Razor/issues/1618)
while using the model expression within a rendering section. This same issue occured in our components while using model expressions.

> A local or parameter named '__model' cannot be declared in this scope because that name is used in an enclosing local scope to define a local or parameter. 

If you want to use the model expressions in your application, then utilize the below workaround solution to resolve this issue.

Declare the model expressions related code blocks in your partial view and call that partial view in your rendering section **(@Html.Partial("partialviewname"))** to resolve this issue.

For exmaple view:

   ~~~ cshtml
           
        <div>  

            @* Partial view returns the control with model expressions value*@ 
            @Html.Partial("dateview")

        </div>
   ~~~

For example partial view ('dateview'):
   
   ~~~ cshtml
   
        @model sample.models.datemodel

        <div>        
            <ej-date-picker id="datepick" ej-for="@Model.Value" />

            @* in partial view, mandatory to define the script manager for control rendering*@ 
            <ej-script-manager></ej-script-manager>
        </div>
   ~~~
