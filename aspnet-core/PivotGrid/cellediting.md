---
layout: post
title: Cell Editing
platform: aspnet-core
control: PivotGrid
documentation: ug
---

# Cell editing

I> This feature is applicable only for the relational data source.

Cell editing allows you to edit and alter the values in the pivot grid. The summary values will be recreated based on the edited values. By selecting multiple cells (like in cell selection feature), you can edit multiple cells at the same time.
  
You can enable the cell editing option in the pivot grid by setting the `enable-cell-editing` property to true.

{% highlight CSHTML %}

<ej-pivot-grid id="PivotGrid1" enable-cell-editing="true"></ej-pivot-grid>

{% endhighlight %}

![](Cell-Editing_images/celleditingclient.png)


