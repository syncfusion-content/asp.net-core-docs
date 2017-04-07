---
layout: post
title: Splitter Integration | Splitter | ASP.NET Core | Syncfusion
description: splitter integration
platform: aspnet-core
control: Splitter
documentation: ug
keywords: integration
---

# Splitter Integration

The Splitter allows you to use other Essential ASP.NET MVC products inside the pane. The integrated function of those widgets can be used in other panes of the Splitter.

## Configuring other widgets in Splitter

The following steps explain the implementation of Splitter integration.

1. In the View page, add the Splitter helper and configure the elements within the split pane. The first pane has the TreeView content and the next one has some content that is related to TreeView.


{% highlight CSHTML %}

@{IDictionary<string, object> htmlAttribute = new Dictionary<string, object>();
  htmlAttribute.Add("class", "_child");}@{Html.EJ().Splitter("outterSplitter").PaneProperties(p =>    {
  p.Add().ContentTemplate(
  @<div class="cont">
  <h3 class="h3">
  ASP.NET MVC
  </h3>
  @Html.EJ().TreeView("treeview").Items(items =>
  {
      items.Add().Text("Mobile").Expanded(true).Children(child =>
	  {                        
	       child.Add().Id("tools").Text("Galaxy").HtmlAttributes(htmlAttribute);
		   });
		   items.Add().Text("Harddisk").Expanded(true).Children(child =>
		   { 
      		   child.Add().Id("chart").Text("Segate").HtmlAttributes(htmlAttribute);
		    });
		   items.Add().Text("Logo").Expanded(true).Children(child =>
		   {
			   child.Add().Id("grid").Text("Amazon").HtmlAttributes(htmlAttribute);
           });
  }).ClientSideEvents(e=>e.NodeSelect("treeClicked"))
</div>).PaneSize("200");
p.Add().ContentTemplate(
@<div class="cont">
<div class="_content">
Select any product from the tree to show the description.
</div>
<div class="tools des">
<h3>
Tools 
</h3> 
<p>
Essential Tools is an collection of user interface components used to create interactive
ASP.NET MVC applications.
</p>
</div>
<div class="chart des">
<h3> 
Chart 
</h3> 
<p> Essential Chart is a business-oriented charting component.</p> 
</div> 
<div class="grid des"> 
<h3>
Grid
</h3>
<p>
Essential MVC Grid offers full featured a Grid control with extensive support for
Grouping and the display of hierarchical data.
</p>
</div>
</div>).PaneSize("200");
}).Height("400").Width("100%").Render();}<style type="text/css">
#outterSplitter {
margin: 0 auto;
}    .cont #treeView_Container {
margin-bottom: 0;
border: none;
}
.h3, ._content, p {
font-size: 14px;
margin-top: 10px;
text-indent: 10px;
} 
.des {
display: none;
}
</style>



<script type="text/javascript">
	function treeClicked(sender, args) 
	{
	if (sender.currentElement.hasClass('_child'))
		{
			//nodeSelect event handle
			var content = $('.' + sender.currentElement[0].id).html();
			$('._content').html(content);
		}
	}
</script>

{% endhighlight %}



When the node is selected in TreeView, the integrated output is displayed in the second pane.



![](Splitter-Integration_images/Splitter-Integration_img1.png)





![](Splitter-Integration_images/Splitter-Integration_img2.png)



