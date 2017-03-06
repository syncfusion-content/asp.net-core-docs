---
layout: post
title: Localization
description: localization
platform: aspnet-core
control: PivotGauge
documentation: ug
---

# Localization

## Localization in PivotGauge Control
We can localize the PivotGauge control texts with a collection of localized strings using **"ej.PivotGauge.Locale"** for different cultures.
 
N> By default, the PivotGauge control is localized in **"en-US"**.
 
Following code example illustrates on how to localize PivotGauge based on **"French"** culture.

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1" locale="fr-FR"></ej-pivot-gauge>

<script>
    ej.PivotGauge.Locale["fr-FR"] = {
        RevenueGoal: "Objectif de chiffre d'affaires",
        RevenueValue: "Valeur du chiffre d'affaires"
    }
</script>

{% endhighlight %}

Following table localizes the in-built keywords to **"French"** culture for PivotGauge.

<table>
<tr>
<th>
Keywords</th><th>
Values</th></tr>
<tr>
<td>
RevenueGoal</td><td>
"Objectif de chiffre d'affaires"</td></tr>
<tr>
<td>
RevenueValue</td><td>
"Valeur du chiffre d'affaires "</td></tr>
</table>

## Localization and Globalization of Cube Info

Content displayed within the PivotGauge control are obtained from the OLAP Cube. So following are the steps that needs to be done to get the localized and globalized Cube content.

To get the localized string based on different cultures, from OLAP Cube, we need to set **"Locale Identifier"** in the connection string to a specific culture. The attribute is set for PivotGauge in Client Mode as shown below

{% highlight cshtml %}

<ej-pivot-gauge id="PivotGauge1" locale="fr-FR">
    <e-data-source catalog="Adventure Works DW 2008 SE" cube="Adventure Works" data="//bi.syncfusion.com/olap/msmdpump.dll;Locale Identifier=1036"></e-data-source>
</ej-pivot-gauge>

{% endhighlight %}

![](Localization-and-Translation-Support_images/Localization.png) 
