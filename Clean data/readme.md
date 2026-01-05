# Measures and DAX

This file contains the measures and DAX expressions used in the project. Each measure is shown with a descriptive heading and the DAX code in a fenced block.

## GROWTH SCORE
Description: Score based on 7-day percentage change.

```dax
GROWTH SCORE =
VAR g = SELECTEDVALUE(crypto[price_change_percentage_7d_in_currency], 0)
RETURN
SWITCH(
    TRUE(),
    ISBLANK(g), 0,
    g >= 30, 20,
    g >= 15, 15,
    g >= 5, 10,
    g >= 0, 5,
    g < 0, 1
)
```

## GROWTH MOMENTUM
Description: Momentum comparing weekly and daily percentage changes.

```dax
GROWTH MOMENTUM =
VAR weekly = SELECTEDVALUE(crypto[price_change_percentage_7d_in_currency])
VAR daily  = SELECTEDVALUE(crypto[price_change_percentage_24h_in_currency])
RETURN
IF(
    ISBLANK(weekly) || ISBLANK(daily),
    BLANK(),
    DIVIDE(weekly - daily, ABS(daily))
)
```

## Expected return 7d
Description: Expected price after 7 days based on 7-day percentage change.

```dax
Expected return 7d =
VAR price    = SELECTEDVALUE(crypto[current_price])
VAR change7d = SELECTEDVALUE(crypto[price_change_percentage_7d_in_currency], 0)
RETURN
price * (1 + change7d / 100)
```
