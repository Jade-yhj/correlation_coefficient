## Correlation Coefficient 
### 1. Introduction & Function
Correlation coefficients are used in statistics to measure how strong a relationship is between two variables, which in our case is, how strong a relationship is between two stocks. 

Correlation coefficient formulas are used to find how strong a relationship is between data. The formulas return a value between -1 and 1, where:

1 indicates a strong positive relationship.

-1 indicates a strong negative relationship.

A result of zero indicates no relationship at all.

![](image/Correlation.png)

There are several types of correlation coefficient formulas.

One of the most commonly used formulas in stats is Pearson’s correlation coefficient formula. 

![](image/Correlation_Coefficient_Formula.png)

### 2. Pinescript Tutorial
#### · Initial Setting 

```
//@version=4
study("Correlation Coefficient", overlay = false)
```

#### · Parameter Setting 

```
period = input(title = "period", type=input.integer, defval=240)            // Set the number of bars back
ticker = input(title="Symbol", type = input.symbol, defval= "NASDAQ:AAPL")  // Get the other stock's name that we want to compare
ticker_price_data = security(ticker, "D", close)                            // Get the close price of the other stock
cc = correlation(ticker_price_data, close, period)                          // Calculate Correlation Coefficient

```

#### · Plotting 
```
plot(cc, color = cc > 0 ? color.green : color.red)
hline(0, color = color.gray, linestyle = hline.style_solid, linewidth = 1)
hline(0.75, color = color.gray, linestyle = hline.style_dashed, linewidth = 1)
hline(-0.75, color = color.gray, linestyle = hline.style_dashed, linewidth = 1)
```
