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

1. 파일 불러오기

.csv(엑셀)파일 불러오기: read.csv(),  
ex: read.csv('c:/users/Yoo/Documents/abc.csv', header=True) 

*header=True는 데이터의 첫번째 열이 변수명일때, 변수명이 아니라면 header=False로 해야됨.

*setwd()로 설정한 현재 작업공간에 데이터 파일이 있으면, 파일명만 입력해도 됨
예: setwd("c:/users/Yoo/Documents")       
    read.csv("abc.csv")


.spss파일 불러오기: read.spss() 
*이 함수는 library(foreign)을 입력해서 foreign 패키지를 사용하는 상태에서만 쓸 수 있음.


.txt와 .dat파일 불러오기: read.delim()



2. 파일 저장하기


write.table(metallica,"Metallica Data.txt",sep="\t",row.names=FALSE) 
*sep="\t"는 데이터 값들을 탭으로 구분


write.table(metallica,"Metallica Data.txt",sep=",",row.names=FALSE) 
*sep = ","는 데이터 값들을 콤마로 구분




그냥 library()를 입력할 경우, 설치된 패키지들 보여줌


```r
library()
```


*패키지들에서 함수 이름이 겹치는 경우:

다른  패키지에  이름이 같은 함수가 있어 이럴 경우, 어떤 패키지에 있는 함수를 쓸 것인지 지정해 주어야 한다.
패키지 car와 Hmisc에는 recode()라는 동일한 이름의 함수가 존재한다.
따라서 car와 Hmisc를 동시에 불러왔을 때, 

car에 있는 recode()함수를 쓸경우에는

car:: recode()

Hmisc패키지에 있는 recode()함수를 쓸 때는

Hmisc:: recode() 

이런식으로 사용해야 한다.





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
birth_date <- as.Date(c("1977-07-03","1969-05-24","1973-06-21","1970-07-16","1949-10-10","1983-11-05","1987-10-08","1989-09-16","1973-05-20","1984-11-12"))
```

as.Date로 날짜를 입력할 경우, 날짜끼리 차이가 얼마나 나는지도 계산가능


```r
husband <- as.Date(c("1973-06-21","1970-07-16","1949-10-08","1969-05-24"))
wife <- as.Date(c("1984-11-12","1973-08-02","1948-11-11","1983-07-23"))
agegap <- husband-wife
agegap
```

```
## Time differences in days
## [1] -4162 -1113   331 -5173
```

동일한 값을 입력할 때는 반복해주는 rep()함수 사용


```r
job <- c(rep(1,5),rep(2,5)) #job<-c(1,1,1,1,1,2,2,2,2,2)와 동일
job
```

```
##  [1] 1 1 1 1 1 2 2 2 2 2
```

명목척도를 만들 때에는 factor()함수 또는 gl()함수 사용


```r
job <- gl(2,5,labels=c("Lecturer","Student"))
#또는 job <-factor(job , levels = c(1:2) , labels = c("Lecturer" , "Student"))
job
```

```
##  [1] Lecturer Lecturer Lecturer Lecturer Lecturer Student  Student 
##  [8] Student  Student  Student 
## Levels: Lecturer Student
```

데이타 프레임 다루기

데이타 프레임 만들기

```r
name<-c("Ben","Martin","Andy","Paul","Graham","carina","Karina","Doug","Mark","Zoe")
friends <- c(5,2,0,4,1,10,12,15,12,17)
alcohol <- c(10,15,20,5,30,25,20,16,17,18)
income <- c(20000,40000,35000,22000,50000,5000,100,3000,10000,10)
neurotic <- c(10,17,14,13,21,7,13,9,14,13)
lecturerData <- data.frame(name, birth_date, job, friends, alcohol, income, neurotic)
lecturerData
```

```
##      name birth_date      job friends alcohol income neurotic
## 1     Ben 1977-07-03 Lecturer       5      10  20000       10
## 2  Martin 1969-05-24 Lecturer       2      15  40000       17
## 3    Andy 1973-06-21 Lecturer       0      20  35000       14
## 4    Paul 1970-07-16 Lecturer       4       5  22000       13
## 5  Graham 1949-10-10 Lecturer       1      30  50000       21
## 6  carina 1983-11-05  Student      10      25   5000        7
## 7  Karina 1987-10-08  Student      12      20    100       13
## 8    Doug 1989-09-16  Student      15      16   3000        9
## 9    Mark 1973-05-20  Student      12      17  10000       14
## 10    Zoe 1984-11-12  Student      17      18     10       13
```

데이타의 결측값은 NA로 입력

```r
neurotic<-c(10,17,NA,13,21,7,13,9,14,NA)
```

데이타프레임에서  특정부분만 가져오기

특정 조건의 열만 가져올 때: 데이타프레임이름[,열]

```r
lecturerpersonality <- lecturerData[,c("friends","alcohol","neurotic")] #[,열]
lecturerpersonality
```

```
##    friends alcohol neurotic
## 1        5      10       10
## 2        2      15       17
## 3        0      20       14
## 4        4       5       13
## 5        1      30       21
## 6       10      25        7
## 7       12      20       13
## 8       15      16        9
## 9       12      17       14
## 10      17      18       13
```

특정 조건의 행만 가져올 때: 데이타프레임이름[행,]

```r
lectureronly <- lecturerData[job =="Lecturer",] #[,열]
lectureronly
```

```
##     name birth_date      job friends alcohol income neurotic
## 1    Ben 1977-07-03 Lecturer       5      10  20000       10
## 2 Martin 1969-05-24 Lecturer       2      15  40000       17
## 3   Andy 1973-06-21 Lecturer       0      20  35000       14
## 4   Paul 1970-07-16 Lecturer       4       5  22000       13
## 5 Graham 1949-10-10 Lecturer       1      30  50000       21
```

특정 조건의 행과 열을 가져올 때: 데이타프레임이름[행,열]

```r
alcoholpersonality <- lecturerData[alcohol>10, c("friends","alcohol","neurotic")] #[행,열]
alcoholpersonality
```

```
##    friends alcohol neurotic
## 2        2      15       17
## 3        0      20       14
## 5        1      30       21
## 6       10      25        7
## 7       12      20       13
## 8       15      16        9
## 9       12      17       14
## 10      17      18       13
```

데이타프레임의 부분집합 추출: subset()함수 사용

```r
lectureonly <- subset(lecturerData, job =="Lecturer") #특정 조건만
lectureonly
```

```
##     name birth_date      job friends alcohol income neurotic
## 1    Ben 1977-07-03 Lecturer       5      10  20000       10
## 2 Martin 1969-05-24 Lecturer       2      15  40000       17
## 3   Andy 1973-06-21 Lecturer       0      20  35000       14
## 4   Paul 1970-07-16 Lecturer       4       5  22000       13
## 5 Graham 1949-10-10 Lecturer       1      30  50000       21
```

특정 조건에서 특정 변수만

```r
alcoholicpersonality <- subset(lecturerData, alcohol > 10, select = c("friends","alcohol","neurotic"))
alcoholicpersonality
```

```
##    friends alcohol neurotic
## 2        2      15       17
## 3        0      20       14
## 5        1      30       21
## 6       10      25        7
## 7       12      20       13
## 8       15      16        9
## 9       12      17       14
## 10      17      18       13
```

매트릭스로 빼낼수도 있음

```r
alcoholpersonalityMatirix <- as.matrix(lecturerData[ alcohol > 10, c("friends","alcohol","neurotic")])
```

또는 이미 빼낸 subset을 매트릭스로 변환

```r
alcoholpersonalitymatirix <- as.matrix(alcoholicpersonality)
```

*as.Date(), as.matrix(), as.factor() 등등 as.데이타형식() 함수는 데이타의 형식을 바꿔주는 기능을 함.

데이타 수정하기

여러 변수들을 하나로 합칠때: reshape 패키지의 stack()함수 사용

```r
satisfactionData <- read.delim('Honeymoon Period.dat', header = TRUE)
satisfactionData
```

```
##     Person Satisfaction_Base Satisfaction_6_Months Satisfaction_12_Months
## 1        1                 6                     6                      5
## 2        2                 7                     7                      8
## 3        3                 4                     6                      2
## 4        4                 6                     9                      4
## 5        5                 6                     7                      6
## 6        6                 5                    10                      4
## 7        7                 6                     6                      4
## 8        8                 2                     5                      4
## 9        9                10                     9                      5
## 10      10                10                    10                     10
## 11      11                 8                     8                     10
## 12      12                 6                    10                      9
## 13      13                 7                     8                      9
## 14      14                 6                     7                      9
## 15      15                 9                    10                      8
## 16      16                10                    10                      8
## 17      17                 1                     2                      1
## 18      18                 5                     6                      7
## 19      19                 6                    10                     10
## 20      20                 5                     6                     NA
## 21      21                 3                     7                      5
## 22      22                 3                     4                      4
## 23      23                 7                     6                      4
## 24      24                 3                     4                      2
## 25      28                 9                    10                      8
## 26      29                 8                    10                      9
## 27      30                 8                     7                      7
## 28      31                 7                     7                      6
## 29      32                10                     8                     NA
## 30      33                 7                     6                      5
## 31      34                 5                     7                      7
## 32      38                 5                     7                      4
## 33      39                 7                     9                      7
## 34      40                 4                     5                      5
## 35      41                 3                     4                      3
## 36      44                 4                     6                      7
## 37      45                 8                     5                      4
## 38      46                10                     4                      4
## 39      47                10                    10                      8
## 40      48                 4                     5                      4
## 41      49                 2                     4                      1
## 42      50                10                    10                      9
## 43      51                 2                     4                      4
## 44      52                 9                    10                      8
## 45      53                 9                    10                      8
## 46      54                 4                     4                      3
## 47      55                 6                    10                      6
## 48      56                 9                     9                      5
## 49      57                 6                     6                      7
## 50      58                 5                     4                      5
## 51      59                 8                     8                      9
## 52      60                 5                     6                      7
## 53      61                 7                    10                     10
## 54      62                 8                     9                      8
## 55      63                 8                     9                      7
## 56      64                 4                     5                      4
## 57      65                10                     8                      9
## 58      66                 6                     9                      8
## 59      67                 7                     9                      7
## 60      68                 3                     3                      3
## 61      69                 8                     9                     10
## 62      70                 3                     3                      4
## 63      71                 8                    10                      7
## 64      72                10                     7                      5
## 65      73                10                    10                      9
## 66      74                 5                     6                      4
## 67      75                10                    10                      6
## 68      76                10                     9                      7
## 69      77                 5                     7                      4
## 70      78                 3                     5                      3
## 71      79                10                     9                      8
## 72      80                 5                    10                      6
## 73      81                 5                     6                      9
## 74      82                 9                     6                      7
## 75      83                 5                     5                      4
## 76      84                 8                     6                      2
## 77      85                10                     9                      6
## 78      86                 7                     7                      6
## 79      87                 8                     7                      9
## 80      88                10                     9                      7
## 81      89                 7                     6                      6
## 82      90                 5                     4                      4
## 83      91                10                     8                      9
## 84      92                 7                     6                      7
## 85      93                10                     7                      9
## 86      94                10                    10                      8
## 87      95                 7                     9                      5
## 88      96                 3                     3                      4
## 89      97                10                    10                      5
## 90      98                 6                     7                      4
## 91      99                 6                     5                      4
## 92     100                 8                     9                      7
## 93     101                 6                     8                      9
## 94     102                 7                     8                      5
## 95     103                 9                     8                      7
## 96     104                 7                     8                      4
## 97     105                10                    10                      8
## 98     106                10                     4                      2
## 99     107                 8                     8                      4
## 100    108                 3                     4                      4
## 101    109                 7                     6                      6
## 102    110                 9                     7                      8
## 103    111                 7                     8                      7
## 104    112                 5                     3                      4
## 105    113                 7                     4                      5
## 106    114                 3                     2                      1
## 107    115                 5                     5                      3
## 108    116                 7                     9                      5
## 109    117                 7                     6                      6
## 110    118                 3                     4                      4
## 111    119                 8                     4                      2
## 112    120                 3                     6                      1
## 113    121                 6                     6                      6
## 114    122                 5                    10                      2
## 115    123                 5                     6                      2
##     Satisfaction_18_Months Gender
## 1                        2      0
## 2                        4      1
## 3                        2      1
## 4                        1      0
## 5                        6      0
## 6                        2      1
## 7                        2      0
## 8                       NA      0
## 9                        6      0
## 10                       9      0
## 11                       9      0
## 12                       9      0
## 13                       6      1
## 14                       5      0
## 15                       6      1
## 16                       6      1
## 17                      NA      1
## 18                       3      0
## 19                       6      1
## 20                      NA      0
## 21                       6      0
## 22                       2      1
## 23                       2      0
## 24                      NA      0
## 25                      NA      1
## 26                       7      1
## 27                       3      0
## 28                       3      0
## 29                      NA      0
## 30                       3      1
## 31                       4      0
## 32                       4      0
## 33                       6      0
## 34                       1      0
## 35                       1      1
## 36                       3      1
## 37                       3      1
## 38                       5      0
## 39                       6      0
## 40                       1      1
## 41                      NA      0
## 42                       7      1
## 43                       1      0
## 44                       5      1
## 45                       5      1
## 46                       3      1
## 47                       2      0
## 48                       4      1
## 49                       9      1
## 50                       1      0
## 51                       4      1
## 52                       1      1
## 53                       4      0
## 54                       8      1
## 55                       4      1
## 56                       3      0
## 57                       4      0
## 58                       7      1
## 59                       6      0
## 60                      NA      0
## 61                       8      0
## 62                       3      1
## 63                       5      1
## 64                       3      1
## 65                       6      0
## 66                       1      0
## 67                      NA      0
## 68                       7      0
## 69                       2      0
## 70                      NA      0
## 71                      NA      1
## 72                       5      0
## 73                       4      0
## 74                       4      0
## 75                       1      1
## 76                       2      1
## 77                      NA      1
## 78                       3      1
## 79                       4      0
## 80                       7      0
## 81                       3      0
## 82                       2      1
## 83                       5      1
## 84                       4      0
## 85                       7      0
## 86                       7      1
## 87                       5      1
## 88                       8      0
## 89                      NA      1
## 90                       1      0
## 91                      NA      1
## 92                       2      1
## 93                       3      0
## 94                      NA      1
## 95                       6      1
## 96                       3      1
## 97                       4      0
## 98                      NA      0
## 99                       5      1
## 100                      3      1
## 101                      3      0
## 102                      6      0
## 103                      8      0
## 104                     NA      1
## 105                      3      0
## 106                     NA      1
## 107                     NA      1
## 108                      2      1
## 109                      4      1
## 110                      1      1
## 111                      1      1
## 112                      7      1
## 113                      7      1
## 114                     NA      1
## 115                      1      0
```

```r
#데이타를 콘솔창 말고 데이타 창으로 보고싶을 땐 View(satisfactionData)
```


```r
library(reshape)
satisfactionStacked <- stack(satisfactionData, select = c("Satisfaction_Base","Satisfaction_6_Months",
                                                          "Satisfaction_12_Months","Satisfaction_18_Months"))
