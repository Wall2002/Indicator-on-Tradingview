# Indicator-on-Tradingview
EMA Cross Signal
// This Pine Script™ code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © Wall_Trading

//@version=5
indicator("EMA Cross Signal", overlay=true)

// Tham số cho EMA
emaShortLength = 9
emaLongLength = 55

// Tính toán EMA
emaShort = ta.ema(close, emaShortLength)
emaLong = ta.ema(close, emaLongLength)

// Điều kiện tín hiệu Buy và Sell
buySignal = ta.crossover(emaShort, emaLong)
sellSignal = ta.crossunder(emaShort, emaLong)

// Vẽ EMA
plot(emaShort, title="EMA 9", color=color.blue)
plot(emaLong, title="EMA 55", color=color.red)

// Vẽ các tín hiệu Buy và Sell trên biểu đồ
plotshape(series=buySignal, title="Buy Signal", location=location.belowbar, color=color.green, style=shape.labelup, text="🟢")
plotshape(series=sellSignal, title="Sell Signal", location=location.abovebar, color=color.red, style=shape.labeldown, text="🔴")
