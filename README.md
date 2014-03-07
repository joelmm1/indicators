<script src="http://code.jquery.com/jquery-1.9.1.min.js"></script>
<script src="http://code.highcharts.com/highcharts.js"></script>
<script src="./bubble-dragAdrop.js"></script>

# Indicators - Highstock module

Go to project page to see this module in action: [http://blacklabel.github.io/indicators/](http://blacklabel.github.io/indicators/)


<div id="chart" style="height: 300px"></div>
<script>
$.getJSON('http://www.highcharts.com/samples/data/jsonp.php?filename=aapl-ohlcv.json&callback=?', function(data) {
    window.chart = new Highcharts.Chart('StockChart',{
        chart:{
            type: 'candlestick'
        },
        indicators: [{
            id: 'AAPL',
            type: 'sma',
            params: {
                period: 5,
            }
        }, {
            id: 'AAPL',
            type: 'ema',
            params: {
                period: 5,
                index: 0 //optional parameter for ohlc / candlestick / arearange - index of value
            },
            styles: {
                strokeWidth: 2,
                stroke: 'green',
                dashstyle: 'solid'
            }
        }, {
            id: 'AAPL',
            type: 'atr',
            params: {
                period: 14,
            },
            styles: {
                strokeWidth: 2,
                stroke: 'orange',
                dashstyle: 'solid'
            },
            yAxis: {
                lineWidth:2,
                title: {
                    text:'My ATR title'
                }
            }   
        }, {
            id: 'AAPL',
            type: 'rsi',
            params: {
                period: 14,
                overbought: 70,
                oversold: 30
            },
            styles: {
                strokeWidth: 2,
                stroke: 'black',
                dashstyle: 'solid'
            },
            yAxis: {
                lineWidth:2,
                title: {
                    text:'My RSI title'
                }
            }   
        }],
        tooltip:{
            enabledIndicators: true
        },
        series: [{
            cropThreshold: 0,
            id: 'AAPL',
            name: 'AAPL',
            data: data,
            tooltip: {
                valueDecimals: 2
            }
        }]
});
</script>

### Requirements

* Plugin requires the latest Highstock (tested with 1.3.9)

### Installation

* Like any other Highcharts module (e.g. exporting), add `<script>` tag pointing to `indicators.js` below Highcharts script tag.

### Code

The latest code is available on github: [https://github.com/blacklabel/indicators/](https://github.com/blacklabel/indicators/)

### Usage and demos
```
indicators: [{
            id: 'AAPL',
            type: 'sma',
            params: {
                period: 5,
            }
        }, {
            id: 'AAPL',
            type: 'ema',
            params: {
                period: 5,
                index: 0
            },
            styles: {
                strokeWidth: 2,
                stroke: 'green',
                dashstyle: 'solid'
            }
        }, {
            id: 'AAPL',
            type: 'atr',
            params: {
                period: 14,
            },
            styles: {
                strokeWidth: 2,
                stroke: 'orange',
                dashstyle: 'solid'
            },
            yAxis: {
                lineWidth:2,
                title: {
                    text:'My ATR title'
                }
            }   
        }, {
            id: 'AAPL',
            type: 'rsi',
            params: {
                period: 14,
                overbought: 70,
                oversold: 30
            },
            styles: {
                strokeWidth: 2,
                stroke: 'black',
                dashstyle: 'solid'
            },
            yAxis: {
                lineWidth:2,
                title: {
                    text:'My RSI title'
                }
            }   
}],
tooltip:{
    enabledIndicators: true
},
```

### Parameters
* id - id of series
* type - type of indicator (one of: 'sma', 'ema', 'atr', 'rsi')
* styles - color, dashstyle, width etc. for a indicator line
* yAxis (ATR/RSI) - yAxis object like in Highcharts, options for additional yAxis
* params - config options for indicator
* params.period (SMA/EMA/ATR/RSI) - base perdiod for indicator (it's number of points to be calculated). Defaults to 14.
* params.index (SMA/EMA) - y-value index. Useful when using candlestick/ohlc/range series to determine which value (open/high/low/close) should be used in indicator. Defaults to 0.
* params.overbought (RSI) - overbought value between 0-100. Defaults to 70.
* params.oversold (RSI) - oversold value between 0-100. Defaults to 30.
* tooltip.enabledIndicators - true/false, show indicators in tooltip. Disabled by default.


### Demo

Demos are available at project's github page: [http://blacklabel.github.io/indicators/](http://blacklabel.github.io/indicators/)