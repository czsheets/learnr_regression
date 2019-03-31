```{r}
setwd("~/Regression_text")
library(readr)
height_weight <- read_csv("height_weight.csv") 
plot(height_weight, xlab = 'Height M', ylab = 'Weight kg', pch = 19, col = 'royalblue')
```

```{r}
cor(height_weight$`Height M`, height_weight$`Weight kg`)
cor.test(height_weight$`Height M`, height_weight$`Weight kg`)$p.value
```


Used this [function](https://stats.stackexchange.com/questions/83172/generate-two-variables-with-precise-pre-specified-correlation)

```{r}
library('MASS')
cor_sim <- function(r = 1.0){
  samples = 200
  data = mvrnorm(n=samples, mu=c(0, 0), Sigma=matrix(c(1, r, r, 1), nrow=2), empirical=TRUE)
  x = data[, 1]  # standard normal (mu=0, sd=1)
  y = data[, 2]  # standard normal (mu=0, sd=1)
  plot(x,y, main = paste('Correlation =',round(r,2)), pch = 19, col = 'royalblue')
}
```

```{r}
cor_sim(1.0)
```

```{r}
cor_sim(0.8)
```

```{r}
cor_sim(.6)
```

```{r}
cor_sim(0)
```

```{r}
cor_sim(-1.0)
```

```{r}
cor_sim(-.8)
```

```{r}
cor_sim(-.6)
```

```{r}
x = rnorm(20)
y = x^2 + rnorm(20)/10
cor(x,y)
plot(x,y)
abline(lm(y~x))
#lines(x,predict(lm(y~x + x^2)), col = 'red', lty = 3)
```