satisfactionStacked
```

```
##     values                    ind
## 1        6      Satisfaction_Base
## 2        7      Satisfaction_Base
## 3        4      Satisfaction_Base
## 4        6      Satisfaction_Base
## 5        6      Satisfaction_Base
## 6        5      Satisfaction_Base
## 7        6      Satisfaction_Base
## 8        2      Satisfaction_Base
## 9       10      Satisfaction_Base
## 10      10      Satisfaction_Base
## 11       8      Satisfaction_Base
## 12       6      Satisfaction_Base
## 13       7      Satisfaction_Base
## 14       6      Satisfaction_Base
## 15       9      Satisfaction_Base
## 16      10      Satisfaction_Base
## 17       1      Satisfaction_Base
## 18       5      Satisfaction_Base
## 19       6      Satisfaction_Base
## 20       5      Satisfaction_Base
## 21       3      Satisfaction_Base
## 22       3      Satisfaction_Base
## 23       7      Satisfaction_Base
## 24       3      Satisfaction_Base
## 25       9      Satisfaction_Base
## 26       8      Satisfaction_Base
## 27       8      Satisfaction_Base
## 28       7      Satisfaction_Base
## 29      10      Satisfaction_Base
## 30       7      Satisfaction_Base
## 31       5      Satisfaction_Base
## 32       5      Satisfaction_Base
## 33       7      Satisfaction_Base
## 34       4      Satisfaction_Base
## 35       3      Satisfaction_Base
## 36       4      Satisfaction_Base
## 37       8      Satisfaction_Base
## 38      10      Satisfaction_Base
## 39      10      Satisfaction_Base
## 40       4      Satisfaction_Base
## 41       2      Satisfaction_Base
## 42      10      Satisfaction_Base
## 43       2      Satisfaction_Base
## 44       9      Satisfaction_Base
## 45       9      Satisfaction_Base
## 46       4      Satisfaction_Base
## 47       6      Satisfaction_Base
## 48       9      Satisfaction_Base
## 49       6      Satisfaction_Base
## 50       5      Satisfaction_Base
## 51       8      Satisfaction_Base
## 52       5      Satisfaction_Base
## 53       7      Satisfaction_Base
## 54       8      Satisfaction_Base
## 55       8      Satisfaction_Base
## 56       4      Satisfaction_Base
## 57      10      Satisfaction_Base
## 58       6      Satisfaction_Base
## 59       7      Satisfaction_Base
## 60       3      Satisfaction_Base
## 61       8      Satisfaction_Base
## 62       3      Satisfaction_Base
## 63       8      Satisfaction_Base
## 64      10      Satisfaction_Base
## 65      10      Satisfaction_Base
## 66       5      Satisfaction_Base
## 67      10      Satisfaction_Base
## 68      10      Satisfaction_Base
## 69       5      Satisfaction_Base
## 70       3      Satisfaction_Base
## 71      10      Satisfaction_Base
## 72       5      Satisfaction_Base
## 73       5      Satisfaction_Base
## 74       9      Satisfaction_Base
## 75       5      Satisfaction_Base
## 76       8      Satisfaction_Base
## 77      10      Satisfaction_Base
## 78       7      Satisfaction_Base
## 79       8      Satisfaction_Base
## 80      10      Satisfaction_Base
## 81       7      Satisfaction_Base
## 82       5      Satisfaction_Base
## 83      10      Satisfaction_Base
## 84       7      Satisfaction_Base
## 85      10      Satisfaction_Base
## 86      10      Satisfaction_Base
## 87       7      Satisfaction_Base
## 88       3      Satisfaction_Base
## 89      10      Satisfaction_Base
## 90       6      Satisfaction_Base
## 91       6      Satisfaction_Base
## 92       8      Satisfaction_Base
## 93       6      Satisfaction_Base
## 94       7      Satisfaction_Base
## 95       9      Satisfaction_Base
## 96       7      Satisfaction_Base
## 97      10      Satisfaction_Base
## 98      10      Satisfaction_Base
## 99       8      Satisfaction_Base
## 100      3      Satisfaction_Base
## 101      7      Satisfaction_Base
## 102      9      Satisfaction_Base
## 103      7      Satisfaction_Base
## 104      5      Satisfaction_Base
## 105      7      Satisfaction_Base
## 106      3      Satisfaction_Base
## 107      5      Satisfaction_Base
## 108      7      Satisfaction_Base
## 109      7      Satisfaction_Base
## 110      3      Satisfaction_Base
## 111      8      Satisfaction_Base
## 112      3      Satisfaction_Base
## 113      6      Satisfaction_Base
## 114      5      Satisfaction_Base
## 115      5      Satisfaction_Base
## 116      6  Satisfaction_6_Months
## 117      7  Satisfaction_6_Months
## 118      6  Satisfaction_6_Months
## 119      9  Satisfaction_6_Months
## 120      7  Satisfaction_6_Months
## 121     10  Satisfaction_6_Months
## 122      6  Satisfaction_6_Months
## 123      5  Satisfaction_6_Months
## 124      9  Satisfaction_6_Months
## 125     10  Satisfaction_6_Months
## 126      8  Satisfaction_6_Months
## 127     10  Satisfaction_6_Months
## 128      8  Satisfaction_6_Months
## 129      7  Satisfaction_6_Months
## 130     10  Satisfaction_6_Months
## 131     10  Satisfaction_6_Months
## 132      2  Satisfaction_6_Months
## 133      6  Satisfaction_6_Months
## 134     10  Satisfaction_6_Months
## 135      6  Satisfaction_6_Months
## 136      7  Satisfaction_6_Months
## 137      4  Satisfaction_6_Months
## 138      6  Satisfaction_6_Months
## 139      4  Satisfaction_6_Months
## 140     10  Satisfaction_6_Months
## 141     10  Satisfaction_6_Months
## 142      7  Satisfaction_6_Months
## 143      7  Satisfaction_6_Months
## 144      8  Satisfaction_6_Months
## 145      6  Satisfaction_6_Months
## 146      7  Satisfaction_6_Months
## 147      7  Satisfaction_6_Months
## 148      9  Satisfaction_6_Months
## 149      5  Satisfaction_6_Months
## 150      4  Satisfaction_6_Months
## 151      6  Satisfaction_6_Months
## 152      5  Satisfaction_6_Months
## 153      4  Satisfaction_6_Months
## 154     10  Satisfaction_6_Months
## 155      5  Satisfaction_6_Months
## 156      4  Satisfaction_6_Months
## 157     10  Satisfaction_6_Months
## 158      4  Satisfaction_6_Months
## 159     10  Satisfaction_6_Months
## 160     10  Satisfaction_6_Months
## 161      4  Satisfaction_6_Months
## 162     10  Satisfaction_6_Months
## 163      9  Satisfaction_6_Months
## 164      6  Satisfaction_6_Months
## 165      4  Satisfaction_6_Months
## 166      8  Satisfaction_6_Months
## 167      6  Satisfaction_6_Months
## 168     10  Satisfaction_6_Months
## 169      9  Satisfaction_6_Months
## 170      9  Satisfaction_6_Months
## 171      5  Satisfaction_6_Months
## 172      8  Satisfaction_6_Months
## 173      9  Satisfaction_6_Months
## 174      9  Satisfaction_6_Months
## 175      3  Satisfaction_6_Months
## 176      9  Satisfaction_6_Months
## 177      3  Satisfaction_6_Months
## 178     10  Satisfaction_6_Months
## 179      7  Satisfaction_6_Months
## 180     10  Satisfaction_6_Months
## 181      6  Satisfaction_6_Months
## 182     10  Satisfaction_6_Months
## 183      9  Satisfaction_6_Months
## 184      7  Satisfaction_6_Months
## 185      5  Satisfaction_6_Months
## 186      9  Satisfaction_6_Months
## 187     10  Satisfaction_6_Months
## 188      6  Satisfaction_6_Months
## 189      6  Satisfaction_6_Months
## 190      5  Satisfaction_6_Months
## 191      6  Satisfaction_6_Months
## 192      9  Satisfaction_6_Months
## 193      7  Satisfaction_6_Months
## 194      7  Satisfaction_6_Months
## 195      9  Satisfaction_6_Months
## 196      6  Satisfaction_6_Months
## 197      4  Satisfaction_6_Months
## 198      8  Satisfaction_6_Months
## 199      6  Satisfaction_6_Months
## 200      7  Satisfaction_6_Months
## 201     10  Satisfaction_6_Months
## 202      9  Satisfaction_6_Months
## 203      3  Satisfaction_6_Months
## 204     10  Satisfaction_6_Months
## 205      7  Satisfaction_6_Months
## 206      5  Satisfaction_6_Months
## 207      9  Satisfaction_6_Months
## 208      8  Satisfaction_6_Months
## 209      8  Satisfaction_6_Months
## 210      8  Satisfaction_6_Months
## 211      8  Satisfaction_6_Months
## 212     10  Satisfaction_6_Months
## 213      4  Satisfaction_6_Months
## 214      8  Satisfaction_6_Months
## 215      4  Satisfaction_6_Months
## 216      6  Satisfaction_6_Months
## 217      7  Satisfaction_6_Months
## 218      8  Satisfaction_6_Months
## 219      3  Satisfaction_6_Months
## 220      4  Satisfaction_6_Months
## 221      2  Satisfaction_6_Months
## 222      5  Satisfaction_6_Months
## 223      9  Satisfaction_6_Months
## 224      6  Satisfaction_6_Months
## 225      4  Satisfaction_6_Months
## 226      4  Satisfaction_6_Months
## 227      6  Satisfaction_6_Months
## 228      6  Satisfaction_6_Months
## 229     10  Satisfaction_6_Months
## 230      6  Satisfaction_6_Months
## 231      5 Satisfaction_12_Months
## 232      8 Satisfaction_12_Months
## 233      2 Satisfaction_12_Months
## 234      4 Satisfaction_12_Months
## 235      6 Satisfaction_12_Months
## 236      4 Satisfaction_12_Months
## 237      4 Satisfaction_12_Months
## 238      4 Satisfaction_12_Months
## 239      5 Satisfaction_12_Months
## 240     10 Satisfaction_12_Months
## 241     10 Satisfaction_12_Months
## 242      9 Satisfaction_12_Months
## 243      9 Satisfaction_12_Months
## 244      9 Satisfaction_12_Months
## 245      8 Satisfaction_12_Months
## 246      8 Satisfaction_12_Months
## 247      1 Satisfaction_12_Months
## 248      7 Satisfaction_12_Months
## 249     10 Satisfaction_12_Months
## 250     NA Satisfaction_12_Months
## 251      5 Satisfaction_12_Months
## 252      4 Satisfaction_12_Months
## 253      4 Satisfaction_12_Months
## 254      2 Satisfaction_12_Months
## 255      8 Satisfaction_12_Months
## 256      9 Satisfaction_12_Months
## 257      7 Satisfaction_12_Months
## 258      6 Satisfaction_12_Months
## 259     NA Satisfaction_12_Months
## 260      5 Satisfaction_12_Months
## 261      7 Satisfaction_12_Months
## 262      4 Satisfaction_12_Months
## 263      7 Satisfaction_12_Months
## 264      5 Satisfaction_12_Months
## 265      3 Satisfaction_12_Months
## 266      7 Satisfaction_12_Months
## 267      4 Satisfaction_12_Months
## 268      4 Satisfaction_12_Months
## 269      8 Satisfaction_12_Months
## 270      4 Satisfaction_12_Months
## 271      1 Satisfaction_12_Months
## 272      9 Satisfaction_12_Months
## 273      4 Satisfaction_12_Months
## 274      8 Satisfaction_12_Months
## 275      8 Satisfaction_12_Months
## 276      3 Satisfaction_12_Months
## 277      6 Satisfaction_12_Months
## 278      5 Satisfaction_12_Months
## 279      7 Satisfaction_12_Months
## 280      5 Satisfaction_12_Months
## 281      9 Satisfaction_12_Months
## 282      7 Satisfaction_12_Months
## 283     10 Satisfaction_12_Months
## 284      8 Satisfaction_12_Months
## 285      7 Satisfaction_12_Months
## 286      4 Satisfaction_12_Months
## 287      9 Satisfaction_12_Months
## 288      8 Satisfaction_12_Months
## 289      7 Satisfaction_12_Months
## 290      3 Satisfaction_12_Months
## 291     10 Satisfaction_12_Months
## 292      4 Satisfaction_12_Months
## 293      7 Satisfaction_12_Months
## 294      5 Satisfaction_12_Months
## 295      9 Satisfaction_12_Months
## 296      4 Satisfaction_12_Months
## 297      6 Satisfaction_12_Months
## 298      7 Satisfaction_12_Months
## 299      4 Satisfaction_12_Months
## 300      3 Satisfaction_12_Months
## 301      8 Satisfaction_12_Months
## 302      6 Satisfaction_12_Months
## 303      9 Satisfaction_12_Months
## 304      7 Satisfaction_12_Months
## 305      4 Satisfaction_12_Months
## 306      2 Satisfaction_12_Months
## 307      6 Satisfaction_12_Months
## 308      6 Satisfaction_12_Months
## 309      9 Satisfaction_12_Months
## 310      7 Satisfaction_12_Months
## 311      6 Satisfaction_12_Months
## 312      4 Satisfaction_12_Months
## 313      9 Satisfaction_12_Months
## 314      7 Satisfaction_12_Months
## 315      9 Satisfaction_12_Months
## 316      8 Satisfaction_12_Months
## 317      5 Satisfaction_12_Months
## 318      4 Satisfaction_12_Months
## 319      5 Satisfaction_12_Months
## 320      4 Satisfaction_12_Months
## 321      4 Satisfaction_12_Months
## 322      7 Satisfaction_12_Months
## 323      9 Satisfaction_12_Months
## 324      5 Satisfaction_12_Months
## 325      7 Satisfaction_12_Months
## 326      4 Satisfaction_12_Months
## 327      8 Satisfaction_12_Months
## 328      2 Satisfaction_12_Months
## 329      4 Satisfaction_12_Months
## 330      4 Satisfaction_12_Months
## 331      6 Satisfaction_12_Months
## 332      8 Satisfaction_12_Months
## 333      7 Satisfaction_12_Months
## 334      4 Satisfaction_12_Months
## 335      5 Satisfaction_12_Months
## 336      1 Satisfaction_12_Months
## 337      3 Satisfaction_12_Months
## 338      5 Satisfaction_12_Months
## 339      6 Satisfaction_12_Months
## 340      4 Satisfaction_12_Months
## 341      2 Satisfaction_12_Months
## 342      1 Satisfaction_12_Months
## 343      6 Satisfaction_12_Months
## 344      2 Satisfaction_12_Months
## 345      2 Satisfaction_12_Months
## 346      2 Satisfaction_18_Months
## 347      4 Satisfaction_18_Months
## 348      2 Satisfaction_18_Months
## 349      1 Satisfaction_18_Months
## 350      6 Satisfaction_18_Months
## 351      2 Satisfaction_18_Months
## 352      2 Satisfaction_18_Months
## 353     NA Satisfaction_18_Months
## 354      6 Satisfaction_18_Months
## 355      9 Satisfaction_18_Months
## 356      9 Satisfaction_18_Months
## 357      9 Satisfaction_18_Months
## 358      6 Satisfaction_18_Months
## 359      5 Satisfaction_18_Months
## 360      6 Satisfaction_18_Months
## 361      6 Satisfaction_18_Months
## 362     NA Satisfaction_18_Months
## 363      3 Satisfaction_18_Months
## 364      6 Satisfaction_18_Months
## 365     NA Satisfaction_18_Months
## 366      6 Satisfaction_18_Months
## 367      2 Satisfaction_18_Months
## 368      2 Satisfaction_18_Months
## 369     NA Satisfaction_18_Months
## 370     NA Satisfaction_18_Months
## 371      7 Satisfaction_18_Months
## 372      3 Satisfaction_18_Months
## 373      3 Satisfaction_18_Months
## 374     NA Satisfaction_18_Months
## 375      3 Satisfaction_18_Months
## 376      4 Satisfaction_18_Months
## 377      4 Satisfaction_18_Months
## 378      6 Satisfaction_18_Months
## 379      1 Satisfaction_18_Months
## 380      1 Satisfaction_18_Months
## 381      3 Satisfaction_18_Months
## 382      3 Satisfaction_18_Months
## 383      5 Satisfaction_18_Months
## 384      6 Satisfaction_18_Months
## 385      1 Satisfaction_18_Months
## 386     NA Satisfaction_18_Months
## 387      7 Satisfaction_18_Months
## 388      1 Satisfaction_18_Months
## 389      5 Satisfaction_18_Months
## 390      5 Satisfaction_18_Months
## 391      3 Satisfaction_18_Months
## 392      2 Satisfaction_18_Months
## 393      4 Satisfaction_18_Months
## 394      9 Satisfaction_18_Months
## 395      1 Satisfaction_18_Months
## 396      4 Satisfaction_18_Months
## 397      1 Satisfaction_18_Months
## 398      4 Satisfaction_18_Months
## 399      8 Satisfaction_18_Months
## 400      4 Satisfaction_18_Months
## 401      3 Satisfaction_18_Months
## 402      4 Satisfaction_18_Months
## 403      7 Satisfaction_18_Months
## 404      6 Satisfaction_18_Months
## 405     NA Satisfaction_18_Months
## 406      8 Satisfaction_18_Months
## 407      3 Satisfaction_18_Months
## 408      5 Satisfaction_18_Months
## 409      3 Satisfaction_18_Months
## 410      6 Satisfaction_18_Months
## 411      1 Satisfaction_18_Months
## 412     NA Satisfaction_18_Months
## 413      7 Satisfaction_18_Months
## 414      2 Satisfaction_18_Months
## 415     NA Satisfaction_18_Months
## 416     NA Satisfaction_18_Months
## 417      5 Satisfaction_18_Months
## 418      4 Satisfaction_18_Months
## 419      4 Satisfaction_18_Months
## 420      1 Satisfaction_18_Months
## 421      2 Satisfaction_18_Months
## 422     NA Satisfaction_18_Months
## 423      3 Satisfaction_18_Months
## 424      4 Satisfaction_18_Months
## 425      7 Satisfaction_18_Months
## 426      3 Satisfaction_18_Months
## 427      2 Satisfaction_18_Months
## 428      5 Satisfaction_18_Months
## 429      4 Satisfaction_18_Months
## 430      7 Satisfaction_18_Months
## 431      7 Satisfaction_18_Months
## 432      5 Satisfaction_18_Months
## 433      8 Satisfaction_18_Months
## 434     NA Satisfaction_18_Months
## 435      1 Satisfaction_18_Months
## 436     NA Satisfaction_18_Months
## 437      2 Satisfaction_18_Months
## 438      3 Satisfaction_18_Months
## 439     NA Satisfaction_18_Months
## 440      6 Satisfaction_18_Months
## 441      3 Satisfaction_18_Months
## 442      4 Satisfaction_18_Months
## 443     NA Satisfaction_18_Months
## 444      5 Satisfaction_18_Months
## 445      3 Satisfaction_18_Months
## 446      3 Satisfaction_18_Months
## 447      6 Satisfaction_18_Months
## 448      8 Satisfaction_18_Months
## 449     NA Satisfaction_18_Months
## 450      3 Satisfaction_18_Months
## 451     NA Satisfaction_18_Months
## 452     NA Satisfaction_18_Months
## 453      2 Satisfaction_18_Months
## 454      4 Satisfaction_18_Months
## 455      1 Satisfaction_18_Months
## 456      1 Satisfaction_18_Months
## 457      7 Satisfaction_18_Months
## 458      7 Satisfaction_18_Months
## 459     NA Satisfaction_18_Months
## 460      1 Satisfaction_18_Months
```

합친 변수들을 다시 나누고 싶으면 unstack()함수 사용

```r
satisfactionUnstacked <- unstack(satisfactionStacked)
#또는  satisfactionUnstacked<-unstack(satisfactionStacked , values~ind)
satisfactionUnstacked
```

```
##     Satisfaction_12_Months Satisfaction_18_Months Satisfaction_6_Months
## 1                        5                      2                     6
## 2                        8                      4                     7
## 3                        2                      2                     6
## 4                        4                      1                     9
## 5                        6                      6                     7
## 6                        4                      2                    10
## 7                        4                      2                     6
## 8                        4                     NA                     5
## 9                        5                      6                     9
## 10                      10                      9                    10
## 11                      10                      9                     8
## 12                       9                      9                    10
## 13                       9                      6                     8
## 14                       9                      5                     7
## 15                       8                      6                    10
## 16                       8                      6                    10
## 17                       1                     NA                     2
## 18                       7                      3                     6
## 19                      10                      6                    10
## 20                      NA                     NA                     6
## 21                       5                      6                     7
## 22                       4                      2                     4
## 23                       4                      2                     6
## 24                       2                     NA                     4
## 25                       8                     NA                    10
## 26                       9                      7                    10
## 27                       7                      3                     7
## 28                       6                      3                     7
## 29                      NA                     NA                     8
## 30                       5                      3                     6
## 31                       7                      4                     7
## 32                       4                      4                     7
## 33                       7                      6                     9
## 34                       5                      1                     5
## 35                       3                      1                     4
## 36                       7                      3                     6
## 37                       4                      3                     5
## 38                       4                      5                     4
## 39                       8                      6                    10
## 40                       4                      1                     5
## 41                       1                     NA                     4
## 42                       9                      7                    10
## 43                       4                      1                     4
## 44                       8                      5                    10
## 45                       8                      5                    10
## 46                       3                      3                     4
## 47                       6                      2                    10
## 48                       5                      4                     9
## 49                       7                      9                     6
## 50                       5                      1                     4
## 51                       9                      4                     8
## 52                       7                      1                     6
## 53                      10                      4                    10
## 54                       8                      8                     9
## 55                       7                      4                     9
## 56                       4                      3                     5
## 57                       9                      4                     8
## 58                       8                      7                     9
## 59                       7                      6                     9
## 60                       3                     NA                     3
## 61                      10                      8                     9
## 62                       4                      3                     3
## 63                       7                      5                    10
## 64                       5                      3                     7
## 65                       9                      6                    10
## 66                       4                      1                     6
## 67                       6                     NA                    10
## 68                       7                      7                     9
## 69                       4                      2                     7
## 70                       3                     NA                     5
## 71                       8                     NA                     9
## 72                       6                      5                    10
## 73                       9                      4                     6
## 74                       7                      4                     6
## 75                       4                      1                     5
## 76                       2                      2                     6
## 77                       6                     NA                     9
## 78                       6                      3                     7
## 79                       9                      4                     7
## 80                       7                      7                     9
## 81                       6                      3                     6
## 82                       4                      2                     4
## 83                       9                      5                     8
## 84                       7                      4                     6
## 85                       9                      7                     7
## 86                       8                      7                    10
## 87                       5                      5                     9
## 88                       4                      8                     3
## 89                       5                     NA                    10
## 90                       4                      1                     7
## 91                       4                     NA                     5
## 92                       7                      2                     9
## 93                       9                      3                     8
## 94                       5                     NA                     8
## 95                       7                      6                     8
## 96                       4                      3                     8
## 97                       8                      4                    10
## 98                       2                     NA                     4
## 99                       4                      5                     8
## 100                      4                      3                     4
## 101                      6                      3                     6
## 102                      8                      6                     7
## 103                      7                      8                     8
## 104                      4                     NA                     3
## 105                      5                      3                     4
## 106                      1                     NA                     2
## 107                      3                     NA                     5
## 108                      5                      2                     9
## 109                      6                      4                     6
## 110                      4                      1                     4
## 111                      2                      1                     4
## 112                      1                      7                     6
## 113                      6                      7                     6
## 114                      2                     NA                    10
## 115                      2                      1                     6
##     Satisfaction_Base
## 1                   6
## 2                   7
## 3                   4
## 4                   6
## 5                   6
## 6                   5
## 7                   6
## 8                   2
## 9                  10
## 10                 10
## 11                  8
## 12                  6
## 13                  7
## 14                  6
## 15                  9
## 16                 10
## 17                  1
## 18                  5
## 19                  6
## 20                  5
## 21                  3
## 22                  3
## 23                  7
## 24                  3
## 25                  9
## 26                  8
## 27                  8
## 28                  7
## 29                 10
## 30                  7
## 31                  5
## 32                  5
## 33                  7
## 34                  4
## 35                  3
## 36                  4
## 37                  8
## 38                 10
## 39                 10
## 40                  4
## 41                  2
## 42                 10
## 43                  2
## 44                  9
## 45                  9
## 46                  4
## 47                  6
## 48                  9
## 49                  6
## 50                  5
## 51                  8
## 52                  5
## 53                  7
## 54                  8
## 55                  8
## 56                  4
## 57                 10
## 58                  6
## 59                  7
## 60                  3
## 61                  8
## 62                  3
## 63                  8
## 64                 10
## 65                 10
## 66                  5
## 67                 10
## 68                 10
## 69                  5
## 70                  3
## 71                 10
## 72                  5
## 73                  5
## 74                  9
## 75                  5
## 76                  8
## 77                 10
## 78                  7
## 79                  8
## 80                 10
## 81                  7
## 82                  5
## 83                 10
## 84                  7
## 85                 10
## 86                 10
## 87                  7
## 88                  3
## 89                 10
## 90                  6
## 91                  6
## 92                  8
## 93                  6
## 94                  7
## 95                  9
## 96                  7
## 97                 10
## 98                 10
## 99                  8
## 100                 3
## 101                 7
## 102                 9
## 103                 7
## 104                 5
## 105                 7
## 106                 3
## 107                 5
## 108                 7
## 109                 7
## 110                 3
## 111                 8
## 112                 3
## 113                 6
## 114                 5
## 115                 5
```

좀더 정교하게 변수를 합치고 싶다면 melt()함수 사용

```r
restructuredData <- melt(satisfactionData, id = c("Person" , "Gender"), measured = c("Satisfaction_Base",
                                                                                     "Satisfaction_6_Months", "Satisfaction_12_Months", "Satisfaction_18_Months"))
