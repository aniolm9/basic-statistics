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
