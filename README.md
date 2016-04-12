# דו"ח מסכם- עבודה 3
קריאת קובץ הנתונים ויצירת רשת הנתונים:
```{r}
ga.data <- read.csv("./R/Work2/ga_edgelist.csv", header=TRUE) 
g <- graph.data.frame(ga.data, directed=FALSE) 
summary(g) 
g$layout <- layout.fruchterman.reingold(g) 
plot(g) 

```


