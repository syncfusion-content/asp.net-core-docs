---
layout: post
title: Selection with Grid widget for Syncfusion Essential ASP.NET Core
description: How to enable selection and its functionalities
platform: ASP.NET Core
control: Grid
documentation: ug
---
# Selection

Selection provides an interactive support to highlight the row, cell or column that you select. Selection can be done through simple Mouse down or Keyboard interaction. To enable selection, set `AllowSelection` as `true`. 

## Types of Selection

There are two types of selections available in grid. They are

1. Single 
2. Multiple 

### Single Selection

Single selection is an interactive support to select a specific row, cell or column in grid by mouse or keyboard interactions. To enable single selection by setting `SelectionType` property as `Single` and also set `AllowSelection` property as `true`.

### Multiple Selections

Multiple selections is an interactive support to select a group of rows, cells or columns in grid by mouse or keyboard interactions. To enable multiple selections by set `SelectionType`  property as `Multiple` and also set `AllowSelection` property as `true`.

## Row Selection

Row selection is enabled by set `SelectionMode` property of `SelectionSettings` as `Row`. For random row selection, press **"Ctrl + mouse left"** click and for continuous row selection press **"Shift + mouse left"** click on the grid rows. To unselect selected rows, by press **"Ctrl + mouse left"** click on selected row.

The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %}

	  @{Html.EJ().Grid<OrdersView>("Selection")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .AllowSelection()
            .SelectionType(SelectionType.Multiple)
            .SelectionSettings(select => { select.SelectionMode(mode => { mode.AddMode(SelectionMode.Row); }); })            
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();   
	 	  	    col.Field("ShipCity").Add();
	 	        col.Field("ShipCountry").Add(); 
                col.Field("Freight").Add();    
            }).Render();
        }
{% endhighlight  %}
{% highlight c# %}
		
        namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public IActionResult Selection()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
              }
           }
         } 
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example

![](Selection_images/Selection_img1.png)

## Multiple Row Selection using Checkbox Column

Select multiple rows in grid by using Checkbox column and it can be enabled by set column `Type` as `checkbox`. It also provides the option to select/deselect all the rows in Grid using a checkbox in the corresponding column header.

If the `Field` property of Checkbox column is not defined, then it acts as a template column. So `Field` property is necessary to perform grid actions like sorting, editing, etc., for the corresponding Checkbox column.

The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %}

	  @{Html.EJ().Grid<OrdersView>("Selection")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .AllowSelection()          
            .Columns(col =>
            {
                col.Type("checkbox").Width(50).Add();
                col.Field("OrderID").IsPrimaryKey(true).Width(80).TextAlign(TextAlign.Right).Add();
                col.Field("CustomerID").HeaderText("Customer ID").Width(75).Add();
                col.Field("EmployeeID").HeaderText("Employee ID").Width(75).TextAlign(TextAlign.Right).Add();
                col.Field("Freight").HeaderText("Freight").Format("{0:C}").Width(75).TextAlign(TextAlign.Right).Add();  
            }).Render();
        }
{% endhighlight  %}
{% highlight c# %}
		
        namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public IActionResult Selection()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
              }
           }
         } 
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example

![](Selection_images/Selection_img12.png)

## Cell Selection

Cell selection is enabled by set `SelectionMode` property of `SelectionSettings` as `Cell`. For random cell selection, press **"Ctrl + mouse left"** click and for continuous cell selection, press **"Shift + mouse left"** click on the grid cells. To unselect selected cells, press **"Ctrl + mouse left"** on selected cell click.

The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %}

	  @{Html.EJ().Grid<OrdersView>("Selection")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .AllowSelection()
            .SelectionType(SelectionType.Multiple)
            .SelectionSettings(select => { select.SelectionMode(mode => { mode.AddMode(SelectionMode.Cell); }); })            
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();   
                col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add(); 
                col.Field("Freight").Add();    
            }).Render(); 
        }
{% endhighlight  %}
{% highlight c# %}
		
	     namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public IActionResult Selection()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
              }
           }
         }
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example

