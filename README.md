# דו"ח מסכם- עבודה 3

##חלק 1:
קריאת קובץ הנתונים ויצירת רשת הנתונים:
```{r}
ga.data <- read.csv("./R/Work2/ga_edgelist.csv", header=TRUE) 
g <- graph.data.frame(ga.data, directed=FALSE) 
summary(g) 
g$layout <- layout.fruchterman.reingold(g) 
plot(g) 

```
![](https://cloud.githubusercontent.com/assets/17852872/14914180/b5b6d1ac-0e10-11e6-9b10-de7a409ed1f4.png)


##a.מדדי מרכזיות גבוהים:
###	i.	Betweeness:

```{r}
nameMaxBtwe = which((betweenness(g))==max(betweenness(g)))
V(g)[ nameMaxBtwe]$name
[1] "sloan"
btwe <- betweenness(g)
max(btwe)
[1] 115.3667
```

###	ii.	Closeness:

```{r}
nameMaxCls = which((closeness(g))==max(closeness (g)))
V(g)[ nameMaxCls]$name
[1] "torres"
 cls <- closeness(g)
max(cls)
[1] 0.003194888
```


###	iii.	Eigencetor

```{r}
maxEv = which(max(evcent(g)$vector)==(evcent(g)$vector))
V(g)[maxEv]$name
[1] "karev"
max(evcent(g)$vector)
[1] 1
```
##b. אלגוריתמים לזיהוי קהילות:

###	Grivan-Newman algorithm
i.	
```{r}
com <- edge.betweenness.community(g, directed=F)
V(g)$color=com$membership
 plot(g)
```
![](https://cloud.githubusercontent.com/assets/17852872/14914178/b5b3820e-0e10-11e6-8996-445169942bf2.png)

ii+iii:
```{r}
com
IGRAPH clustering edge betweenness, groups: 7, mod: 0.58
table(clusters(g2)$membership)

table(com$membership)

1 2 3 4 5 6 7 
8 5 4 4 5 3 3 
```
* ניתן לראות שישנן סה"כ 7 קהילות. בקבילה מספר 1 8 אנשים, בקהילה מספר 2 חמישה וכך הלאה..
* כמו כן, הערך שהתקבל, כפי שניתן לראות הוא 0.58

###	Fast-Greedy algorithm:
i.	
```{r}
com <- fastgreedy.community(g)
V(g)$color=com$membership
plot(g)
```
![](https://cloud.githubusercontent.com/assets/17852872/14914179/b5b3375e-0e10-11e6-839c-a7d330e8275b.png)

ii+iii:
```{r}
com
IGRAPH clustering fast greedy, groups: 6, mod: 0.59


table(com$membership)
1  2  3  4  5  6 
10  5  4  5  5  3 
```
* ישנן סה"כ 6 קהילות וניתן לראות כמה אנשים יש בכל קהילה
* כמו כן, ערך הmodularity שהתקבל הוא 0.59


##חלק 2:
קריאת קובץ הנתונים ויצירת רשת הנתונים:
```{r}
g<-read.graph("./R/Work2/football.gml",format=c("gml"))
summary(g) 
g$layout <- layout.fruchterman.reingold(g) 
plot(g)
```
![](https://cloud.githubusercontent.com/assets/17852872/14914177/b5ad9894-0e10-11e6-93fc-e62ac46b0eb7.png)


##a.מדדי מרכזיות גבוהים:
###	i.	Betweeness:

```{r}
nameMaxBtwe = which((betweenness(g))==max(betweenness(g)))
V(g)[ nameMaxBtwe]$name
[1] "sloan"
btwe <- betweenness(g)
max(btwe)
[1] 115.3667
```

###	ii.	Closeness:

```{r}
nameMaxCls = which((closeness(g))==max(closeness (g)))
V(g)[ nameMaxCls]$name
[1] "torres"
 cls <- closeness(g)
max(cls)
[1] 0.003194888
```


###	iii.	Eigencetor

```{r}
maxEv = which(max(evcent(g)$vector)==(evcent(g)$vector))
V(g)[maxEv]$name
[1] "karev"
max(evcent(g)$vector)
[1] 1
```
