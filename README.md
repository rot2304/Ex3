# דו"ח מסכם- עבודה 3
קריאת קובץ הנתונים ויצירת רשת הנתונים:
```{r}
ga.data <- read.csv("./R/Work2/ga_edgelist.csv", header=TRUE) 
g <- graph.data.frame(ga.data, directed=FALSE) 
summary(g) 
g$layout <- layout.fruchterman.reingold(g) 
plot(g) 

```
![](https://cloud.githubusercontent.com/assets/17852872/14914180/b5b6d1ac-0e10-11e6-9b10-de7a409ed1f4.png)

##מדדי מרכזיות גבוהים:
###	i.	Betweeness:

```{r}
nameMaxBtwe = which((betweenness(g))==max(betweenness(g)))
V(g)[ nameMaxBtwe]$name
[1] "sloan"
btwe <- betweenness(g)
max(btwe)
[1] 115.3667
```

