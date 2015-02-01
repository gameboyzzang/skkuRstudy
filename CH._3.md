# CH. 3

벡터를 생성하는 c()함수


```r
metallica <- c('Lars','James','Jason','Kirk')
metallica
```

```
## [1] "Lars"  "James" "Jason" "Kirk"
```

벡터에서 특정 값 빼기


```r
metallica <- metallica[metallica != 'Jason']
metallica
```

```
## [1] "Lars"  "James" "Kirk"
```

벡터에 특정 값 추가


```r
metallica <- c(metallica, 'Rob')
metallica
```

```
## [1] "Lars"  "James" "Kirk"  "Rob"
```

R의 기본 내장 데이터들 불러오는 함수


```r
data()
```

기본 내장 데이타는 테이터 이름만 입력해도 볼수 있음


```r
trees
```

```
##    Girth Height Volume
## 1    8.3     70   10.3
## 2    8.6     65   10.3
## 3    8.8     63   10.2
## 4   10.5     72   16.4
## 5   10.7     81   18.8
## 6   10.8     83   19.7
## 7   11.0     66   15.6
## 8   11.0     75   18.2
## 9   11.1     80   22.6
## 10  11.2     75   19.9
## 11  11.3     79   24.2
## 12  11.4     76   21.0
## 13  11.4     76   21.4
## 14  11.7     69   21.3
## 15  12.0     75   19.1
## 16  12.9     74   22.2
## 17  12.9     85   33.8
## 18  13.3     86   27.4
## 19  13.7     71   25.7
## 20  13.8     64   24.9
## 21  14.0     78   34.5
## 22  14.2     80   31.7
## 23  14.5     74   36.3
## 24  16.0     72   38.3
## 25  16.3     77   42.6
## 26  17.3     81   55.4
## 27  17.5     82   55.7
## 28  17.9     80   58.3
## 29  18.0     80   51.5
## 30  18.0     80   51.0
## 31  20.6     87   77.0
```

setwd()로 설정한 현재 작업공간(Working Directory)이 어디인지 알아보는 getwd()함수


```r
getwd()
```

```
## [1] "C:/Users/Yoo/Documents/GitHub/skkuRstudy"
```

함수에 대한 도움말 문서를 불러오는 함수와 예제를 불러오는 함수


```r
#help(함수이름)
help(sum)
```

```
## starting httpd help server ... done
```

```r
#example(함수이름)
example(mean)
```

```
## 
## mean> x <- c(0:10, 50)
## 
## mean> xm <- mean(x)
## 
## mean> c(xm, mean(x, trim = 0.10))
## [1] 8.75 5.50
```

패키지설치: install.packages()함수 사용, ex: install.packages('패키지이름')

설치한 패키지 사용:library()함수 사용,  ex: library('ggplot2')

파일 불러오기

.csv(엑셀)파일 불러오기: read.csv(),  ex: read.csv('c:/users/Yoo/Documents/abc.csv', header=True) 
*header=True는 데이터의 첫번째 열이 변수명일때, 변수명이 아니라면 header=False로 해야됨.
*setwd()로 설정한 현재 작업공간에 데이터 파일이 있으면, 파일명만 입력해도 됨
예: setwd("c:/users/Yoo/Documents")       
    read.csv("abc.csv")

.spss파일 불러오기: read.spss 
*이 함수는 library(foreign)을 입력해서 foreign 패키지를 사용하는 상태에서만 쓸 수 있음.

.txt와 .dat파일 불러오기: read.delim()


그냥 library()를 입력할 경우, 설치된 패키지들 보여줌


```r
library()
```

metallica라는 dataframe생성, data.frame()함수 사용 


```r
metallicaNames <- c('Lars','James','Kirk','Rob')
metallicaAges <- c(47, 47, 48, 46)

#방금 위에서 생성한 metallicaNames와 metallicaAges 이 두 벡터를
#data.frame함수를 사용하여 metallica라는 데이터프레임으로 만듬
metallica <- data.frame(Name=metallicaNames, Age=metallicaAges) 
#metallica는 Name과 Age라는 두개의 변수를 가지는 데이타 프레임
metallica
```

```
##    Name Age
## 1  Lars  47
## 2 James  47
## 3  Kirk  48
## 4   Rob  46
```

metallica 데이터 프레임 내 각각의 변수 확인


```r
metallica$Name
```

```
## [1] Lars  James Kirk  Rob  
## Levels: James Kirk Lars Rob
```

```r
metallica$Age
```

```
## [1] 47 47 48 46
```

metallica에 Childage라는 변수 추가


```r
metallica$Childage <- c(12, 12, 4, 6)
metallica
```

```
##    Name Age Childage
## 1  Lars  47       12
## 2 James  47       12
## 3  Kirk  48        4
## 4   Rob  46        6
```

데이터 프레임내 변수명 확인, names()함수 사용


```r
names(metallica)
```

```
## [1] "Name"     "Age"      "Childage"
```

리스트 생성은 list()함수 사용 


```r
metallicalist <- list(metallicaNames, metallicaAges)
metallicalist
```

```
## [[1]]
## [1] "Lars"  "James" "Kirk"  "Rob"  
## 
## [[2]]
## [1] 47 47 48 46
```

각각의 변수들을 열로 묶어서 matrix를 만들때는 cbind()함수


```r
metallicamatrix <- cbind(metallicaNames, metallicaAges)
metallicamatrix
```

```
##      metallicaNames metallicaAges
## [1,] "Lars"         "47"         
## [2,] "James"        "47"         
## [3,] "Kirk"         "48"         
## [4,] "Rob"          "46"
```

자료 내의 변수들을 조작하여 새변수 생성도 가능함.

Age변수에서 Childage변수를 빼서 아빠가 된 나이인 Fatherhoodage 변수 생성.


```r
metallica$Fatherhoodage <- metallica$Age - metallica$Childage
metallica
```

```
##    Name Age Childage Fatherhoodage
## 1  Lars  47       12            35
## 2 James  47       12            35
## 3  Kirk  48        4            44
## 4   Rob  46        6            40
```

날짜를 변수 값으로 입력할 땐 as.Date()함수 사용


```r
birth_date<-as.Date(c("1977-07-03","1969-05-24","1973-06-21","1970-07-16","1949-10-10","1983-11-05","1987-10-08","1989-09-16","1973-05-20","1984-11-12"))
```

as.Date로 날짜를 입력할 경우, 날짜끼리 차이가 얼마나 나는지도 계산가능


```r
husband<-as.Date(c("1973-06-21","1970-07-16","1949-10-08","1969-05-24"))
wife<-as.Date(c("1984-11-12","1973-08-02","1948-11-11","1983-07-23"))
agegap<-husband-wife
agegap
```

```
## Time differences in days
## [1] -4162 -1113   331 -5173
```

동일한 값을 입력할때는 반복해주는 rep()함수 사용


```r
job<-c(rep(1,5),rep(2,5)) #job<-c(1,1,1,1,1,2,2,2,2,2)와 동일
job
```

```
##  [1] 1 1 1 1 1 2 2 2 2 2
```

명목척도를 만들 때에는 factor()함수 또는 gl()함수 사용


```r
job <-gl(2,5,labels=c("Lecturer","Student"))
#또는 job <-factor(job , levels = c(1:2) , labels = c("Lecturer" , "Student"))
job
```

```
##  [1] Lecturer Lecturer Lecturer Lecturer Lecturer Student  Student 
##  [8] Student  Student  Student 
## Levels: Lecturer Student
```

