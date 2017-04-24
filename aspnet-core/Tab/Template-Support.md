---
layout: post
title: Template Support | Tab  | ASP.NET Core | Syncfusion
description: template support
platform: aspnet-core
control: Tab 
documentation: ug
---

# Template Support

The Content template option provided in ASP.NET Core is used to specify the HTML elements inside the Tab control. We can use this option to load any HTML elements and showcase it in the Tab panels as per our requirement.

The following code block showcases how to use content template option in the Tab control.

{% highlight CSHTML %}

<div style="width: 650px">

	<ej-tab id="tabSample">
		<e-tab-items>
			<e-tab-item id="gardenfresh" text="GARDEN FRESH (Veg)">
				<e-content-template>
					<div>
						<img src="~/Content/accordion/garden-veggie.png" alt="garden-fresh" />
						<div class="ingredients">
							Rate    : $50
							<br />
							Ingredients : cheese, onions, green capsicums & tomatoes.
						</div>
					</div>
				</e-content-template>
			</e-tab-item>
			<e-tab-item id="cornandspinach" text="CORN & SPINACH (Veg)">
				<e-content-template>
					<div>
						<img src="~/Content/accordion/corn-and-spinach-05.png" alt="garden-fresh" />
						<div class="ingredients">
							Rate    : $70
							<br />
							Ingredients : cheese, sweet corn & green capsicums.
						</div>
					</div>
				</e-content-template>
			</e-tab-item>
			<e-tab-item id="chickendelite" text="CHICKEN DELITE (Non-veg)">
				<e-content-template>
					<div>
						<img src="~/Content/accordion/chicken-delite.png" alt="garden-fresh" />
						<div class="ingredients">
							Rate    : $100
							<br />
							Ingredients : cheese, chicken chunks, onions & pineapple chunks.
						</div>
					</div>
				</e-content-template>
			</e-tab-item>
		</e-tab-items>
	</ej-tab>

</div>

{% endhighlight %}

Output:

![](Template-Support_images/Template-Support_img1.png)

Tab control with template support
{:.caption}