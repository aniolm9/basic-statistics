# Basic R notes
#### Create an object
```R
> a<-9
> a
[1] 9
```
#### Show objects
```R
> objects()
[1] "a"
```
#### Delete an object
```R
> rm(a)
```
#### Create a function
```R
> f<-function(x){2*x}
> f(4)
[1] 8
```
#### Edit an object
Opens the default editor.
```
fix(f)
```
#### Exit R
```R
> q()
```

## Vectors
#### Create a vector
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
#### Vector mode and length
```R
> x<-c(1,2,5)
> mode(x)
[1] "numeric"
> length(x)
[1] 3
```

## Matrix
#### Create a matrix
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

#### Combining vectors
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
#### Matrix dimension
```R
> dim(z)
[1] 2 3
```

#### Name columns and rows
```R
> x<-matrix(c(2,8,33,19,22,16,5,4), ncol=4, dimnames=list(c("Persona 1", "Persona 2"), c("Germans", "Edat", "Pes", "Escolaritat")))
> x
          Germans Edat Pes Escolaritat
Persona 1       2   33  22           5
Persona 2       8   19  16           4
```

## Data frames
#### Create a data frame
From a file.
```R
data<-read.table("path/to/file", header=T)
```
`header=T` means we want to import the first row of variable names.

## Graphics
To plot a continuous sine function.
```R
> x<-seq(-pi, pi, len=100)
> plot(x, sin(x), type="l")
```
`type="l"` is set to draw a continuous line instead of points.