![](Selection_images/Selection_img2.png)

### Cell Selection Mode

There are two types of cell selection available in grid. They are

1. Continuous Selection
2. Box Selection

Box cell selection is to select multiple cells vertically based on the initial column index selection.  

The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %}

	  @{Html.EJ().Grid<OrdersView>("Selection")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .AllowSelection()
            .SelectionType(SelectionType.Multiple)
            .SelectionSettings(select => { select.SelectionMode(mode => { mode.AddMode(SelectionMode.Cell);}).CellSelectionMode(CellSelectionMode.Box); })           
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();   
	            col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add(); 
                col.Field("Freight").Add();    
            }).Render();
         }
{% endhighlight  %}
{% highlight c# %}
		
	    namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public IActionResult Selection()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
              }
            }
          }
{% endhighlight  %}
{% endtabs %}

 The following output is displayed as a result of the above code example

![](Selection_images/Selection_img3.png)


## Column Selection

Column selection can be enabled by setting `SelectionMode` property of `SelectionSettings` as `Column`. For random column selection, press **"Ctrl + mouse left click"** and for continuous column selection, press **"Shift + mouse left click"** on the top of the column header. To unselect selected columns, press **"Ctrl + mouse left click"** on top of the selected column header.

The following code example describes the above behavior.

{% tabs %} 
{% highlight razor %}

	  @{Html.EJ().Grid<OrdersView>("Selection")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .AllowSelection()
            .SelectionType(SelectionType.Multiple)
            .SelectionSettings(select => { select.SelectionMode(mode => { mode.AddMode(SelectionMode.Column); }); })           
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();   
	            col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add(); 
                col.Field("Freight").Add();    
            }).Render(); 
        }
{% endhighlight  %}
{% highlight c# %}
		
	    namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public IActionResult Selection()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
              }
          }
       }

{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example

![](Selection_images/Selection_img4.png)


## Touch options

While using grid in a touch device environment, there is an option for multi selection through single tap on the row and it will shows a popup with multi-selection symbol. Tap the icon to enable multi selection in a single tap.

The following code example describes the above behavior. 

{% tabs %} 
{% highlight razor %}

	  @{Html.EJ().Grid<OrdersView>("Selection")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .AllowSelection()
            .SelectionType(SelectionType.Multiple)           
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();   
	            col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add(); 
                col.Field("Freight").Add();    
            }).Render();
         }
{% endhighlight  %}
{% highlight c# %}
		
         namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public IActionResult Selection()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
              }
            }
          }
{% endhighlight  %}
{% endtabs %}

The following output is displayed as a result of the above code example.

![](Selection_images/Selection_img5.png)


## Toggle Selection

The Toggle selection allows to perform selection and unselection of the particular row, cell or column.  To enable toggle selection, set `EnableToggle` property of `SelectionSettings`  as `true`. If you click on the selected row, cell or column then it will be unselected and vice versa. 

N> If multi selection is enabled, then in first click on any selected row (without pressing Ctrl key), it will clear multi selection and in second click on the same row, it will be unselected. 

The following code example describes the above behavior. 

{% tabs %} 
{% highlight razor %}

	  @{Html.EJ().Grid<OrdersView>("Selection")
            .Datasource((IEnumerable<object>)ViewBag.datasource)
            .AllowPaging()
            .EnableRowHover(false)
            .SelectionSettings(select => { select.EnableToggle(true); })        
            .Columns(col =>
            {
                col.Field("OrderID").Add();
                col.Field("EmployeeID").Add();   
	            col.Field("ShipCity").Add();
                col.Field("ShipCountry").Add(); 
                col.Field("Freight").Add();    
            }).Render(); 
         }
{% endhighlight  %}
{% highlight c# %}
		
	    namespace MVCSampleBrowser.Controllers
     	 {
          public partial class GridController : Controller
          {
           public IActionResult Selection()
             {
                var DataSource = new NorthwindDataContext().OrdersViews.ToList();
                ViewBag.datasource = DataSource;
                return View();
              }
           }
         }
{% endhighlight  %}
{% endtabs %}  