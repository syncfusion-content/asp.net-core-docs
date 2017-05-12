---
layout: post
title: Technical Indicators| Chart  | ASP.NET Core | Syncfusion
description: What are the different types of technical indicators supported in Essential Chart for financial analysis.
platform: aspnet-core
control: Chart
documentation: ug
---

# Technical Indicators

EjChart control supports 10 types of technical indicators. 

## Bind data to render the indicator

You can bind the series **DataSource** to the indicator by setting the specific series name to the indicator by using the *Indicators.SeriesName* property.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series x-name="XDate" high="High" low="Low"open="Open" close="Close" name="Hilo" datasource="ViewBag.ChartData">
        </e-series>
    </e-chart-series>
    <e-indicators>
        <e-indicator series-name="Hilo"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

{% highlight csharp %}

           //// Create dataSource to chart
            List<ChartData> data = new List<ChartData>();
            data.Add(new ChartData("2010/7/1", 38, 10, 58, 27));
            data.Add(new ChartData("2010/7/8", 28, 15, 48, 58));
            data.Add(new ChartData("2010/7/9", 54, 35, 85, 98));
            data.Add(new ChartData("2010/7/10", 52, 21, 38, 85));
            ///...
            ViewBag.ChartData = data;

{% endhighlight %}

Also, you can add data to the indicator directly by using the DataSource option of the indicator.  

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-indicators>
        <e-indicator x-name="XDate" high="High" low="Low"open="Open" close="Close" datasource="ViewBag.ChartData"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}
	
## Indicator Types

### Accumulation Distribution

To create an Accumulation Distribution indicator, set the *Indicators.Type* as **AccumulationDistribution**. Accumulation Distribution require **Volume** field additionally with the DataSource to calculate the signal line.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        <e-series x-name="XDate" high="High" low="Low"open="Open" close="Close" volume="Volume" name="Hilo" datasource="ViewBag.ChartData">
        </e-series>
    </e-chart-series>
    <e-indicators>
        <e-indicator type="AccumulationDistribution" series-name="Hilo"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img1.png)


### Average True Range (ATR)

You can create an ATR indicator by setting the Indicators.Type as **ATR** in the Indicators. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        //...
    </e-chart-series>
    <e-indicators>
        <e-indicator type="ATR"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img2.png)


### Bollinger Band 

Bollinger Band indicator is created by setting the Indicators.Type as **BollingerBand**. It contains three lines, namely upper band, lower band and signal line. Bollinger Band default value of the *Period* is 14 and *StandardDeviations* is 2.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        //...
    </e-chart-series>
    <e-indicators>
        <e-indicator type="BollingerBand"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img3.png)


### Exponential Moving Average (EMA)

To render an EMA indicator, you have to set the Indicators.Type as **EMA**.  

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        //...
    </e-chart-series>
    <e-indicators>
        <e-indicator type="EMA"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img4.png)

### Momentum 

Momentum Technical indicator is created by setting the Indicators.Type as **Momentum**. The momentum indicator renders two lines, namely upper band and signal line. Upper band always rendered at the value 100 and the signal line is calculated based on the momentum of the data.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        //...
    </e-chart-series>
    <e-indicators>
        <e-indicator type="Momentum"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img5.png)

### Moving Average Convergence Divergence (MACD)

To render an MACD indicator, you have to set the Indicators.Type as **MACD**.  MACD indicator contains MACD line, Signal line and Histogram column. Histogram is used to differentiate MACD and signal line.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        //...
    </e-chart-series>
    <e-indicators>
        <e-indicator type="MACD"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img6.png)

#### MacdType

By using the **MacdType** enumeration property, you can change the MACD rendering as *Line*, *Histogram* or *Both*. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        //...
    </e-chart-series>
    <e-indicators>
        <e-indicator type="MACD" macd-type="Histogram"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img7.png)

### Relative Strength Index (RSI)

To render the RSI indicator, set the Indicators.Type as **RSI**. It contains three lines, namely upper band, lower band and signal line. Upper and lower band always render at value 70 and 30 respectively and signal line is calculated based on the *RSI* formula.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        //...
    </e-chart-series>
    <e-indicators>
        <e-indicator type="RSI"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img8.png)

### Simple Moving Average (SMA)

To render the SMA indicator, you should specify the Indicators.Type as **SMA**.  

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        //...
    </e-chart-series>
    <e-indicators>
        <e-indicator type="SMA"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img9.png)


### Stochastic 

For the Stochastic indicator, you need to set the Indicators.Type as **Stochastic**. The Stochastic indicator renders four lines namely, upper line, lower line, stochastic line and the signal line. Upper line always rendered at value 80 and the lower line is rendered at value 20. Stochastic and Signal Lines are calculated based on the stochastic formula.

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        //...
    </e-chart-series>
    <e-indicators>
        <e-indicator type="Stochastic"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img10.png)

### Triangular Moving Average (TMA)

To render the TMA indicator, you should specify the Indicators.Type as **TMA**. 

{% highlight cshtml %}

<ej-chart id="chartContainer">
    // ...
    <e-chart-series>
        //...
    </e-chart-series>
    <e-indicators>
        <e-indicator type="TMA"></e-indicator>
    </e-indicators>
    // ...
</ej-chart>

{% endhighlight %}

![](Technical-Indicators_images/Technical-Indicators_img11.png)