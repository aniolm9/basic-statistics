# R notes
## Basic commands
### Create an object
```R
> a<-9
> a
[1] 9
```
### Show objects
```R
> objects()
[1] "a"
```
### Delete an object
```R
> rm(a)
```
### Create a function
```R
> f<-function(x){2*x}
> f(4)
[1] 8
```
### Edit an object
Opens the default editor.
```
fix(f)
```
### Exit R
```R
> q()
```

## Vectors
### Create a vector
All the values must have the same type.
```R
> x<-c(1,2,5)
> x
[1] 1 2 5
```
From a file:
```R
x<-scan("path/to/file")
```
### Vector mode and length
```R
> x<-c(1,2,5)
> mode(x)
[1] "numeric"
> length(x)
[1] 3
```

## Matrix
### Create a matrix
Setting the column number.
```R
> x<-matrix(c(2,8,33,19,22,16,6,4),ncol=4)
> x
     [,1] [,2] [,3] [,4]
[1,]    2   33   22    6
[2,]    8   19   16    4
```

Setting the row number.
```R
> x<-matrix(c(2,8,33,19,22,16,6,4),nrow=4)
> x
     [,1] [,2]
[1,]    2   22
[2,]    8   16
[3,]   33    6
[4,]   19    4
```

Setting both.
```R
> z<-matrix(x,nrow=2,ncol=2)
> z
     [,1] [,2]
[1,]    2   33
[2,]    8   19
```

From a file.
```R
A<-matrix(scan("path/to/file"),ncol=2)
```

R creates matrixes completing columns. But they can be created by rows with `byrow=T`.

### Combining vectors
By column.
```R
> x<-c(2,3,4)
> y<-c(5,6,7)
> z<-cbind(x,y)
> z
     x y
[1,] 2 5
[2,] 3 6
[3,] 4 7
```

By row.
```R
> x<-c(2,3,4)
> y<-c(5,6,7)
> z<-rbind(x,y)
> z
  [,1] [,2] [,3]
x    2    3    4
y    5    6    7
```
### Matrix dimension
```R
> dim(z)
[1] 2 3
```

### Name columns and rows
```R
> x<-matrix(c(2,8,33,19,22,16,5,4), ncol=4, dimnames=list(c("Persona 1", "Persona 2"), c("Germans", "Edat", "Pes", "Escolaritat")))
> x
          Germans Edat Pes Escolaritat
Persona 1       2   33  22           5
Persona 2       8   19  16           4
```

## Data frames
### Create a data frame
From a file.
```R
data<-read.table("path/to/file", header=T)
```
`header=T` means we want to import the first row of variable names.

## Graphics
### Function plot
To plot a continuous sine function.
```R
> x<-seq(-pi, pi, len=100)
> plot(x, sin(x), type="l")
```
`type="l"` is set to draw a continuous line instead of points.

### Pie diagram
```R
> data<-c(26,3,10,1)
> names<-c("Name 1", "Name 2", "Name 3", "Other")
> color<-c(2,3,4,5)
> pie(data, labels=names, col=color, main="Title")
```

To set the names you could also use:
```R
> data<-c(26,3,10,1)
> names(data)<-c("Name 1", "Name 2", "Name 3", "Other")
> color<-c(2,3,4,5)
> pie(data, col=color, main="Title")
```

### Bar diagram
It's pretty similar to the pie diagram, but to name each class the keyword is `names` instead of `labels`.
```R
> data<-c(26,3,10,1)
> names<-c("Name 1", "Name 2", "Name 3", "Other")
> color<-c(2,3,4,5)
> barplot(data, col=color, names=names, main="Title")
```
### Box diagram
```R
> boxplot(x1)
```

## Dispersion and central tendency measures
We will be using the next vector.
```R
> x1<-c(10.6,12.5,11.1,9.2,11.5,9.9,11.9,8.5,11.3,12.0,12.7,10.7,9.6,10.5,19.9)
> x1
 [1] 10.6 12.5 11.1  9.2 11.5  9.9 11.9  8.5 11.3 12.0 12.7 10.7  9.6 10.5 19.9
```
### Mean
```R
> mean(x1)
[1] 11.46
```
### Median
```R
> median(x1)
[1] 11.1
```
### Quantiles
```R
> quantile(x1)
   0%   25%   50%   75%  100%
 8.50 10.20 11.10 11.95 19.90
> quantile(x1,probs=0.33)
   33%
10.562
```
### Almost-variance and almost-standard deviation
It performs a `n-1` division instead of `n`.
```R
> var(x1)
[1] 6.892571
> sd(x1)
[1] 2.625371
```
### Summary
```R
> summary(x1)
   Min. 1st Qu.  Median    Mean 3rd Qu.    Max.
   8.50   10.20   11.10   11.46   11.95   19.90
```

## Probabilistic models
There are 4 basic functions to get the distribution function, the mass or the density function, the quantiles and random values from the model.

To get the value of F(x), where F is the distribution function of _distribu_.
```R
p<distribu>(x, params)
```

To get the value of f(x) (or p(x) in a discrete model):
```R
d<distribu>(x, params)
```

To get the p-quantile:
```R
q<distribu>(p, params)
```

To get _n_ random values from the model:
```R
r<distribu>(n, params)
```

Where _distribu_ is the type of distribution, for example `norm` for the normal distribution.