restructuredData
```

```
##     Person Gender               variable value
## 1        1      0      Satisfaction_Base     6
## 2        2      1      Satisfaction_Base     7
## 3        3      1      Satisfaction_Base     4
## 4        4      0      Satisfaction_Base     6
## 5        5      0      Satisfaction_Base     6
## 6        6      1      Satisfaction_Base     5
## 7        7      0      Satisfaction_Base     6
## 8        8      0      Satisfaction_Base     2
## 9        9      0      Satisfaction_Base    10
## 10      10      0      Satisfaction_Base    10
## 11      11      0      Satisfaction_Base     8
## 12      12      0      Satisfaction_Base     6
## 13      13      1      Satisfaction_Base     7
## 14      14      0      Satisfaction_Base     6
## 15      15      1      Satisfaction_Base     9
## 16      16      1      Satisfaction_Base    10
## 17      17      1      Satisfaction_Base     1
## 18      18      0      Satisfaction_Base     5
## 19      19      1      Satisfaction_Base     6
## 20      20      0      Satisfaction_Base     5
## 21      21      0      Satisfaction_Base     3
## 22      22      1      Satisfaction_Base     3
## 23      23      0      Satisfaction_Base     7
## 24      24      0      Satisfaction_Base     3
## 25      28      1      Satisfaction_Base     9
## 26      29      1      Satisfaction_Base     8
## 27      30      0      Satisfaction_Base     8
## 28      31      0      Satisfaction_Base     7
## 29      32      0      Satisfaction_Base    10
## 30      33      1      Satisfaction_Base     7
## 31      34      0      Satisfaction_Base     5
## 32      38      0      Satisfaction_Base     5
## 33      39      0      Satisfaction_Base     7
## 34      40      0      Satisfaction_Base     4
## 35      41      1      Satisfaction_Base     3
## 36      44      1      Satisfaction_Base     4
## 37      45      1      Satisfaction_Base     8
## 38      46      0      Satisfaction_Base    10
## 39      47      0      Satisfaction_Base    10
## 40      48      1      Satisfaction_Base     4
## 41      49      0      Satisfaction_Base     2
## 42      50      1      Satisfaction_Base    10
## 43      51      0      Satisfaction_Base     2
## 44      52      1      Satisfaction_Base     9
## 45      53      1      Satisfaction_Base     9
## 46      54      1      Satisfaction_Base     4
## 47      55      0      Satisfaction_Base     6
## 48      56      1      Satisfaction_Base     9
## 49      57      1      Satisfaction_Base     6
## 50      58      0      Satisfaction_Base     5
## 51      59      1      Satisfaction_Base     8
## 52      60      1      Satisfaction_Base     5
## 53      61      0      Satisfaction_Base     7
## 54      62      1      Satisfaction_Base     8
## 55      63      1      Satisfaction_Base     8
## 56      64      0      Satisfaction_Base     4
## 57      65      0      Satisfaction_Base    10
## 58      66      1      Satisfaction_Base     6
## 59      67      0      Satisfaction_Base     7
## 60      68      0      Satisfaction_Base     3
## 61      69      0      Satisfaction_Base     8
## 62      70      1      Satisfaction_Base     3
## 63      71      1      Satisfaction_Base     8
## 64      72      1      Satisfaction_Base    10
## 65      73      0      Satisfaction_Base    10
## 66      74      0      Satisfaction_Base     5
## 67      75      0      Satisfaction_Base    10
## 68      76      0      Satisfaction_Base    10
## 69      77      0      Satisfaction_Base     5
## 70      78      0      Satisfaction_Base     3
## 71      79      1      Satisfaction_Base    10
## 72      80      0      Satisfaction_Base     5
## 73      81      0      Satisfaction_Base     5
## 74      82      0      Satisfaction_Base     9
## 75      83      1      Satisfaction_Base     5
## 76      84      1      Satisfaction_Base     8
## 77      85      1      Satisfaction_Base    10
## 78      86      1      Satisfaction_Base     7
## 79      87      0      Satisfaction_Base     8
## 80      88      0      Satisfaction_Base    10
## 81      89      0      Satisfaction_Base     7
## 82      90      1      Satisfaction_Base     5
## 83      91      1      Satisfaction_Base    10
## 84      92      0      Satisfaction_Base     7
## 85      93      0      Satisfaction_Base    10
## 86      94      1      Satisfaction_Base    10
## 87      95      1      Satisfaction_Base     7
## 88      96      0      Satisfaction_Base     3
## 89      97      1      Satisfaction_Base    10
## 90      98      0      Satisfaction_Base     6
## 91      99      1      Satisfaction_Base     6
## 92     100      1      Satisfaction_Base     8
## 93     101      0      Satisfaction_Base     6
## 94     102      1      Satisfaction_Base     7
## 95     103      1      Satisfaction_Base     9
## 96     104      1      Satisfaction_Base     7
## 97     105      0      Satisfaction_Base    10
## 98     106      0      Satisfaction_Base    10
## 99     107      1      Satisfaction_Base     8
## 100    108      1      Satisfaction_Base     3
## 101    109      0      Satisfaction_Base     7
## 102    110      0      Satisfaction_Base     9
## 103    111      0      Satisfaction_Base     7
## 104    112      1      Satisfaction_Base     5
## 105    113      0      Satisfaction_Base     7
## 106    114      1      Satisfaction_Base     3
## 107    115      1      Satisfaction_Base     5
## 108    116      1      Satisfaction_Base     7
## 109    117      1      Satisfaction_Base     7
## 110    118      1      Satisfaction_Base     3
## 111    119      1      Satisfaction_Base     8
## 112    120      1      Satisfaction_Base     3
## 113    121      1      Satisfaction_Base     6
## 114    122      1      Satisfaction_Base     5
## 115    123      0      Satisfaction_Base     5
## 116      1      0  Satisfaction_6_Months     6
## 117      2      1  Satisfaction_6_Months     7
## 118      3      1  Satisfaction_6_Months     6
## 119      4      0  Satisfaction_6_Months     9
## 120      5      0  Satisfaction_6_Months     7
## 121      6      1  Satisfaction_6_Months    10
## 122      7      0  Satisfaction_6_Months     6
## 123      8      0  Satisfaction_6_Months     5
## 124      9      0  Satisfaction_6_Months     9
## 125     10      0  Satisfaction_6_Months    10
## 126     11      0  Satisfaction_6_Months     8
## 127     12      0  Satisfaction_6_Months    10
## 128     13      1  Satisfaction_6_Months     8
## 129     14      0  Satisfaction_6_Months     7
## 130     15      1  Satisfaction_6_Months    10
## 131     16      1  Satisfaction_6_Months    10
## 132     17      1  Satisfaction_6_Months     2
## 133     18      0  Satisfaction_6_Months     6
## 134     19      1  Satisfaction_6_Months    10
## 135     20      0  Satisfaction_6_Months     6
## 136     21      0  Satisfaction_6_Months     7
## 137     22      1  Satisfaction_6_Months     4
## 138     23      0  Satisfaction_6_Months     6
## 139     24      0  Satisfaction_6_Months     4
## 140     28      1  Satisfaction_6_Months    10
## 141     29      1  Satisfaction_6_Months    10
## 142     30      0  Satisfaction_6_Months     7
## 143     31      0  Satisfaction_6_Months     7
## 144     32      0  Satisfaction_6_Months     8
## 145     33      1  Satisfaction_6_Months     6
## 146     34      0  Satisfaction_6_Months     7
## 147     38      0  Satisfaction_6_Months     7
## 148     39      0  Satisfaction_6_Months     9
## 149     40      0  Satisfaction_6_Months     5
## 150     41      1  Satisfaction_6_Months     4
## 151     44      1  Satisfaction_6_Months     6
## 152     45      1  Satisfaction_6_Months     5
## 153     46      0  Satisfaction_6_Months     4
## 154     47      0  Satisfaction_6_Months    10
## 155     48      1  Satisfaction_6_Months     5
## 156     49      0  Satisfaction_6_Months     4
## 157     50      1  Satisfaction_6_Months    10
## 158     51      0  Satisfaction_6_Months     4
## 159     52      1  Satisfaction_6_Months    10
## 160     53      1  Satisfaction_6_Months    10
## 161     54      1  Satisfaction_6_Months     4
## 162     55      0  Satisfaction_6_Months    10
## 163     56      1  Satisfaction_6_Months     9
## 164     57      1  Satisfaction_6_Months     6
## 165     58      0  Satisfaction_6_Months     4
## 166     59      1  Satisfaction_6_Months     8
## 167     60      1  Satisfaction_6_Months     6
## 168     61      0  Satisfaction_6_Months    10
## 169     62      1  Satisfaction_6_Months     9
## 170     63      1  Satisfaction_6_Months     9
## 171     64      0  Satisfaction_6_Months     5
## 172     65      0  Satisfaction_6_Months     8
## 173     66      1  Satisfaction_6_Months     9
## 174     67      0  Satisfaction_6_Months     9
## 175     68      0  Satisfaction_6_Months     3
## 176     69      0  Satisfaction_6_Months     9
## 177     70      1  Satisfaction_6_Months     3
## 178     71      1  Satisfaction_6_Months    10
## 179     72      1  Satisfaction_6_Months     7
## 180     73      0  Satisfaction_6_Months    10
## 181     74      0  Satisfaction_6_Months     6
## 182     75      0  Satisfaction_6_Months    10
## 183     76      0  Satisfaction_6_Months     9
## 184     77      0  Satisfaction_6_Months     7
## 185     78      0  Satisfaction_6_Months     5
## 186     79      1  Satisfaction_6_Months     9
## 187     80      0  Satisfaction_6_Months    10
## 188     81      0  Satisfaction_6_Months     6
## 189     82      0  Satisfaction_6_Months     6
## 190     83      1  Satisfaction_6_Months     5
## 191     84      1  Satisfaction_6_Months     6
## 192     85      1  Satisfaction_6_Months     9
## 193     86      1  Satisfaction_6_Months     7
## 194     87      0  Satisfaction_6_Months     7
## 195     88      0  Satisfaction_6_Months     9
## 196     89      0  Satisfaction_6_Months     6
## 197     90      1  Satisfaction_6_Months     4
## 198     91      1  Satisfaction_6_Months     8
## 199     92      0  Satisfaction_6_Months     6
## 200     93      0  Satisfaction_6_Months     7
## 201     94      1  Satisfaction_6_Months    10
## 202     95      1  Satisfaction_6_Months     9
## 203     96      0  Satisfaction_6_Months     3
## 204     97      1  Satisfaction_6_Months    10
## 205     98      0  Satisfaction_6_Months     7
## 206     99      1  Satisfaction_6_Months     5
## 207    100      1  Satisfaction_6_Months     9
## 208    101      0  Satisfaction_6_Months     8
## 209    102      1  Satisfaction_6_Months     8
## 210    103      1  Satisfaction_6_Months     8
## 211    104      1  Satisfaction_6_Months     8
## 212    105      0  Satisfaction_6_Months    10
## 213    106      0  Satisfaction_6_Months     4
## 214    107      1  Satisfaction_6_Months     8
## 215    108      1  Satisfaction_6_Months     4
## 216    109      0  Satisfaction_6_Months     6
## 217    110      0  Satisfaction_6_Months     7
## 218    111      0  Satisfaction_6_Months     8
## 219    112      1  Satisfaction_6_Months     3
## 220    113      0  Satisfaction_6_Months     4
## 221    114      1  Satisfaction_6_Months     2
## 222    115      1  Satisfaction_6_Months     5
## 223    116      1  Satisfaction_6_Months     9
## 224    117      1  Satisfaction_6_Months     6
## 225    118      1  Satisfaction_6_Months     4
## 226    119      1  Satisfaction_6_Months     4
## 227    120      1  Satisfaction_6_Months     6
## 228    121      1  Satisfaction_6_Months     6
## 229    122      1  Satisfaction_6_Months    10
## 230    123      0  Satisfaction_6_Months     6
## 231      1      0 Satisfaction_12_Months     5
## 232      2      1 Satisfaction_12_Months     8
## 233      3      1 Satisfaction_12_Months     2
## 234      4      0 Satisfaction_12_Months     4
## 235      5      0 Satisfaction_12_Months     6
## 236      6      1 Satisfaction_12_Months     4
## 237      7      0 Satisfaction_12_Months     4
## 238      8      0 Satisfaction_12_Months     4
## 239      9      0 Satisfaction_12_Months     5
## 240     10      0 Satisfaction_12_Months    10
## 241     11      0 Satisfaction_12_Months    10
## 242     12      0 Satisfaction_12_Months     9
## 243     13      1 Satisfaction_12_Months     9
## 244     14      0 Satisfaction_12_Months     9
## 245     15      1 Satisfaction_12_Months     8
## 246     16      1 Satisfaction_12_Months     8
## 247     17      1 Satisfaction_12_Months     1
## 248     18      0 Satisfaction_12_Months     7
## 249     19      1 Satisfaction_12_Months    10
## 250     20      0 Satisfaction_12_Months    NA
## 251     21      0 Satisfaction_12_Months     5
## 252     22      1 Satisfaction_12_Months     4
## 253     23      0 Satisfaction_12_Months     4
## 254     24      0 Satisfaction_12_Months     2
## 255     28      1 Satisfaction_12_Months     8
## 256     29      1 Satisfaction_12_Months     9
## 257     30      0 Satisfaction_12_Months     7
## 258     31      0 Satisfaction_12_Months     6
## 259     32      0 Satisfaction_12_Months    NA
## 260     33      1 Satisfaction_12_Months     5
## 261     34      0 Satisfaction_12_Months     7
## 262     38      0 Satisfaction_12_Months     4
## 263     39      0 Satisfaction_12_Months     7
## 264     40      0 Satisfaction_12_Months     5
## 265     41      1 Satisfaction_12_Months     3
## 266     44      1 Satisfaction_12_Months     7
## 267     45      1 Satisfaction_12_Months     4
## 268     46      0 Satisfaction_12_Months     4
## 269     47      0 Satisfaction_12_Months     8
## 270     48      1 Satisfaction_12_Months     4
## 271     49      0 Satisfaction_12_Months     1
## 272     50      1 Satisfaction_12_Months     9
## 273     51      0 Satisfaction_12_Months     4
## 274     52      1 Satisfaction_12_Months     8
## 275     53      1 Satisfaction_12_Months     8
## 276     54      1 Satisfaction_12_Months     3
## 277     55      0 Satisfaction_12_Months     6
## 278     56      1 Satisfaction_12_Months     5
## 279     57      1 Satisfaction_12_Months     7
## 280     58      0 Satisfaction_12_Months     5
## 281     59      1 Satisfaction_12_Months     9
## 282     60      1 Satisfaction_12_Months     7
## 283     61      0 Satisfaction_12_Months    10
## 284     62      1 Satisfaction_12_Months     8
## 285     63      1 Satisfaction_12_Months     7
## 286     64      0 Satisfaction_12_Months     4
## 287     65      0 Satisfaction_12_Months     9
## 288     66      1 Satisfaction_12_Months     8
## 289     67      0 Satisfaction_12_Months     7
## 290     68      0 Satisfaction_12_Months     3
## 291     69      0 Satisfaction_12_Months    10
## 292     70      1 Satisfaction_12_Months     4
## 293     71      1 Satisfaction_12_Months     7
## 294     72      1 Satisfaction_12_Months     5
## 295     73      0 Satisfaction_12_Months     9
## 296     74      0 Satisfaction_12_Months     4
## 297     75      0 Satisfaction_12_Months     6
## 298     76      0 Satisfaction_12_Months     7
## 299     77      0 Satisfaction_12_Months     4
## 300     78      0 Satisfaction_12_Months     3
## 301     79      1 Satisfaction_12_Months     8
## 302     80      0 Satisfaction_12_Months     6
## 303     81      0 Satisfaction_12_Months     9
## 304     82      0 Satisfaction_12_Months     7
## 305     83      1 Satisfaction_12_Months     4
## 306     84      1 Satisfaction_12_Months     2
## 307     85      1 Satisfaction_12_Months     6
## 308     86      1 Satisfaction_12_Months     6
## 309     87      0 Satisfaction_12_Months     9
## 310     88      0 Satisfaction_12_Months     7
## 311     89      0 Satisfaction_12_Months     6
## 312     90      1 Satisfaction_12_Months     4
## 313     91      1 Satisfaction_12_Months     9
## 314     92      0 Satisfaction_12_Months     7
## 315     93      0 Satisfaction_12_Months     9
## 316     94      1 Satisfaction_12_Months     8
## 317     95      1 Satisfaction_12_Months     5
## 318     96      0 Satisfaction_12_Months     4
## 319     97      1 Satisfaction_12_Months     5
## 320     98      0 Satisfaction_12_Months     4
## 321     99      1 Satisfaction_12_Months     4
## 322    100      1 Satisfaction_12_Months     7
## 323    101      0 Satisfaction_12_Months     9
## 324    102      1 Satisfaction_12_Months     5
## 325    103      1 Satisfaction_12_Months     7
## 326    104      1 Satisfaction_12_Months     4
## 327    105      0 Satisfaction_12_Months     8
## 328    106      0 Satisfaction_12_Months     2
## 329    107      1 Satisfaction_12_Months     4
## 330    108      1 Satisfaction_12_Months     4
## 331    109      0 Satisfaction_12_Months     6
## 332    110      0 Satisfaction_12_Months     8
## 333    111      0 Satisfaction_12_Months     7
## 334    112      1 Satisfaction_12_Months     4
## 335    113      0 Satisfaction_12_Months     5
## 336    114      1 Satisfaction_12_Months     1
## 337    115      1 Satisfaction_12_Months     3
## 338    116      1 Satisfaction_12_Months     5
## 339    117      1 Satisfaction_12_Months     6
## 340    118      1 Satisfaction_12_Months     4
## 341    119      1 Satisfaction_12_Months     2
## 342    120      1 Satisfaction_12_Months     1
## 343    121      1 Satisfaction_12_Months     6
## 344    122      1 Satisfaction_12_Months     2
## 345    123      0 Satisfaction_12_Months     2
## 346      1      0 Satisfaction_18_Months     2
## 347      2      1 Satisfaction_18_Months     4
## 348      3      1 Satisfaction_18_Months     2
## 349      4      0 Satisfaction_18_Months     1
## 350      5      0 Satisfaction_18_Months     6
## 351      6      1 Satisfaction_18_Months     2
## 352      7      0 Satisfaction_18_Months     2
## 353      8      0 Satisfaction_18_Months    NA
## 354      9      0 Satisfaction_18_Months     6
## 355     10      0 Satisfaction_18_Months     9
## 356     11      0 Satisfaction_18_Months     9
## 357     12      0 Satisfaction_18_Months     9
## 358     13      1 Satisfaction_18_Months     6
## 359     14      0 Satisfaction_18_Months     5
## 360     15      1 Satisfaction_18_Months     6
## 361     16      1 Satisfaction_18_Months     6
## 362     17      1 Satisfaction_18_Months    NA
## 363     18      0 Satisfaction_18_Months     3
## 364     19      1 Satisfaction_18_Months     6
## 365     20      0 Satisfaction_18_Months    NA
## 366     21      0 Satisfaction_18_Months     6
## 367     22      1 Satisfaction_18_Months     2
## 368     23      0 Satisfaction_18_Months     2
## 369     24      0 Satisfaction_18_Months    NA
## 370     28      1 Satisfaction_18_Months    NA
## 371     29      1 Satisfaction_18_Months     7
## 372     30      0 Satisfaction_18_Months     3
## 373     31      0 Satisfaction_18_Months     3
## 374     32      0 Satisfaction_18_Months    NA
## 375     33      1 Satisfaction_18_Months     3
## 376     34      0 Satisfaction_18_Months     4
## 377     38      0 Satisfaction_18_Months     4
## 378     39      0 Satisfaction_18_Months     6
## 379     40      0 Satisfaction_18_Months     1
## 380     41      1 Satisfaction_18_Months     1
## 381     44      1 Satisfaction_18_Months     3
## 382     45      1 Satisfaction_18_Months     3
## 383     46      0 Satisfaction_18_Months     5
## 384     47      0 Satisfaction_18_Months     6
## 385     48      1 Satisfaction_18_Months     1
## 386     49      0 Satisfaction_18_Months    NA
## 387     50      1 Satisfaction_18_Months     7
## 388     51      0 Satisfaction_18_Months     1
## 389     52      1 Satisfaction_18_Months     5
## 390     53      1 Satisfaction_18_Months     5
## 391     54      1 Satisfaction_18_Months     3
## 392     55      0 Satisfaction_18_Months     2
## 393     56      1 Satisfaction_18_Months     4
## 394     57      1 Satisfaction_18_Months     9
## 395     58      0 Satisfaction_18_Months     1
## 396     59      1 Satisfaction_18_Months     4
## 397     60      1 Satisfaction_18_Months     1
## 398     61      0 Satisfaction_18_Months     4
## 399     62      1 Satisfaction_18_Months     8
## 400     63      1 Satisfaction_18_Months     4
## 401     64      0 Satisfaction_18_Months     3
## 402     65      0 Satisfaction_18_Months     4
## 403     66      1 Satisfaction_18_Months     7
## 404     67      0 Satisfaction_18_Months     6
## 405     68      0 Satisfaction_18_Months    NA
## 406     69      0 Satisfaction_18_Months     8
## 407     70      1 Satisfaction_18_Months     3
## 408     71      1 Satisfaction_18_Months     5
## 409     72      1 Satisfaction_18_Months     3
## 410     73      0 Satisfaction_18_Months     6
## 411     74      0 Satisfaction_18_Months     1
## 412     75      0 Satisfaction_18_Months    NA
## 413     76      0 Satisfaction_18_Months     7
## 414     77      0 Satisfaction_18_Months     2
## 415     78      0 Satisfaction_18_Months    NA
## 416     79      1 Satisfaction_18_Months    NA
## 417     80      0 Satisfaction_18_Months     5
## 418     81      0 Satisfaction_18_Months     4
## 419     82      0 Satisfaction_18_Months     4
## 420     83      1 Satisfaction_18_Months     1
## 421     84      1 Satisfaction_18_Months     2
## 422     85      1 Satisfaction_18_Months    NA
## 423     86      1 Satisfaction_18_Months     3
## 424     87      0 Satisfaction_18_Months     4
## 425     88      0 Satisfaction_18_Months     7
## 426     89      0 Satisfaction_18_Months     3
## 427     90      1 Satisfaction_18_Months     2
## 428     91      1 Satisfaction_18_Months     5
## 429     92      0 Satisfaction_18_Months     4
## 430     93      0 Satisfaction_18_Months     7
## 431     94      1 Satisfaction_18_Months     7
## 432     95      1 Satisfaction_18_Months     5
## 433     96      0 Satisfaction_18_Months     8
## 434     97      1 Satisfaction_18_Months    NA
## 435     98      0 Satisfaction_18_Months     1
## 436     99      1 Satisfaction_18_Months    NA
## 437    100      1 Satisfaction_18_Months     2
## 438    101      0 Satisfaction_18_Months     3
## 439    102      1 Satisfaction_18_Months    NA
## 440    103      1 Satisfaction_18_Months     6
## 441    104      1 Satisfaction_18_Months     3
## 442    105      0 Satisfaction_18_Months     4
## 443    106      0 Satisfaction_18_Months    NA
## 444    107      1 Satisfaction_18_Months     5
## 445    108      1 Satisfaction_18_Months     3
## 446    109      0 Satisfaction_18_Months     3
## 447    110      0 Satisfaction_18_Months     6
## 448    111      0 Satisfaction_18_Months     8
## 449    112      1 Satisfaction_18_Months    NA
## 450    113      0 Satisfaction_18_Months     3
## 451    114      1 Satisfaction_18_Months    NA
## 452    115      1 Satisfaction_18_Months    NA
## 453    116      1 Satisfaction_18_Months     2
## 454    117      1 Satisfaction_18_Months     4
## 455    118      1 Satisfaction_18_Months     1
## 456    119      1 Satisfaction_18_Months     1
## 457    120      1 Satisfaction_18_Months     7
## 458    121      1 Satisfaction_18_Months     7
## 459    122      1 Satisfaction_18_Months    NA
## 460    123      0 Satisfaction_18_Months     1
```

melt()함수로 합친 변수를 다시 되돌리려면 cast()함수 사용

```r
wideData <- cast(restructuredData , Person + Gender ~ variable, value="value")
wideData
```

```
##     Person Gender Satisfaction_Base Satisfaction_6_Months
## 1        1      0                 6                     6
## 2        2      1                 7                     7
## 3        3      1                 4                     6
## 4        4      0                 6                     9
## 5        5      0                 6                     7
## 6        6      1                 5                    10
## 7        7      0                 6                     6
## 8        8      0                 2                     5
## 9        9      0                10                     9
## 10      10      0                10                    10
## 11      11      0                 8                     8
## 12      12      0                 6                    10
## 13      13      1                 7                     8
## 14      14      0                 6                     7
## 15      15      1                 9                    10
## 16      16      1                10                    10
## 17      17      1                 1                     2
## 18      18      0                 5                     6
## 19      19      1                 6                    10
## 20      20      0                 5                     6
## 21      21      0                 3                     7
## 22      22      1                 3                     4
## 23      23      0                 7                     6
## 24      24      0                 3                     4
## 25      28      1                 9                    10
## 26      29      1                 8                    10
## 27      30      0                 8                     7
## 28      31      0                 7                     7
## 29      32      0                10                     8
## 30      33      1                 7                     6
## 31      34      0                 5                     7
## 32      38      0                 5                     7
## 33      39      0                 7                     9
## 34      40      0                 4                     5
## 35      41      1                 3                     4
## 36      44      1                 4                     6
## 37      45      1                 8                     5
## 38      46      0                10                     4
## 39      47      0                10                    10
## 40      48      1                 4                     5
## 41      49      0                 2                     4
## 42      50      1                10                    10
## 43      51      0                 2                     4
## 44      52      1                 9                    10
## 45      53      1                 9                    10
## 46      54      1                 4                     4
## 47      55      0                 6                    10
## 48      56      1                 9                     9
## 49      57      1                 6                     6
## 50      58      0                 5                     4
## 51      59      1                 8                     8
## 52      60      1                 5                     6
## 53      61      0                 7                    10
## 54      62      1                 8                     9
## 55      63      1                 8                     9
## 56      64      0                 4                     5
## 57      65      0                10                     8
## 58      66      1                 6                     9
## 59      67      0                 7                     9
## 60      68      0                 3                     3
## 61      69      0                 8                     9
## 62      70      1                 3                     3
## 63      71      1                 8                    10
## 64      72      1                10                     7
## 65      73      0                10                    10
## 66      74      0                 5                     6
## 67      75      0                10                    10
## 68      76      0                10                     9
## 69      77      0                 5                     7
## 70      78      0                 3                     5
## 71      79      1                10                     9
## 72      80      0                 5                    10
## 73      81      0                 5                     6
## 74      82      0                 9                     6
## 75      83      1                 5                     5
## 76      84      1                 8                     6
## 77      85      1                10                     9
## 78      86      1                 7                     7
## 79      87      0                 8                     7
## 80      88      0                10                     9
## 81      89      0                 7                     6
## 82      90      1                 5                     4
## 83      91      1                10                     8
## 84      92      0                 7                     6
## 85      93      0                10                     7
## 86      94      1                10                    10
## 87      95      1                 7                     9
## 88      96      0                 3                     3
## 89      97      1                10                    10
## 90      98      0                 6                     7
## 91      99      1                 6                     5
## 92     100      1                 8                     9
## 93     101      0                 6                     8
## 94     102      1                 7                     8
## 95     103      1                 9                     8
## 96     104      1                 7                     8
## 97     105      0                10                    10
## 98     106      0                10                     4
## 99     107      1                 8                     8
## 100    108      1                 3                     4
## 101    109      0                 7                     6
## 102    110      0                 9                     7
## 103    111      0                 7                     8
## 104    112      1                 5                     3
## 105    113      0                 7                     4
## 106    114      1                 3                     2
## 107    115      1                 5                     5
## 108    116      1                 7                     9
## 109    117      1                 7                     6
## 110    118      1                 3                     4
## 111    119      1                 8                     4
## 112    120      1                 3                     6
## 113    121      1                 6                     6
## 114    122      1                 5                    10
## 115    123      0                 5                     6
##     Satisfaction_12_Months Satisfaction_18_Months
## 1                        5                      2
## 2                        8                      4
## 3                        2                      2
## 4                        4                      1
## 5                        6                      6
## 6                        4                      2
## 7                        4                      2
## 8                        4                     NA
## 9                        5                      6
## 10                      10                      9
## 11                      10                      9
## 12                       9                      9
## 13                       9                      6
## 14                       9                      5
## 15                       8                      6
## 16                       8                      6
## 17                       1                     NA
## 18                       7                      3
## 19                      10                      6
## 20                      NA                     NA
## 21                       5                      6
## 22                       4                      2
## 23                       4                      2
## 24                       2                     NA
## 25                       8                     NA
## 26                       9                      7
## 27                       7                      3
## 28                       6                      3
## 29                      NA                     NA
## 30                       5                      3
## 31                       7                      4
## 32                       4                      4
## 33                       7                      6
## 34                       5                      1
## 35                       3                      1
## 36                       7                      3
## 37                       4                      3
## 38                       4                      5
## 39                       8                      6
## 40                       4                      1
## 41                       1                     NA
## 42                       9                      7
## 43                       4                      1
## 44                       8                      5
## 45                       8                      5
## 46                       3                      3
## 47                       6                      2
## 48                       5                      4
## 49                       7                      9
## 50                       5                      1
## 51                       9                      4
## 52                       7                      1
## 53                      10                      4
## 54                       8                      8
## 55                       7                      4
## 56                       4                      3
## 57                       9                      4
## 58                       8                      7
## 59                       7                      6
## 60                       3                     NA
## 61                      10                      8
## 62                       4                      3
## 63                       7                      5
## 64                       5                      3
## 65                       9                      6
## 66                       4                      1
## 67                       6                     NA
## 68                       7                      7
## 69                       4                      2
## 70                       3                     NA
## 71                       8                     NA
## 72                       6                      5
## 73                       9                      4
## 74                       7                      4
## 75                       4                      1
## 76                       2                      2
## 77                       6                     NA
## 78                       6                      3
## 79                       9                      4
## 80                       7                      7
## 81                       6                      3
## 82                       4                      2
## 83                       9                      5
## 84                       7                      4
## 85                       9                      7
## 86                       8                      7
## 87                       5                      5
## 88                       4                      8
## 89                       5                     NA
## 90                       4                      1
## 91                       4                     NA
## 92                       7                      2
## 93                       9                      3
## 94                       5                     NA
## 95                       7                      6
## 96                       4                      3
## 97                       8                      4
## 98                       2                     NA
## 99                       4                      5
## 100                      4                      3
## 101                      6                      3
## 102                      8                      6
## 103                      7                      8
## 104                      4                     NA
## 105                      5                      3
## 106                      1                     NA
## 107                      3                     NA
## 108                      5                      2
## 109                      6                      4
## 110                      4                      1
## 111                      2                      1
## 112                      1                      7
## 113                      6                      7
## 114                      2                     NA
## 115                      2                      1
```


