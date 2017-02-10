---
title: Essential Studio for ASP.NET Core 2017 Volume 1 Migration document
description: Essential Studio for ASP.NET Core 2017 Volume 1 Migration document
platform: aspnet-core
documentation: ug
keywords: migration, upgradation, upgrade-changes, 2017vol1-changes
---

# Common Changes

* As a part of NET Standard support, we are deprecating the existing packages and adding new packages as mentioned below. So the older packages are no longer shipped along with our next Essential Studio release.

<table class="params">
<tbody>
<tr>
<th>Deprecated packages</th>
<th>New packages</th>
</tr>
<tr>
<td>Syncfusion.Compression.AspNet.Core</td>
<td>Syncfusion.Compression.Portable</td>
</tr>
<tr>
<td>Syncfusion.DocIO.AspNet.Core</td>
<td>Syncfusion.DocIO.Portable</td>
</tr>
<tr>
<td>Syncfusion.OfficeChart.AspNet.Core</td>
<td>Syncfusion.OfficeChart.Portable</td>
</tr>
<tr>
<td>Syncfusion.Pdf.AspNet.Core</td>
<td>Syncfusion.Pdf.Portable</td>
</tr>
<tr>
<td>Syncfusion.Presentation.AspNet.Core</td>
<td>Syncfusion.Presentation.Portable</td>
</tr>
<tr>
<td>Syncfusion.XlsIO.AspNet.Core</td>
<td>Syncfusion.XlsIO.Portable</td>
</tr>
</tbody>
</table>

## DocIO

As a part of NET Standard support, we have made below changes

## PDF

As a part of NET Standard support, we have made below changes

## Presentation

As a part of NET Standard support, we have made below changes

* Presentation.Open(string filename) has been removed, instead make use of Presentation.Open(Stream inputFileStream) method.
* Presentation.Save(string filename) has been removed, instead make use of Presentation.Save(Stream outputFileStream) method.

## XlsIO

As a part of NET Standard support, we have made below changes