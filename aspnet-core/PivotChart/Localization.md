---
layout: post
title: Localization
description: localization 
platform: aspnet-core
control: PivotChart
documentation: ug
---

# Localization

## Localization in PivotChart

We can localize the PivotChart controls text with a collection of localized strings using **"ej.PivotChart.Locale"** for different cultures. By default, the PivotChart control is localized in **“en-US”.**

Following code example illustrates on how to localize PivotChart based on **“French”** culture.

{% highlight cshtml %}

<ej-pivot-chart id="PivotChart1" locale="fr-FR">
    <e-size width="950px" height="460px"></e-size>
</ej-pivot-chart>
<script type="text/javascript">
    ej.PivotChart.Locale["fr-FR"] = {
        Measure: "Mesure",
        Row: "Rangée",
        Column: "Colonne",
        Value: "Valeur",
        Expand: "Développer",
        Collapse: "Effondrement",
        Exit: "Quitter"
    };
</script>

{% endhighlight %}

Following table localizes the in-built keywords to **“French”** culture for PivotChart.

<table>
<tr>
<th>
KEYWORDS</th><th>
VALUES</th></tr>
<tr>
<td>
Measure</td><td>
“Mesure”</td></tr>
<tr>
<td>
Row</td><td>
"Rangée "</td></tr>
<tr>
<td>
Column</td><td>
"Colonne”</td></tr>
<tr>
<td>
Value</td><td>
" Valeur "</td></tr>
<tr>
<td>
Expand</td><td>
" Développer "</td></tr>
<tr>
<td>
Collapse</td><td>
" Effondrement "</td></tr>
<tr>
<td>
Exit</td><td>
“Quitter "</td></tr>
</table>

## Localization and Globalization of Cube Info (OLAP)

Content displayed within the PivotChart control are obtained from the OLAP Cube. So following are the steps that needs to be done to get the localized and globalized Cube content.

* To get localized data from OLAP Cube, we need to set **"Locale Identifier"** in the connection string to a specific culture in the **"Data"** property present inside **"DataSource"**. 
* To bind the globalized content in PivotChart control, we need to set **"Locale"** property to a specific culture and want to refer specific culture file in the sample.
 
N> Culture files are present under **"[installed drive]:\Users\ [user name]\AppData\Local\Syncfusion\EssentialStudio\X.X.X.X\Web\Samples\Web\Scripts\cultures".**
 
{% highlight cshtml %}

//1036 refers to “fr-FR” culture.
<ej-pivot-chart id="PivotChart1" locale="fr-FR" load="loadTheme">
    <e-data-source catalog="Adventure Works DW 2008 SE" cube="Adventure Works" data="//bi.syncfusion.com/olap/msmdpump.dll;Locale Identifier=1036;"></e-data-source>
    <e-size width="100%" height="460px"></e-size>
</ej-pivot-chart>

{% endhighlight %}

![](Localization-and-Translation-support_images/Localization-and-Translation-support_img1.png) 