# IRD
#Ćwiczenia 1

### 4) Operacje matematyczne, podstawowe funkcje matematyczne/statystyczne

## operacje przypisania, operacje matematyczne

a <- 5
a

a*3
a-1

# Różne rodzaje dzielenia:

a/2

10 %% 3   # reszta z dzielenia
10 %/% 3  # część całkowita z dzielenia
938749324789203 %% 10 # ostatnia cyfra

# Przypisywanie wartości zmiennym i porównywanie zmiennych
a <- 2
b <- 3
a == b
a > b
a < b
a != b

2 == 3
2+2 == 4
3 < 5
3 <= 5
3 <=5 | 10 > 100 # lub
3 <=5 & 10 > 100 # oraz

# Rodzaje cudzysłowów zwykle nie mają znaczenia
var_t <- "SGH"
var_t2 <- 'SGH'

var_t == var_t2

## wbudowane funkcje (wybrane)

sqrt(16) 
abs(-99)
sum(5, 6)
cos(pi)
sin(pi)
log(4)
log(10)
log10(10)
logb(56, base = 5)
logb(base = 5, x = 56)
logb(5, 56)
exp(0)
round(pi, 2)

ceiling(3.3)
floor(3.6)
trunc(5.99)
trunc(-1.5)
floor(-1.5)
ceiling(-1.5)

round(6.592, digits = 2)
factorial(4) # silnia

## przypisywanie

x <- 5 # najpopularniejszy, deklarowanie 

##############################################################################################
# Dygresja o różnicy między "=" a "<-":
# to szczegóły mało istotne na codzień, lepiej po prostu konsekwentnie używać "<-"
x = 5 # trzeba uważać, np:

# przykład 1:
sum(x = 1:10)
x # x nie zostało zadeklarowane w workspace
sum(y <- 1:10) # y deklarowane w workspace
y

# przykład 2: argumenty funkcji
x <- 1 # deklarujemy zmienną
x
cos(x = 0) # podajemy argument funkcji "cos" o nazwie 'x'
# zwraca cos(0) = 1
x # x nadal równy 1 --> "=" nie przypisało wartości 0 do x
cos(x <- 0) # ponownie zwraca cos(0) = 1
x # "<-": do x przypisano wartość 0

# Koniec dygresji
##############################################################################################

## workspace

ls() # sprawdzenie, co znajduje się w Workspace
rm("x") # usuwanie elementu z Workspace
rm(list=ls()) # usuwa wszystkie obiekty z workspace

### 5) Typy zmiennych

calkowita <- 4L
calkowita
typeof(calkowita)
class(calkowita)

przecinkowa <- 1.5
przecinkowa
typeof(przecinkowa)

tekstowa <- "tekst"
tekstowa
typeof(tekstowa)

logiczna <- TRUE
logiczna

typeof(logiczna)
T == TRUE    # obie formy są równoważne, ale czytelniej jest używać pełnej
F == FALSE  

## przydatne stałe
Inf
Inf + 2
24 / 0
-Inf
-24 / 0

NA # Not Available
NA + 3 # operacje na NA dają w wyniku NA

is.na(NA) # używane głównie do usuwania brakujących wartości
is.na(3)
NaN # Not a Number
0/0
Inf - Inf

NULL # brak danych - w sensie technicznym
v <- c(1, NA, NULL)
v

Inf + 2
1/Inf
23 / 0
-23 / 0

missing <- NA
NA + 2
NA == 5

0/0

# Klasa to co innego niż typ. Typ który określa wewnętrzny sposób 
# przechowywania obiektu. Klasa to atrybut obiektu w sensie programowania
# obiektowego.
typeof(1)
class(1)

### 6) Obiekty w R

## skalary:

n <- 100
n

## wektory: wszystkie elementy muszą być tego samego typu:

v1 <- 1:10
v1
v2 <- c(1,4,6,3,11,3)
v2
typeof(v2)
sort(v2)
length(v2)
unique(v2)

v3 <- c("ala", "ma", "kota") # wektor tekstowy
typeof(v3)
v4 <- c()
v5 <- 11:20

length(v1)
mean(v2)
sum(v1)
v1 + v5

# Rzutowanie typów
c(10, 20, TRUE)
c(10, 20, TRUE, 'ala ma kota')
# cały wektor zostaje skonwertowany do najogólniejszego typu

# indeksowanie:
v3
v3[3] # 3ci element
v1[2:4] # element od 2giego do 4tego
v1[c(2,3,10)] # element 2, 3 i 10ty
v1[v1<4 | v1>6]
v1[v1>4 & v1<8]

# a co, gdy wychodzimy poza rzeczywistą długość wektora?
v3
length(v3)
v3[100]

# indeks z minusem oznacza "wszystko oprócz tego"
v3[-1]

# Wektory tekstowe
vec_txt <- c('SGH', 'PW', 'UW', 'SGGW', 'SWPS', 'SGH')
length(vec_txt)
vec_txt_u <- unique(vec_txt) # unikatowe wartości
length(vec_txt_u)
vec_txt_u <- sort(vec_txt_u) # sort działa i na liczbach, i na tekście
vec_txt_u

vec_txt_u[1]
vec_txt_u[2:3]
vec_txt_u[c(1, 3, 4)]

nchar('SGH')
nchar(vec_txt_u) # ta funkcja też jest naturalnie zwektoryzowana

w <- c(4,36,6,2,6,5,6,2,4.6)
w
k <- sqrt(w) # ta funkcja też jest naturalnie zwektoryzowana
k

sort(w)
length(w)
unique(w)
length(unique(w))
sort(unique(w))

w1 <- c(5,5.5,2)
w2 <- c(3,12,5.2)

w1 + w2

w1 <- c(1,2,3,4)
w2 <- c(10,100)
w3 <- c(1000, 2000, 3000)


w1 + w2

w1 <- c(3,4,5,6,7)
2 * w1

# Zawijanie wektorów
w1 + w3

#Kilka dodatkowych operacji
x <- 1:100
x
3 %in% x # czy 3 jest w zbiorze x?

c(3, 100, 2000) %in% x # które elementy tego wektora są w zbiorze x?

# ciagi

licznik <- 1:10
licznik

licznik2 <- 10:0
licznik2

seq(-1, 1, 0.1)

seq(from=-1,to=1,length=21)

seq(1, 1,length = 21)

seq(length=21, from=-1, by=0.1)

rep(1, 5)

rep('TORA', 3)

rep(1:2, times = 3)
rep(1:2,each = 3)
# ^ w praktyce lepiej pisać wprost, co chcemy osiągnąć, zamiast opierać kod na
# znajomości takich pamięciowych sztuczek.


## macierze

m1 <- matrix (1:100, 10, 10, byrow = T)
m1
m2 <- matrix (1:100, 10, 10)
m2

seq(from=-1,to=1,length=20)
m3 <- matrix(seq(from=-1,to=1,length=20), 4 ,5)
m3

rep(1, 5)
rep(1:2, times = 4)
m4 <- matrix(rep(1:3, times = 3), 3, 3)
m4

t(m1) #transpozycja
m1 == t(t(m1)) #transpozycja
all(m1 == t(t(m1))) #?

dim(m1) #wymiary
m1 %*% m2 #mnozenie macierzy

nrow(m1)
ncol(m1)
colSums(m1)

cbind(m1, m2)
rbind(m1, m2)

m1 == m2
any(m1 == m2)
all(m1 == m2)

# indeksowanie macierzy:
m1[2,3]
m1[1,]
m1[,3]
m1[m1>mean(m1)]

## lista-  "wektory", ale mogą przechowywać elementy dowolnych typów,
# także bardzo rozbudowanych (np. inne listy), elementy mogą być różnej długości

lista <- list(a = 1, b = "a", c = 1:4, d = list(), 6)
lista
names(lista) # nazwy elementów listy
class(lista)

# listę indeksuje się podobnie jak wektory, ale:
lista[3] # zwraca listę jednoelementową
class(lista[3]) # mamy dalej listę
lista[[3]]         # zwraca element listy
class(lista[[3]])
lista[[3]][1]      # pierwszy element trzeciego elementu listy

# można się odwoływać po nazwach
lista[["c"]]
# lub użyć operatora '$'
lista$c

# podwójny && porównuje pierwsze elementy, a pojedynczy poszczególne wartości
# (lepiej nie używać tego typu sztuczek w poważnym kodzie)
# & - i ,| - lub
c(TRUE, TRUE) &  c(FALSE, TRUE)
c(TRUE, TRUE) &&  c(TRUE, FALSE)
c(TRUE, TRUE) &&  c(FALSE, FALSE)

all(c(TRUE, FALSE) & c(TRUE, FALSE))
all(c(TRUE, FALSE) | c(TRUE, TRUE))

## typ czynnikowy

kolor.oczu <- c('n', 'n', 'z', 'b', 'b', 'b', 'n', 'z', 'b', 'z')
kolor.oczu
kolor.oczu <- factor(kolor.oczu)
kolor.oczu
levels(kolor.oczu)
levels(kolor.oczu) <- c("brazowe", "niebieskie", "zielone")
levels(kolor.oczu)
kolor.oczu

plec <- c('f','m','f','f','m','m','f',
          'm','f','f')
plec

mode(plec)

plec <- as.factor(plec)
plec

plec2 <- factor(c('f','f','f','f','f'),
                levels=c('f','m'))
plec2


# Tabele częstości
table(plec)

table(plec2)[2]

length(plec)

wiek<-c('>18','<18','<18','<18','<18','>18','>18','>18','>18','>18')
wiek
wiek <- factor(c('>18','<18','<18','<18','<18','>18','>18','>18','>18','>18'))
wiek
length(wiek)

t <- table(plec,wiek)
t

# Warianty tabel częstości
prop.table(t)

margin.table(t,1)

margin.table(t,2)
prop.table(t,1)
prop.table(t,2)

## ramka danych (data frame) - wektory różnych typów o RÓWNEJ liczbie elementów:

df1 <- data.frame(v1= c(10,20,30), v2= c("ala", "ma", "kota"), v3= c(NA, 13, NaN), v4 = c(TRUE, FALSE, TRUE))
df1
names(df1) <- c('wiek', 'haslo', 'wiek_brata', 'ma_siostre')
df1

class(df1)

## ZADANIE 1
# Stwórz wektor o nazwie indeks, który będzie się składał z elementów 
# będącymi poszczególnymi cyframi z numeru Twojego indeksu. 
# Sprawdź, jakiego jest typu. 
# Zamień trzeci element na liczbę 100
# Podnieś 1 i 2 element do kwadratu
# Sprawdź, które elementy są większe od 3 i mniejsze lub równe 8
# Posortuj malejąco 
# Stwórz wektor indeks2, który będzie dwukrotnością wektora indeks
# Dodaj elementy wektora indeks2, podziel przez 7.3 i zaokrąglij wynik do 2 miejsc po przecinku

indeks <- c(2, 5, 3, 4, 9, 2, 7)
typeof(indeks)
indeks[3] <- 100
indeks[1:2] <- indeks[1:2]^2
indeks[indeks > 3 & indeks <= 8]
indeks <- sort(indeks, decreasing = TRUE)
indeks2 <- 2 * indeks
round(sum(indeks2) / 7.3, 2)

## ZADANIE 2
# Stwórz ramkę danych "dane" z następującymi rekordami:
# • imię
# • drugie imię, jeżeli nie ma, to NA
# • wiek
# • płeć - jako czynnik (factor)
# • informację o tym, czy osoba ma status studenta (tak lub nie)
# zawierającymi dane Twoje i trzech innych osób (mogą być zmyślone)

dane <- data.frame(imie = c('Jan', 'Adam', 'Ewa', 'Justyna'),
                   drugie_imie = c('Chryzostom', 'Jan', NA, 'Maria'),
                   wiek = c(24, 25, 23, 31),
                   plec = factor(c('m', 'm', 'f', 'f')),
                   status_studenta = c(TRUE, FALSE, TRUE, FALSE))

# Check:
class(dane$plec) == 'factor' # TRUE

#Wykład 1

# Budujemy pomocniczą funkcję do mierzenia czasu wykonywania różnych operacji
measure_time <- function(f, ...)
{
  start_time <- Sys.time()
  r <- f(...)
  end_time <- Sys.time()
  print(end_time - start_time)
  return(r)
}

getwd()

#ustalenie katalogu roboczego (tam, gdzie znajduja sie pliki z danymi do przykladow)
setwd("github/data/")


##wczytywanie roznego rodzaju danych z pliku

#wartosci rozdzielone przecinkami

titanic <- measure_time(read.csv, "Titanic.csv")
titanic <- measure_time(read_csv, "Titanic.csv")
# Dygresja: data.table potrafi być jeszcze szybszy
library(data.table)
titanic <- measure_time(fread, "Titanic.csv")

przecinkowe <- read_csv("Titanic.csv")
head(przecinkowe)

#wartosci rozdzielone srednikami
srednikowe <- read_csv2("cars.csv")
head(srednikowe)

#wartosci rozdzielone stala szerokoscia
#fwf_widths sluzy podaniu szerokosci kolumn i ich nazw
stale <- read_fwf(file="iris.txt", fwf_widths(c(3, 5, 3, 5, 6), c("Sepal.Length", "Sepal.Width", "Petal.Length", "Petal.Width", "Species")))
head(stale)

#wartosci rozdzielone spacjami
spacjowe <- read_table("heights.txt", col_names=c("height", "cubit"))
head(spacjowe)

##wczytanie danych z ciagu liczb - pierwsza linijka zawsze sluzy jako nazwy kolumn
ciag <- read_csv("a,b,c
                 1,2,3
                 A,B,C")
ciag

#pozbywanie sie metadanych za pomoca skip lub "#"
read_csv("Pierwsza linia metadanych
         Druga linia metadanych
         x,y,z
         1,2,3", skip=2)

read_csv("#Komentarz
         x,y,z
         1,2,3", comment="#")

#wczytanie danych bez nazw kolumn
esoph <- read_csv("esoph.csv", col_names=FALSE)
head(esoph)

#nadanie wlasnych nazw dla kolumn
esoph <- read_csv("esoph.csv", col_names=c("jeden", "2", "trzy", "4", "piec"))
head(esoph)

#konwersja pustych lub konkretnych wartosci na NA (w tym przypadku kropki)
#\n sluzy jako przejscie do nastepnej linijki
read_csv("a,b,c\n1,2,.", na=".")


###pakiet dplyr - umozliwia manipulacje danych zarowno zapisanych w formie ramek danych, 
# jak i przechowywanych w bazach danych. 
# Jest w stanie przetlumaczyc kod R na zapytanie SQL (ale to poza zakresem naszych zajęć)

# http://seananderson.ca/2014/09/13/dplyr-intro.html

# dplyr is built around 5 verbs. 
# These verbs make up the majority of the data manipulation you tend to do. 
# You might need to:

# Select certain columns of data.
# Filter your data to select specific rows.
# Arrange the rows of your data into an order.
# Mutate your data frame to contain new columns.
# Summarise chunks of you data in some way.

#instalacja pakietu
#install.packages("dplyr")
library("dplyr")

#wczytanie przykladowych danych
#install.packages("nycflights13")
library("nycflights13")
dim(flights)
head(flights)

##operacje na danych

#filtrowanie
filter(flights, month==2, day==22)
#rownoznaczne z: 
flights[flights$month == 2 & flights$day == 22, ]

filter(flights, month == 1 | month == 2)
filter(flights, month %in% c(1,2))
#wycinek danych
slice(flights, 1:5)

#sortowanie danych rosnaco wg kolejnych kolumn
arrange(flights, year, month, day)

#sortowanie danych malejaco
arrange(flights, desc(dep_delay))

#wybor konkretnych kolumn 
select(flights, year, month, day)
select(flights, year:day) #przedzial kolumn
select(flights, -(year:day)) #wszystkie poza przedzialem kolumn

#zmiana nazwy kolumny
rename(flights, tail_num = tailnum)
select(flights, tailnum)

#wybor niepowtarzalnych wartosci
distinct(flights, origin, dest)

#dodawanie nowej kolumny
f2 <- mutate(flights,
             gain = arr_delay - dep_delay,
             speed = distance / air_time * 60)

View(f2)

#mozna odniesc sie do wlasnie tworzonej kolumny
mutate(flights,
       gain = arr_delay - dep_delay,
       gain_per_hour = gain / (air_time / 60)
)

#zachowanie tylko nowych kolumn
transmute(flights,
          gain = arr_delay - dep_delay,
          gain_per_hour = gain / (air_time / 60)
)

#podsumowanie zbioru
summarise(flights,
          delay = mean(dep_delay, na.rm = TRUE))

#losowe obserwacje
sample_n(flights, 10) #10 wierszy
sample_frac(flights, 0.01) #10% wierszy

##zgrupowane operacje na danych

#funkcja group_by() pozwala na grupowanie obserwacji w zbiorze
#wykorzystane po niej inne funkcje beda wykonywane dla kazdej grupy osobno

#select() dziala identycznie, ale grupujace zmienne sa zachowywane
a1 <- group_by(flights, year, month, day)
select(a1, day)

distinct(select(a1, day))

#arrange() porzadkuje po zgrupowanych wartosciach
arrange(a1)

#mutate() i filter() dzialaja podobnie
filter(a1, day > 30 & dep_time < 10)

#sample_n() i sample_frac() losuja liczbe lub czesc wierszy dla kazdej grupy
sample_n(a1, 5)
sample_frac(a1, 0.01)

#slice() wybiera wiersze w kazdej z grup
slice(a1,1:2)

#summarise() jest latwiejszy do zrozumienia i uzycia
#przyklad - dane pogrupowane wg nr samolotow, podsumowane poprzez liczbe lotow, srednia odleglosc
#i opoznienie lotu kazdego z samolotow
by_tailnum <- group_by(flights, tailnum)
delay <- summarise(by_tailnum,
                   count = n(),  #liczba lotow
                   dist = mean(distance, na.rm = TRUE),  #sredni dystans
                   delay = mean(arr_delay, na.rm = TRUE))  #srednie opoznienie
delay <- filter(delay, count > 20, dist < 2000)
delay


#funkcje agregacyjne
#liczba obserwacji w danej grupie
destinations <- group_by(flights, dest)
summarise(destinations,
          flights = n()
)

#liczba unikatowych wartosci w zbiorze
summarise(destinations,
          planes = n_distinct(tailnum)
)


#kazde kolejne summarise zabiera jedna "warstwe" zgrupowanego zbioru
daily <- group_by(flights, year, month, day)
(per_day   <- summarise(daily, flights = n()))

(per_month <- summarise(per_day, flights = sum(flights)))

(per_year  <- summarise(per_month, flights = sum(flights)))


#lancuchy
#wykonywanie kazdej operacji po kolei z zapisywaniem krokow w kolejnych obiektach jest dosyc uciazliwe
#przyklad:
a1 <- group_by(flights, year, month, day)
a2 <- select(a1, arr_delay, dep_delay)
a3 <- summarise(a2,
                arr = mean(arr_delay, na.rm = TRUE),
                dep = mean(dep_delay, na.rm = TRUE))
a4 <- filter(a3, arr > 30 | dep > 30)
a4


#bez zapisywania kolejnych krokow mozna tworzyc funkcje zagniezdzone
a4_nested <- filter(
  summarise(
    select(
      group_by(flights, year, month, day),
      arr_delay, dep_delay
    ),
    arr = mean(arr_delay, na.rm = TRUE),
    dep = mean(dep_delay, na.rm = TRUE)
  ),
  arr > 30 | dep > 30
)

all(a4 == a4_nested)

# jednak jest to trudne do czytania, dlatego w dplyr istnieje operator %>%,
# ktory wynik poprzedniej operacji przerzuca jako argument do następnej.
# Mozna dzieki temu zapisac wiele operacji, ktore nalezy czytac od lewej do prawej, od gory do dolu
a4_pipeline <- flights %>%
  group_by(year, month, day) %>%
  select(arr_delay, dep_delay) %>%
  summarise(
    arr = mean(arr_delay, na.rm = TRUE),
    dep = mean(dep_delay, na.rm = TRUE)
  ) %>%
  filter(arr > 30 | dep > 30)

all(a4_pipeline == a4)

#Ćwiczenia 2

# Podpunkt a)
# Wykonaj ponizsze transformacje, za kazdym razem zapisujac posredni wynik do nowej zmiennej

# ze zbioru danych wybierz kolumny dotyczace miesiecy, plci, dlugosci i wagi rybek, zapisz wynik jako lw
# posortuj dane wedlug miesiecy i plci rybek, zapisz wynik jako ms
# do zbioru LW dodaj nowa kolumne bedaca logarytmem dlugosci rybek, nazwij ja log_l, wynikowa tabele zapisz jako log_lw
# wskaz liczbe rybek dla kazdego miesiaca i plci, zapisz wynik jako sum_mon_sex
# pogrupuj rybki wg plci i wybierz te grupy, ktorych srednia waga jest wieksza niz 15

# Podpunkt b)
# Wykonaj ponizsze transformacje, laczac je za pomoca operatora pipeline %>% z pakietu dplyr

# ze zbioru danych wybierz kolumny dotyczace miesiecy, plci, dlugosci i wagi rybek
# posortuj dane wedlug miesiecy i plci rybek
# dodaj nowa kolumne bedaca logarytmem dlugosci rybek, nazwij ja log_l
# wskaz liczbe rybek dla kazdego miesiaca i plci, zapisz wynik jako sum_mon_sex

### 2) Instrukcje warunkowe, petle, funkcje

## instrukcje warunkowe

# Instrukcja przypisania w nawiasie oznacza: wykonaj przypisanie, ale tez i wydrukuj wynik do konsoli

# jeżeli spełniony warunek to wykonaj komendę
(zmienna <- rnorm(1))
if (zmienna < 0){
  cat("mniejsza ")
}

# jeżeli spełniony warunek to wykonaj komendę, w przeciwnym wypadku zrób co innego
(zmienna <- rnorm(1))
if (zmienna < 0){
  cat("mniejsza \n")
}else cat("wieksza\n")

# warunek musi być pojedynczą wartością
if (c(-1,0,1) > 0){
  cat("wieksze\n")
} #error

# ale można podawać rozbudowane warunki
(zmienna <- rnorm(1))
if (zmienna < 0 || zmienna^2 > 0.5){
  cat("OK\n") 
}else{
  cat("Nie OK\n")
}

# ifelse - wersja wektorowa funkcji IF
(zmienna <- rnorm(5))
ifelse(zmienna < 0, "mniejsza", "wieksza")
d <- ifelse(zmienna < 0, "mniejsza", "wieksza")
d

x <- 1:5
y <- -(1:5)
ifelse(zmienna < 0, x, y)



## petle

for(i in 1:5) {
  cat("aktualna wartosc i to", i, "\n")
}

(macierz <- matrix(1:20, 5, 4))
for(i in 1:nrow(macierz))
{
  print(mean(macierz[i,]))
}


# Petla while
licznik <- 1
while(licznik < 5)
{
  licznik <- licznik + runif(1, min = 0, max = 1)
  cat(licznik, '\n')
}


## funkcje
# składnia:
# NazwaFunkcji <- function(argument1, argument 2) {
#   instrukcje
# (opcjonalnie) return(wynik)
# }

# PRZYKLADY:
MojaFunkcja <- function(a,b) {
  a^2 + b^2
}
#wywołanie:
MojaFunkcja(1,2)
MojaFunkcja(124,445)

MojaFunkcja2 <- function(x, y) {
  a <- sin(x)
  b <- cos(y)
  (a+b)^2
}

MojaFunkcja2(1, pi)

# funkcja domyślnie zwraca ostatnie wyrażenie, ale można zadeklarować co ma zwrócić - instrukcja RETURN
MojaFunkcja3 <- function(x, y) {
  a <- sin(x)
  b <- cos(y)
  wynik <- a*b*100
  print("ala ma kota")
  return(c(a, b*100, wynik))
}

MojaFunkcja3(1, 2)

# po instrukcji RETURN nic nie jest już wykonywane:
MojaFunkcja4 <- function(x, y) {
  a <- sin(x)
  b <- cos(y)
  wynik <- a*b*100
  return(c(a, b*100, wynik))
  print("ala ma kota")
}

MojaFunkcja4(1, 2)

MojaFunkcja5 <- function(x,y)
{
  paste(x,y)
}

MojaFunkcja5("ala", "ma")
MojaFunkcja5(MojaFunkcja5("ala", "ma"), "kota")

# ... - arbitralna liczba argumentow. Uzywane glownie, gdy funkcja bierze jako jeden z argumentow
# inna funkcje i musi jej te argumenty przekazac.

measure_time <- function(f, ...)
{
  start_time <- Sys.time()
  r <- f(...)
  end_time <- Sys.time()
  run_time <- end_time - start_time
  return(list(result = r, run_time = run_time))
}

(mt <- measure_time(MojaFunkcja5, 'ala', 'ma'))

mt$result
mt$run_time

### Stosowanie funkcji na wektorach, listach i macierzach - rodzina funkcji apply
# Tutorial (po angielsku): https://www.datacamp.com/community/tutorials/r-tutorial-apply-family

# apply
n <- 5
m <- 10
mx <- matrix(data = round(100*runif(n*m, 0, 1), 0), nrow = n, ncol = m)

apply(mx, 1, sum)
apply(mx, 2, sum)

# lapply

example_list <- list(c(0, 1, 2, 3), rep('p', 5), seq(2, 20, 3), runif(20))
length(example_list)

lapply(example_list, length)
lapply(example_list, function(element){
  if (length(element) > 5) 'Wiecej niz 5 elementow' else '5 elementow lub mniej'
})
# Podpunkt a)
# Wykonaj ponizsze transformacje, za kazdym razem zapisujac posredni wynik do nowej zmiennej

library("tidyverse")

# ze zbioru danych wybierz kolumny dotyczace miesiecy, plci, dlugosci i wagi rybek, zapisz wynik jako lw

lw <- select(RuffeSLRH92, month, sex, length, weight)

# posortuj dane wedlug miesiecy i plci rybek, zapisz wynik jako ms

ms <- arrange(lw, month, sex)

# do zbioru LW dodaj nowa kolumne bedaca logarytmem dlugosci rybek, nazwij ja log_l, wynikowa tabele zapisz jako log_lw

log_lw <- mutate(lw,
                 log_l = log(length))

# wskaz liczbe rybek dla kazdego miesiaca i plci, zapisz wynik jako sum_mon_sex

by_mon_sex <- group_by(lw, month, sex)
sum_mon_sex <- summarise(by_mon_sex,
                         count = n())

# pogrupuj rybki wg plci i wybierz te grupy, ktorych srednia waga jest wieksza niz 15

by_sex <- group_by(lw, sex)
mean_weight_by_sex <- summarise(by_sex,
                                mean_weight = mean(weight, na.rm = TRUE))
mean_weight_by_sex_above_15 <- filter(mean_weight_by_sex, mean_weight > 15)

# Podpunkt b)
# Wykonaj ponizsze transformacje, laczac je za pomoca operatora pipeline %>% z pakietu dplyr

# ze zbioru danych wybierz kolumny dotyczace miesiecy, plci, dlugosci i wagi rybek
# posortuj dane wedlug miesiecy i plci rybek
# dodaj nowa kolumne bedaca logarytmem dlugosci rybek, nazwij ja log_l
# wskaz liczbe rybek dla kazdego miesiaca i plci, zapisz wynik jako sum_mon_sex

sum_mon_sex <- RuffeSLRH92 %>%
  select(., month, sex, length, weight) %>%
  arrange(., month, sex) %>%
  mutate(., log_l = log(length)) %>%
  group_by(., month, sex) %>%
  summarise(., count = n())

#Wykład 2

# Wczytanie danych

titanic_fpath <- "github/data/titanic_full.csv"
tdf <- read.csv(titanic_fpath)

# Ułamek liczby rekordów przeznaczony do zbioru testowego
test_prop <- 0.25

test_bound <- floor(nrow(tdf)* test_prop)

tdf <- tdf[sample(nrow(tdf)), ]
tdf.test <- tdf[1:test_bound, ]
tdf.train <- tdf[(test_bound+1):nrow(tdf), ]

# Eksploracja danych

names(tdf)
str(tdf)
table(tdf$survived)
prop.table(table(tdf$survived))

# Budowa drzewa decyzyjnego

tree <- rpart(survived ~ pclass + sex + age + sibsp + parch + fare + embarked,
              data=tdf.train,
              method="class",
              control = list(maxdepth = 3))

# Wizualizacja drzewa

tree

plot(tree)
text(tree, pretty = TRUE)

rpart.plot(tree, under=FALSE, tweak=1.3, fallen.leaves = TRUE)

# Wartości w węzłach drzewa:
# - przewidywana kategoria
# - prawdopodobieństwo przynależności do kategorii 1
# - procentowy udział obserwacji w danym węźle

# Interpretacja wyników

prop.table(table(tdf$sex, tdf$survived), 1)
prop.table(table(tdf$sex, tdf$survived), 2)

# Weryfikacja jakości klasyfikacji

EvaluateClassifier <- function(response_colname, prediction_colname, df,  positive="1")
{
  y <- factor(df[response_colname][[1]]) # factor of positive / negative cases
  predictions <- factor(df[prediction_colname][[1]]) # factor of predictions
  precision <- posPredValue(predictions, y, positive)
  recall <- sensitivity(predictions, y, positive)
  F1 <- (2 * precision * recall) / (precision + recall)
  
  return(list(precision=precision, recall=recall, F1=F1))
}

# Weryfikacja jakości klasyfikacji - zbiór uczący i testowy

## https://en.wikipedia.org/wiki/Precision_and_recall

tdf.train$survival_predicted <- predict(tree, tdf.train, type = "class")
tdf.test$survival_predicted <- predict(tree, tdf.test, type = "class")

EvaluateClassifier('survived', 'survival_predicted', tdf.train)
EvaluateClassifier('survived', 'survival_predicted', tdf.test)

# Alternatywne drzewo decyzyjne - głębsze

tree_deeper <- rpart(survived ~ pclass + sex + age + sibsp + parch + fare + embarked,
                     data=tdf.train,
                     method="class",
                     control = list(maxdepth = 10))

rpart.plot(tree_deeper, under=FALSE, tweak=1.5, fallen.leaves = TRUE)

tdf.train$survival_predicted_deeper <- predict(tree_deeper, tdf.train, type = "class")
tdf.test$survival_predicted_deeper <- predict(tree_deeper, tdf.test, type = "class")

EvaluateClassifier('survived', 'survival_predicted_deeper', tdf.train)
EvaluateClassifier('survived', 'survival_predicted_deeper', tdf.test)

# Las losowy, czyli kombinacja wielu drzew

#install.packages("party")
library(party)

set.seed(123)
forest <- cforest(as.factor(survived) ~ pclass + sex + age + sibsp + parch + fare + embarked,
                  data = tdf.train, 
                  controls=cforest_unbiased(ntree=200, mtry=3))

tdf.train$survival_predicted_forest<- predict(forest, tdf.train, OOB=TRUE, type = "response")
tdf.test$survival_predicted_forest<- predict(forest, tdf.test, OOB=TRUE, type = "response")

EvaluateClassifier('survived', 'survival_predicted_forest', tdf.train)
EvaluateClassifier('survived', 'survival_predicted_forest', tdf.test)

#Ćwiczenia 3
# Histogram
hist(diamonds$carat)
hist(diamonds$carat, col = "red")
hist(diamonds$carat, col = "red", breaks = 20)
hist(diamonds$carat, col = "red", breaks = 50)
hist(diamonds$carat, col = "red", breaks = 100)
hist(diamonds$carat, col = "red", breaks = 500)

# Wykresy bazowe

plot(diamonds$carat, diamonds$price)

plot(diamonds$carat, diamonds$price, col = "blue", pch = 20,
     xlim = c(0, 8), ylim = c(0, 20000), 
     xlab = "masa [karaty]", ylab = "cena [USD]",
     main = "Diamenty: zaleznosc ceny od masy")

################################################################################
# ggplot
################################################################################

##kazdy wykres sklada sie:
ggplot(diamonds)   +  # z odwolania do zbioru danych 
  geom_point( # warstw ~ 'ksztaltow'
    aes( x = carat, y = price) # przyporzadkowania zmiennych do osi wewnatrz warstwy 
  )

## ale 'rzutowania' mozna podac od razu: 
ggplot(diamonds,  aes( x = carat, y = price) ) +
  geom_point( ) ## wtedy wszystkie warstwy maja domyslne przyporzadkowane zmienne

### jakie sa inne warstwy? 

## linia (lamana)
ggplot(diamonds)   +
  geom_line( 
    aes( x = carat, y = price, color = "red") 
  )

## punkty + linia trendu
ggplot(diamonds, aes( x = carat, y = price) )   +
  geom_point( ) +
  geom_smooth( 
    aes( x = carat, y = price) 
  )

ggplot(diamonds, aes( x = carat, y = price) )   +
  geom_point( ) +
  geom_smooth( 
    aes( x = carat, y = price),
    method = "lm"
  )  

ggplot(diamonds,  aes( x = carat, y = price) ) +
  geom_point( ) +
  geom_smooth(method = "loess") 

## Wykres pudelkowy (boxplot) 

ggplot(diamonds, aes(x = cut, y = price)) +
  geom_boxplot()

## wykres slupkowy 

diamondsMean <- diamonds %>% 
  group_by(., clarity) %>% 
  summarise(., price = mean(price))

# Srednia cena w podziale na szlif
ggplot(diamondsMean) + 
  geom_bar( aes(x = clarity, y = price ), 
            stat = "identity") 

diamondsMeanCut <- diamonds %>% 
  group_by(., clarity, cut) %>% 
  summarise(., price = mean(price))

# Srednia cena w podziale na szlif i czystosc

ggplot(diamondsMeanCut) + 
  geom_bar( aes(x = clarity, y = price, fill = cut ),
            stat = "identity") 

ggplot(diamondsMeanCut) + 
  geom_bar( aes(x = clarity, y = price, fill = cut ),
            stat = "identity",
            position = "dodge") 

## Histogram

ggplot(diamonds) + 
  geom_histogram( aes(x = carat )) 

ggplot(diamonds) + 
  geom_histogram( aes(x = carat), binwidth = 0.02) 

## Wykres gestosci 

ggplot(diamonds) + 
  geom_density( aes(x = price )) 

# W zaleznosci od czystosci
ggplot(diamonds) + 
  geom_density( aes(x = price, fill = clarity)) 

# alpha - parametr przejrzystosci
ggplot(diamonds) + 
  geom_density( aes(x = price, fill = clarity), alpha = 1) 

ggplot(diamonds) + 
  geom_density( aes(x = price, fill = clarity), alpha = 0.2) 

### jakie moga byc parametry kazdej warstwy?

## color
ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price,
         col = clarity)
  )

## ale
ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price), 
    col = "blue"
  )

ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price, col = "blue")
  )

## fill

ggplot(diamonds)   +  
  geom_smooth( 
    aes( x = carat, y = price,
         fill = clarity)
  )

### roznica miedzy fill a color 

ggplot(filter(diamonds, clarity == "I1",carat <=1))   +  
  geom_bar( 
    aes( x = carat , fill = clarity)
  )

ggplot(filter(diamonds, clarity == "I1", carat <=1))   +  
  geom_bar( 
    aes( x = carat , col = clarity)
  )

## shape 

ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price,
         col = clarity,
         shape = cut)
  )

## size

ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price,
         size = z),
    alpha = 0.4
  )


## typ linii 
ggplot(diamondsMeanCut)   +  
  geom_line( 
    aes( x = clarity , y = price , linetype = cut, group = cut)
  )

### grupowanie wykresow 

ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price)) 

ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price)) +
  facet_grid(cut ~. )

ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price)) +
  facet_grid(. ~ cut )

ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price)) +
  facet_grid(clarity ~ cut )

### kwestie estetyczne 

ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price,
         col = clarity)
  )

## sterowanei wygladem poprzez theme i jego predefiniowane warianty
ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price,
         col = clarity)
  ) + 
  theme_bw(base_size = 16)


ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price,
         col = clarity)
  ) + 
  theme_bw(base_size = 16) +
  xlab("Karaty") +
  ylab("Cena") +
  theme(axis.text.x = element_text(face="bold", color="#993333", 
                                   size=14, angle=45))

## kolejnosc ma znaczenie: 

ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price,
         col = clarity)
  ) + 
  xlab("Karaty") +
  ylab("Cena") +
  theme(axis.text.x = element_text(face="bold", color="#993333", 
                                   size=14, angle=45)) +
  theme_bw(base_size = 16) 


## zmiany na osiach 
ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price,
         col = clarity)
  ) + 
  xlab("Karaty") +
  ylab("Cena") +
  theme_bw(base_size = 16)  +
  scale_x_continuous(breaks = c(0:5), 
                     labels = c("0 karatow", "1 karat", "2 karaty", "3 karaty", "4 karaty", "5 karatow")) 

## zmiany legendy 
ggplot(diamonds)   +  
  geom_point( 
    aes( x = carat, y = price,
         col = clarity)
  ) + 
  xlab("Karaty") +
  ylab("Cena") +
  theme_bw(base_size = 16)  +
  scale_color_discrete(name = "Czystosc")


### eksportowanie wykresow 

pdf("diamonds.pdf", width = 10, height = 8)

print(
  ggplot(diamonds)   +  
    geom_point( 
      aes( x = carat, y = price))
)

dev.off()

## wiele wykresow
clarityVal  <- unique(diamonds$clarity)

for(i in 1:length(clarityVal)){
  pdf(
    paste0("diamonds",i,".pdf"), 
    width = 10, height = 8)
  
  print(
    ggplot(
      filter(diamonds, clarity == clarityVal[i])  
    ) +  
      geom_point( 
        aes( x = carat, y = price)) +
      ggtitle(clarityVal[i])
  )
  
  dev.off()
}

pdf(
  "diamondsClarity.pdf", 
  width = 10, height = 8)
for(i in 1:length(clarityVal)){
  print(
    ggplot(
      filter(diamonds, clarity == clarityVal[i])  
    ) +  
      geom_point( 
        aes( x = carat, y = price)) +
      ggtitle(clarityVal[i])
  )
  
}

dev.off()


### dodatek - zmiana struktury danych funkcjami melt i dcast 

#install.packages("datasets")
#install.packages("reshape2")
library(reshape2)

# Indeksy giełd europejskich
EuStockMarkets <- as_tibble(
  data.frame(time = time(EuStockMarkets), EuStockMarkets)
)

meltedStock <- as_tibble(melt(EuStockMarkets, id = "time" ))

ggplot(meltedStock) +
  geom_line(aes(x = time, y = value, col = variable))

##i powrot do poprzedniej postaci
dcast(meltedStock, time ~ variable )

# 1)
# Dla danych o samochodach (cars) narysuj wykres punktowy dystansu hamowania 
# w zaleznosci od predkosci, uzywajac:
# a) funkcji bazowych,
# b) ggplot.

# W podpunkcie b) dopasuj linie trendu (na rozne sposoby). Wybierz najlepsza, wybor uzasadnij.
# Nadaj wykresom tytuly i opisz osie (po polsku).

data(cars)
cars <- cars

str(cars)
summary(cars)

plot(x = cars$speed, y = cars$dist,
     xlab = "Predkosc", ylab = "Dystans hamowania", 
     main = "Wykres punktowy dystansu hamowania\n w zaleznosci od predkosci")

library(ggplot2)

plot_gg <- ggplot(cars, aes( x = speed, y = dist) )   +
  geom_point( ) +
  xlab("Predkosc") +
  ylab("Dystans hamowania") +
  ggtitle("Wykres punktowy dystansu hamowania w zaleznosci od predkosci")

plot_gg

# Rozne metody dopasowywania krzywych:
# http://ggplot2.tidyverse.org/reference/geom_smooth.html

plot_gg + geom_smooth(method = "lm")
plot_gg + geom_smooth(method = "glm")
plot_gg + geom_smooth(method = "gam")
plot_gg + geom_smooth(method = "loess")
plot_gg + geom_smooth(method = "loess", span = 2)

# Wiemy z fizyki, ze energia kinetyczna jest proporcjonalna do kwadratu predkosci,
# wiec spodziewamy sie krzywej drugiego stopnia.

## 2)
# Dla danych iris zwizualizuj zaleznosci pomiedzy wymiarami elementow 
# kwiatow w zaleznosci od gatunku, uzywajac pakietu ggplot.
# Nadaj wykresom tytuly i opisz osie (po polsku).

# Sprobuj roznych (co najmniej 2) podejsc do wizualizacji danych. 
# Wskaz sposob, ktory Twoim zdaniem bedzie najbardziej czytelny 
# dla osoby niezaznajomionej ze statystyką i programowaniem.

# Zwiazki do pokazania (w zaleznosci od gatunku):
# a) Dlugosc kwiatu a szerokosc kwiatu
# b) Dlugosc liscia a szerokosc liscia
# c) Dlugosc liscia a dlugosc kwiatu

# (Sepal oznacza lisc, petal - kwiat)

data(iris)
iris <- iris

str(iris)
summary(iris)

# a) Dlugosc kwiatu a szerokosc kwiatu

ggplot(iris)   +  
  geom_point( 
    aes( x = Petal.Width, y = Petal.Length)) +
  facet_grid(. ~ Species) +
  xlab("Szerokosc kwiatu") +
  ylab("Dlugosc kwiatu ") +
  ggtitle("Dlugosc kwiatu a szerokosc kwiatu")

ggplot(iris)   +  
  geom_point( 
    aes( x = Petal.Width, y = Petal.Length,
         col = Species)
  ) +
  xlab("Szerokosc kwiatu") +
  ylab("Dlugosc kwiatu") +
  ggtitle("Dlugosc kwiatu a szerokosc kwiatu") +
  labs(color='Gatunek') 

# b) Dlugosc liscia a szerokosc liscia

ggplot(iris)   +  
  geom_point( 
    aes( x = Sepal.Width, y = Sepal.Length)) +
  facet_grid(. ~ Species) +
  xlab("Szerokosc liscia") +
  ylab("Dlugosc liscia") +
  ggtitle("Dlugosc liscia a szerokosc liscia")

ggplot(iris)   +  
  geom_point( 
    aes( x = Sepal.Width, y = Sepal.Length,
         col = Species, shape = Species)
  ) +
  xlab("Szerokosc liscia") +
  ylab("Dlugosc liscia") +
  ggtitle("Dlugosc liscia a szerokosc liscia") +
  labs(color='Gatunek', shape = "Gatunek") 

# c) Dlugosc liscia a dlugosc kwiatu

ggplot(iris)   +  
  geom_point( 
    aes( x = Petal.Length, y = Sepal.Length)) +
  facet_grid(. ~ Species) +
  xlab("Dlugosc kwiatu") +
  ylab("Dlugosc liscia") +
  ggtitle("Dlugosc liscia a dlugosc kwiatu")

ggplot(iris)   +  
  geom_point( 
    aes( x = Petal.Length, y = Sepal.Length,
         col = Species, shape = Species)
  ) +
  xlab("Dlugosc kwiatu") +
  ylab("Dlugosc liscia") +
  ggtitle("Dlugosc liscia a dlugosc kwiatu") +
  labs(color='Gatunek', shape = "Gatunek") 

#Ćwiczenia 4 

data_fpath <- 'data/car.data.txt' # Wpisac poprawna sciezke dostepu w zaleznosci od lokalizacji pliku
DATA_SET <- read.csv(data_fpath, header = FALSE)
names(DATA_SET) <- c("buying", "maint", "doors", "persons",
                     "lug_boot", "safety", "class")

# Eksploracja danych
str(DATA_SET)
summary(DATA_SET)

# Laczymy klasy acc, good, vgood w jedna

DATA_SET$class <- factor(ifelse(DATA_SET$class == "unacc", 0, 1))

################################################################################
# Zadanie 1
################################################################################

# W oparciu o przyklad omowiony na wykladzie
# (skrypt IRD_2017_lecture_2017-11-07_decision_trees_in_R.R)
# zbuduj 2 drzewa decyzyjne przewidujace klase samochodu 
# w zaleznosci od jego pozostalych parametrow.

# Niech pierwsze z drzew ma maksymalna glebokosc rowna 3, drugie - rowna 5.

# Zwizualizuj drzewa. Czym sie roznia miedzy soba?
# Policz precyzje i czulosc (precision and recall) klasyfikacji
# z uzyciem obu drzew na zbiorze testowym. Porownaj wyniki. Co jest przyczyna roznicy?

# Uzyj 80% rekordow jako zbioru uczacego i 20% jako zbioru testowego.














################################################################################
################################################################################

# Biblioteki
library(party) # inna biblioteka do drzew decyzyjnych

# Czym sie roznia rpart i ctree?

# https://stats.stackexchange.com/questions/12140/conditional-inference-trees-vs-traditional-decision-trees

# both rpart and ctree recursively perform univariate splits 
# of the dependent variable based on values on a set of covariates.
# rpart and related algorithms usually employ information measures 
# (such as the Gini coefficient) for selecting the current covariate.
# 
# ctree, according to its authors (...) avoids the following variable selection bias 
# of rpart (and related methods): They tend to select variables that have 
# many possible splits or many missing values. 
# Unlike the others, ctree uses a significance test procedure 
# in order to select variables instead of selecting the variable 
# that maximizes an information measure (e.g. Gini coefficient).

# Alternatywny sposob podzialu zbioru na uczacy i testowy
TRAINING_SET_FRACTION <- 0.7
training.set.index <- (runif(nrow(DATA_SET)) < TRAINING_SET_FRACTION)
train.set <- DATA_SET[training.set.index, ]
test.set <- DATA_SET[!training.set.index, ]

ctree.model <- ctree(factor(class) ~ ., data = train.set,
                     controls = ctree_control(mincriterion = 0.99,
                                              minsplit = 20))
plot(ctree.model, tnex = 2, type = "simple")
plot(ctree.model, tnex = 2, type = "extended")

# Roughly, the algorithm works as follows: 
# 
# 1) Test the global null hypothesis of independence between any of the input variables 
# and the response (which may be multivariate as well). 
# Stop if this hypothesis cannot be rejected. 
# Otherwise select the input variable with strongest association to the response. 
# This association is measured by a p-value corresponding to a test 
# for the partial null hypothesis of a single input variable and the response. 
# 
# 2) Implement a binary split in the selected input variable. 
# 
# 3) Recursively repeat steps 1) and 2).

devAskNewPage(ask = TRUE) # do kontrolowania wydruku wynikow

# To samo poprzednia metoda - rpart
rpart.model <- rpart(class ~ ., train.set, cp = 0.01, minsplit = 3)
plotcp(rpart.model)

# Przycinanie drzewa
minimum.error <- which.min(rpart.model$cptable[, "xerror"])
optimal.complexity <- rpart.model$cptable[minimum.error, "CP"]
points(minimum.error, rpart.model$cptable[minimum.error, "xerror"],
       col = "red", pch = 19)
rpart.model.pruned <- prune(rpart.model, cp = optimal.complexity)

# Porownanie drzewa przed i po przycieciu
rpart.plot(rpart.model, under=FALSE, tweak=1.3, fallen.leaves = TRUE)
rpart.plot(rpart.model.pruned, under=FALSE, tweak=1.3, fallen.leaves = TRUE)

# Porownanie wynikow metod
confusion.matrix <- list()
print(confusion.matrix[[1]] <- table(predict(ctree.model, new = test.set),
                                     test.set$class))
print(confusion.matrix[[2]] <- table(predict(rpart.model, type = "class",
                                             newdata = test.set),
                                     test.set$class))
print(confusion.matrix[[3]] <- table(predict(rpart.model.pruned, type = "class",
                                             newdata = test.set),
                                     test.set$class))

CalculateAccuracy <- function(confusion.matrix) {
  return(sum(diag(confusion.matrix)) / sum(confusion.matrix))
}

print(data.frame(model = c("ctree.model", "rpart.model", "rpart.model.pruned"),
                 accuracy = sapply(confusion.matrix, CalculateAccuracy)),
      row.names = FALSE)

# Bonus: algorytmiczne konstruowanie formul do zadan klasyfikacji

FormulaString <- function(tdf, response_colname)
{
  predictor_colname_vec <- setdiff(names(tdf), response_colname)
  return(paste(response_colname, paste(predictor_colname_vec, collapse = " + "), sep = " ~ "))
}

FormulaString(train.set, "class")

rpart.model <- rpart(formula = FormulaString(train.set, "class"), train.set, cp = 0.01, minsplit = 2)
rpart.model

# Inicjalizacja ziarna do zmiennych pseudolosowych
set.seed(1)

# Dane
data_fpath <- 'github/data/car.data.txt' # Wpisac poprawna sciezke dostepu w zaleznosci od lokalizacji pliku
DATA_SET <- read.csv(data_fpath, header = FALSE)
names(DATA_SET) <- c("buying", "maint", "doors", "persons",
                     "lug_boot", "safety", "class")

# Eksploracja danych
str(DATA_SET)
summary(DATA_SET)

# Laczymy klasy acc, good, vgood w jedna

DATA_SET$class <- factor(ifelse(DATA_SET$class == "unacc", 0, 1))

# Zadanie 1

# W oparciu o przyklad omowiony na wykladzie
# (skrypt IRD_2017_lecture_2017-11-07_decision_trees_in_R.R)
# zbuduj drzewo decyzyjne przewidujace klase samochodu 
# w zaleznosci od jego pozostalych parametrow.
# Uzyj 80% rekordow jako zbioru uczacego i 20% jako zbioru testowego.

# Biblioteki
library(rpart) # do drzewa
library(rpart.plot) # do rysowania drzewa
library(caret) # do oceny wyników

test_prop <- 0.20
test_bound <- floor(nrow(DATA_SET)* test_prop)
tdf <- DATA_SET[sample(nrow(DATA_SET)), ] # mieszamy losowo kolejnosc wierszy
tdf.test <- tdf[1:test_bound, ]
tdf.train <- tdf[(test_bound+1):nrow(tdf), ]

# Budowa drzew decyzyjnych

tree3 <- rpart(class ~ buying + maint + doors + persons + lug_boot + safety,
               data=tdf.train,
               method="class",
               control = list(maxdepth = 3))

rpart.plot(tree3, under=FALSE, tweak=1.3, fallen.leaves = TRUE)

tree5 <- rpart(class ~ buying + maint + doors + persons + lug_boot + safety,
               data=tdf.train,
               method="class",
               control = list(maxdepth = 5))

tree5 <- rpart(class ~ .,
               data=tdf.train,
               method="class",
               control = list(maxdepth = 5))

rpart.plot(tree5, under=FALSE, tweak=1.3, fallen.leaves = TRUE)

# Ewaluacja wynikow

EvaluateClassifier <- function(response_colname, prediction_colname, df,  positive="1")
{
  y <- factor(df[response_colname][[1]]) # factor of positive / negative cases
  predictions <- factor(df[prediction_colname][[1]]) # factor of predictions
  precision <- posPredValue(predictions, y, positive)
  recall <- sensitivity(predictions, y, positive)
  F1 <- (2 * precision * recall) / (precision + recall)
  
  return(list(precision=precision, recall=recall, F1=F1))
}

# Weryfikacja jakości klasyfikacji

## https://en.wikipedia.org/wiki/Precision_and_recall

# tree3

tdf.test$prediction3 <- predict(tree3, tdf.test, type = "class")
EvaluateClassifier('class', 'prediction3', tdf.test)

# tree5

tdf.test$prediction5 <- predict(tree5, tdf.test, type = "class")
EvaluateClassifier('class', 'prediction5', tdf.test)

#Ćwiczenia 5

# Inicjalizacja ziarna do zmiennych pseudolosowych
set.seed(1)

# dzielimy na zbior treningowy i testowy
train_proportion <- 0.7
train_index <- runif(nrow(dane)) < train_proportion
train <- dane[train_index,]
test <- dane[!train_index,]

# Regresja liniowa
lin_m <- lm(quality ~ ., data = train)

# Drzewo regresji
d.regr <- rpart(quality ~., data = train, cp = 0.01)
#plot(d.regr, margin = 0.2)
#text(d.regr, pretty = 0)
rpart.plot(d.regr, under=FALSE, fallen.leaves = FALSE, cex = 0.9)

# Drzewo regresji - wieksze
d.regr.duze <- rpart(quality ~. , data = train, cp = 0.003)
#plot(d.regr.duze, margin = 0.2)
#text(d.regr.duze, pretty = 0)
rpart.plot(d.regr.duze, under=FALSE, fallen.leaves = FALSE, cex = 0.5)

min.error <- which.min(d.regr.duze$cptable[,"xerror"])
opt.cp <- d.regr.duze$cptable[min.error,"CP"]

plotcp(d.regr.duze)
points(min.error, d.regr.duze$cptable[min.error, "xerror"], pch = 19, col = "red")

d.regr.przyciete <- prune.rpart(d.regr.duze, cp = opt.cp)
#plot(d.regr.przyciete, margin = 0.2)
#text(d.regr.przyciete, pretty = 0)
rpart.plot(d.regr.przyciete, under=FALSE, fallen.leaves = FALSE, cex = 0.7)

################################################################################
# 2) Variable Importance, RSS, MAE, RMSE, RAE, RRSE, R^2
################################################################################

# variable importance

varImp(lin_m)
d.regr$variable.importance
d.regr.przyciete$variable.importance

# odchylenia reszt - rozne miary

# funkcja residuals liczy reszty = wartosci rzeczywiste - prognoza:
all(as.vector(residuals(d.regr)) == train$quality - predict(d.regr, train))

modele <- list("d.regr" = d.regr, "d.regr.duze" = d.regr.duze, "d.regr.przyciete" = d.regr.przyciete,
               "lin_m" = lin_m)

OcenaModeli <- function(modele, dane, predicted_col_name) {
  
  print("Suma kwadatow reszt RSS")
  print(sapply(modele, function(x) sum((dane[[predicted_col_name]] - predict(x, dane))^2) ))
  
  print("Średni błąd absolutny MAE")
  print(sapply(modele, function(x) sum(abs((dane[[predicted_col_name]] - predict(x, dane))))/nrow(dane) ))
  
  print("Pierwiastek błędu średniokwadratowego RMSE")
  print(sapply(modele, function(x) sqrt(sum((dane[[predicted_col_name]] - predict(x, dane))^2)/nrow(dane)) ))
  
  print("Względny błąd absolutny RAE")
  print(sapply(modele, function(x) sum(abs((dane[[predicted_col_name]] - predict(x, dane))))/sum(abs(dane[[predicted_col_name]] - mean(dane[[predicted_col_name]]))) ))
  
  print("Pierwiastek Względnego błędu średniokw RRSE")
  print(sapply(modele, function(x) sqrt(sum((dane[[predicted_col_name]] - predict(x, dane))^2)/sum((dane[[predicted_col_name]] - mean(dane[[predicted_col_name]]))^2)) ))
  
}

OcenaModeli(modele, train, 'quality')
OcenaModeli(modele, test, 'quality')

################################################################################
# Drzewa klasyfikacyjne - powtorzenie, ocena dokladnosci
################################################################################

# zmienna objasniana zamieniamy na zmienna binarna: jezeli quality >= 6, to jakosc wysoka, wpp niska:

dane$quality <- ifelse(dane$quality >= 6, 'high', 'low')

set.seed(1)
train_proportion <- 0.7
train_index <- runif(nrow(dane)) < train_proportion
train <- dane[train_index,]
test <- dane[!train_index,]

# budujemy i porownujemy 2 drzewa klasyfikacyjne: lekka modyfikacja kodow powyzej
d.klas <- rpart(quality~., data = train, method = "class", cp = 0.001)
#plot(d.klas, margin = 0.2)
#text(d.klas, pretty = 0)
rpart.plot(d.klas, under=FALSE, fallen.leaves = FALSE, cex = 0.3)

min.error <- which.min(d.klas$cptable[,"xerror"])
opt.cp <- d.klas$cptable[min.error,"CP"]

plotcp(d.klas)
points(min.error, d.klas$cptable[min.error, "xerror"], pch = 19, col = "red")

d.klas.przyciete <- prune.rpart(d.klas, cp = opt.cp)
#plot(d.klas.przyciete, margin = 0.2)
#text(d.klas.przyciete, pretty = 0)
rpart.plot(d.klas.przyciete, under=FALSE, fallen.leaves = FALSE, cex = 0.5)

# 3) Classification matrix + its statistics
CM <- list()
CM[["d.klas"]] <- table(predict(d.klas, new = test, type = "class"), test$quality)
CM[["d.klas.przyciete"]] <- table(predict(d.klas.przyciete, new = test, type = "class"), test$quality)

# Accuracy = odsetek poprawnie sklasyfikowanych odpowiedzi
CalcAcc <- function(macierz) {
  return(sum(diag(macierz))/sum(macierz))
}

printAcc <- function () {
  cat(toupper("Accuracy dla wybranych modeli \n"))
  cat("\n")
  Accuracy <- data.frame(model = names(CM), Accuracy = round(sapply(CM, CalcAcc), 6))
  print(Accuracy, row.names = FALSE)
  return(Accuracy)
}

Accuracy <- printAcc()

# Misclassification rate = 1-Accuracy = odsetek blednie sklasyfikowanych odpowiedzi
MER <- sapply(Accuracy[2], function(x) 1-x)
colnames(MER) <- "Missclassification Error Rate"
rownames(MER) <- Accuracy[[1]]
MER

# Zadanie 1
###############################################################################################

# napisz funkcje, ktora na podstawie macierzy klasyfikacji oblicza i zwraca
# 3-elementowa nazwana liste zawierajaca informacje o accuracy, sensitivity i specificity modelu.

EvaluateModel <- function(classif_mx)
{
  # Sciagawka: https://en.wikipedia.org/wiki/Sensitivity_and_specificity#Confusion_matrix
  true_positive <- classif_mx[1,1]
  true_negative <- classif_mx[2,2]
  condition_positive <- sum(classif_mx[ ,1])
  condition_negative <- sum(classif_mx[ ,2])
  # Uzywanie zmiennych pomocniczych o sensownych nazwach
  # ulatwia zrozumienie, co sie dzieje w funkcji
  accuracy <- (true_positive + true_negative) / sum(classif_mx)
  sensitivity <- true_positive / condition_positive
  specificity <- true_negative / condition_negative
  return(list(accuracy = accuracy, 
              sensitivity = sensitivity,
              specificity = specificity))
  # Notacja "accuracy = accuracy" itd. jest potrzebna,
  # zeby elementy listy mialy nazwy.
}

###############################################################################################
# Zadanie 2
###############################################################################################

### Po kolei:

# Wczytaj dane o czerwonych winach (plik "winequality-red.csv"). Zamien wartosc zmiennej quality na
# binarna, przyjmujac, ze wina o jakosci 6 lub wyzszej sa wysokiej jakosci, a pozostale - niskiej jakosci.
# 

dane <- read.csv2('data/winequality-white.csv',  stringsAsFactors = FALSE, dec = '.')
if (typeof(dane$quality) == "integer") dane$quality <- ifelse(dane$quality >= 6, 'high', 'low')
## Uzycie warunku na typ zmiennej zabezpiecza nas przed zepsuciem danych
## w przypadku przypadkowego wywolania tej linijki wiecej niz 1 raz.
## Nie jest konieczne, ale czyni kod bezpieczniejszym.

## Inicjalizacja ziarna do zmiennych pseudolosowych
set.seed(1)

# Podziel zbior na uczacy i testowy losowo w proporcji 0.8:0.2.
# 
train_proportion <- 0.8
train_index <- runif(nrow(dane)) < train_proportion
train <- dane[train_index,]
test <- dane[!train_index,]

# Zbuduj drzewo klasfikacyjne przewidujce jakosc czerwonego wina na podstawie jego parametrow chemicznych.
# Przyjmij na poczatek parametr zlozonosci (complexity parameter) rowny 0.005. Zwizualizuj drzewo.

cp_start <- 0.005 ## dobra praktyka jest wypisywanie zalozen wprost, w pomocnicznych zmiennych,
## jeszcze przed wywolaniem funkcji

library(rpart)
library(rpart.plot)
d.klas <- rpart(quality~., data = train, method = "class", cp = cp_start)
rpart.plot(d.klas, under=FALSE, fallen.leaves = FALSE, cex = 0.3)

# Narysuj wykres bledu w zaleznosci od wielkosci drzewa. 
# Czerwoną kropką oznacz na wykresie wielkosc drzewa o minimalnym bledzie.
# 

plotcp(d.klas)
min.error <- which.min(d.klas$cptable[,"xerror"])
opt.cp <- d.klas$cptable[min.error,"CP"]
points(min.error, d.klas$cptable[min.error, "xerror"], pch = 19, col = "red")

# Zbuduj nowe drzewo powstale przez przyciecie poprzedniego drzewa do wartosci optymalnego parametru zlozonosci.
# 

d.klas.przyciete <- prune.rpart(d.klas, cp = opt.cp)
rpart.plot(d.klas.przyciete, under=FALSE, fallen.leaves = FALSE, cex = 0.5)

# Policz macierze klasyfikacji dla obu drzew.

CM <- list()
CM[["d.klas"]] <- table(predict(d.klas, new = test, type = "class"), test$quality)
CM[["d.klas.przyciete"]] <- table(predict(d.klas.przyciete, new = test, type = "class"), test$quality)

# Na postawie macierzy klasyfikacji policz dla obu drzew accuracy, sensitivity i specificity.

## Uzywajac funkcji napisanej w zadaniu 1:

lapply(CM, EvaluateModel) # lapply stosuje funkcje po kolei do kazdego elementu listy i zwraca liste wynikow

# Narysuj krzywa ROC i lift oraz policz AUC dla obu drzew.

## Zamiast pisac dwa razy to samo, wygodniej bedzie napisac funkcje, ktora to robi w sposob ogolny,
## i zastosowac ja do obu drzew.

library(ROCR) # do krzywej ROC

EvaluateTree <- function(tree_model, data_set, response_column_name)
{
  prognoza_ciagla <- predict(tree_model, newdata = data_set)
  prognoza_ciagla <- as.vector(prognoza_ciagla[,2])
  
  # krzywa ROC - potrzebuje "ciaglej" prognozy
  plot(performance(prediction(prognoza_ciagla, data_set[[response_column_name]]),"tpr","fpr"),lwd=2, colorize=T) 
  
  # AUC (Area Under Curve) - pole pod krzywa ROC
  print(performance(prediction(prognoza_ciagla, data_set[[response_column_name]]),"auc"))
  
  # Sensitivity/specificity plots ~ trade-off
  plot(performance(prediction(prognoza_ciagla, data_set[[response_column_name]]),"sens","spec"),lwd=2) 
  
  # Lift chart
  plot(performance(prediction(prognoza_ciagla, data_set[[response_column_name]]),"lift","rpp"),lwd=2, 
       col = "darkblue") 
}

EvaluateTree(tree_model = d.klas, data_set = test, response_column_name = "quality")
EvaluateTree(tree_model = d.klas.przyciete, data_set = test, response_column_name = "quality")

# Za kazdym wywolaniem powstaje kilka wykresow, ale widac tylko ostatni.
# Wczesniejsze mozna obejrzec, uzywajac strzalki wstecz nad wykresem.

#Ćwiczenia 6

data <- na.omit(data)
data <- select(data, age, workclass,education, income, maritalStatus, occupation, capitalGain,
               capitalLoss, hourPerWeek, nativeCountry, race,sex, relationship)

if (any(data$income == "<=50K")) data$income <- ifelse(data$income == "<=50K", "low", "high")
# Uzycie instrukcji warunkowej nie jest niezbedne,
# ale chroni nas przed zepsuciem danych w sytuacji przypadkowego wywolania tej linijki
# wiecej, niz jeden raz.

table(data$income)

data <- mutate(data, 
               income = factor(income),
               workclass = factor(workclass),
               education = factor(education), 
               maritalStatus = factor(maritalStatus),
               occupation = factor(occupation),
               nativeCountry = factor(nativeCountry), 
               race = factor(race),
               sex = factor(sex), 
               relationship = factor(relationship)
)

# Podzial zbioru na uczacy i testowy
train_dataset_proportion <- 0.8
train_index <- (runif(nrow(data), 0, 1) <= train_dataset_proportion)

train <- data[train_index, ]
test <- data[!train_index, ]

# Budowa (hodowla?) lasu losowego
rf <- randomForest(income ~., data = train)

# Uzyteczne parametry:
# ntree - liczba drzew
# mtry - liczba zmiennych do losowego próbkowania jako kandydaci przy każdym podziale

varImpPlot(rf)

# Ocena modelu 

# Funkcja ponizej to rozwiazanie zadania 1) z zajec numer 5:
EvaluateModel <- function(classif_mx)
{
  # Sciagawka: https://en.wikipedia.org/wiki/Sensitivity_and_specificity#Confusion_matrix
  true_positive <- classif_mx[1,1]
  true_negative <- classif_mx[2,2]
  condition_positive <- sum(classif_mx[ ,1])
  condition_negative <- sum(classif_mx[ ,2])
  # Uzywanie zmiennych pomocniczych o sensownych nazwach
  # ulatwia zrozumienie, co sie dzieje w funkcji
  accuracy <- (true_positive + true_negative) / sum(classif_mx)
  sensitivity <- true_positive / condition_positive
  specificity <- true_negative / condition_negative
  return(list(accuracy = accuracy, 
              sensitivity = sensitivity,
              specificity = specificity))
  # Notacja "accuracy = accuracy" itd. jest potrzebna,
  # zeby elementy listy mialy nazwy.
}

rf_classif_mx <- table(predict(rf, new = test, type = "class"), test$income)
EvaluateModel(rf_classif_mx)

# Dla porownania: drzewo klasyfikacyjne (powtorzenie z poprzednich zajec)

dtree <- rpart(income ~., data = train,  method = "class")
dtree_classif_mx <- table(predict(dtree, new = test, type = "class"), test$income)
EvaluateModel(dtree_classif_mx)

# Ale jakie AUC dla drzewa?
prognoza_ciagla <- predict(dtree, newdata = test)
prognoza_ciagla <- as.vector(prognoza_ciagla[,2])
performance(prediction(prognoza_ciagla, test[["income"]]),"auc")

# A jakie bedzie dla lasu losowego?

## wykresy diagnostyczne - znow powtorka

forecast <- predict(rf, newdata = test, type = "prob")[,2]
plottingData <- prediction(forecast, test$income)

# krzywa ROC - potrzebuje "ciaglej" prognozy
plot(performance(plottingData,"tpr","fpr"),lwd=2, colorize=T) 

#AUC (Area Under Curve) - pole pod krzywa ROC
performance(plottingData,"auc")@y.values[[1]]
# skladnia obiektowa: @ zamiast $, [[1]] do wyciagniecia elementu z listy

# Sensitivity/specificity plots ~ trade-off
plot(performance(plottingData ,"sens","spec"),lwd=2) 

# Lift chart
plot(performance(plottingData ,"lift","rpp"),lwd=2, col = "darkblue") 


################################################################################
### Pakiet caret - na przykladzie drzewa klasyfikacyjnego 
################################################################################

# http://topepo.github.io/caret/index.html

library(caret)

set.seed(1)

## podzial na zbior testowy i uczacy
inTraining <- createDataPartition(data$income, p = .8, list = FALSE)
training <- data[ inTraining,]
#training  <- na.omit(training) # gdybysmy wczesniej nie usuneli z calego zbioru
testing  <- data[-inTraining,]

## budowa modelu na zbiorze uczacym - na poczatek okreslamy sposob uczenia

## 5-krotna walidacja krzyzowa
fitControl <- trainControl(
  method = "cv",
  number = 5)

# Najpierw proste drzewo z CV
treeCaret_simple <- train(income ~ ., data = training, 
                          method = "rpart", 
                          trControl = fitControl)

plot(treeCaret_simple)
rpart.plot(treeCaret_simple$finalModel)

# Ewaluacja
confusionMatrix(data = predict(treeCaret_simple, testing), reference = testing$income, mode = "everything")

# Teraz recznie zadajemy zbior wartosci parametru zlozonosci do przeszukania
rpartGrid <- expand.grid(cp = seq(0.001, 0.1, by = 0.005))

treeCaret <- train(income ~ ., data = training, 
                   method = "rpart", 
                   trControl = fitControl,
                   tuneGrid = rpartGrid)
treeCaret
# https://en.wikipedia.org/wiki/Cohen%27s_kappa
plot(treeCaret)
rpart.plot(treeCaret$finalModel)

# Ewaluacja
confusionMatrix(data = predict(treeCaret, testing), reference = testing$income, mode = "everything")

# Zadanie 1
################################################################################

# Uzupelnij skrypt z cwiczen 5 (przewidywanie jakosci bialego wina na podstawie jego
# parametrow chemicznych) o model lasu losowego. Porownaj rozne metryki jakosci
# tego modelu do analogicznych metryk jakosci modeli uzywanych na cwiczeniach 5.

library(randomForest)

################################################################################
# Regresja - liczbowa zmienna przewidywana
################################################################################

dane <- read.csv2('data/winequality-white.csv',  stringsAsFactors = FALSE, dec = '.')

set.seed(1)
train_proportion <- 0.7
train_index <- runif(nrow(dane)) < train_proportion
train <- dane[train_index,]
test <- dane[!train_index,]

rf_reg <- randomForest(quality ~., data = train)

# Ocena lasu losowego regresji
varImpPlot(rf_reg)

OcenaModeli <- function(modele, dane, predicted_col_name) {
  
  print("Suma kwadatow reszt RSS")
  print(sapply(modele, function(x) sum((dane[[predicted_col_name]] - predict(x, dane))^2) ))
  
  print("Średni błąd absolutny MAE")
  print(sapply(modele, function(x) sum(abs((dane[[predicted_col_name]] - predict(x, dane))))/nrow(dane) ))
  
  print("Pierwiastek błędu średniokwadratowego RMSE")
  print(sapply(modele, function(x) sqrt(sum((dane[[predicted_col_name]] - predict(x, dane))^2)/nrow(dane)) ))
  
  print("Względny błąd absolutny RAE")
  print(sapply(modele, function(x) sum(abs((dane[[predicted_col_name]] - predict(x, dane))))/sum(abs(dane[[predicted_col_name]] - mean(dane[[predicted_col_name]]))) ))
  
  print("Pierwiastek Względnego błędu średniokw RRSE")
  print(sapply(modele, function(x) sqrt(sum((dane[[predicted_col_name]] - predict(x, dane))^2)/sum((dane[[predicted_col_name]] - mean(dane[[predicted_col_name]]))^2)) ))
  
}

OcenaModeli(list(rf_reg), train, 'quality')
OcenaModeli(list(rf_reg), test, 'quality')

################################################################################
# Klasyfikacja - czynnikowa, dwuwartościowa zmienna przewidywana
################################################################################

dane <- read.csv2('data/winequality-white.csv',  stringsAsFactors = FALSE, dec = '.')

# Zamiana jakosci na zmienna o 2 wartosciach
dane$quality <- ifelse(dane$quality >= 6, 'high', 'low')

# Zamiana jakosci na zmienna typu czynnikowego
dane$quality <- as.factor(dane$quality)

set.seed(1)
train_proportion <- 0.7
train_index <- runif(nrow(dane)) < train_proportion
train <- dane[train_index,]
test <- dane[!train_index,]

rf_class <- randomForest(quality ~., data = train)
cm <- table(predict(rf_class, new = test, type = "class"), test$quality)

EvaluateModel <- function(classif_mx)
{
  # Sciagawka: https://en.wikipedia.org/wiki/Sensitivity_and_specificity#Confusion_matrix
  true_positive <- classif_mx[1,1]
  true_negative <- classif_mx[2,2]
  condition_positive <- sum(classif_mx[ ,1])
  condition_negative <- sum(classif_mx[ ,2])
  # Uzywanie zmiennych pomocniczych o sensownych nazwach
  # ulatwia zrozumienie, co sie dzieje w funkcji
  accuracy <- (true_positive + true_negative) / sum(classif_mx)
  sensitivity <- true_positive / condition_positive
  specificity <- true_negative / condition_negative
  return(list(accuracy = accuracy, 
              sensitivity = sensitivity,
              specificity = specificity))
  # Notacja "accuracy = accuracy" itd. jest potrzebna,
  # zeby elementy listy mialy nazwy.
}

EvaluateModel(cm)

library(ROCR) # do krzywej ROC

prognoza_ciagla <- predict(rf_class, newdata = test, type = "prob")
# trzeba podac type = "prob", bo dla lasu losowego domyslnie zwracal przewidywana klase
prognoza_ciagla <- as.vector(prognoza_ciagla[,2])

# krzywa ROC - potrzebuje "ciaglej" prognozy
plot(performance(prediction(prognoza_ciagla,test$quality),"tpr","fpr"),lwd=2, colorize=T) 

# AUC (Area Under Curve) - pole pod krzywa ROC
performance(prediction(prognoza_ciagla, test$quality),"auc")

# Sensitivity/specificity plots ~ trade-off
plot(performance(prediction(prognoza_ciagla,test$quality),"sens","spec"),lwd=2) 

# Lift chart
plot(performance(prediction(prognoza_ciagla,test$quality),"lift","rpp"),lwd=2, col = "darkblue") 
#Lift is a measure of the effectiveness of a predictive model calculated 
#as the ratio between the results obtained with and without the predictive model. 


################################################################################
# Zadanie 2
################################################################################

# Uzywajac pakietu caret, zbuduj model drzewa klasyfikacyjnego 
# do przewidywania jakosci czerwonego wina. 
# Uzyj 3-krotnej walidacji krzyzowej. Pokaz jego metryki
# dla zbioru uczacego i testowego.
# Zbuduj kolejne drzewo, tym razem uzywajac 10-krotnej walidacji krzyzowej.
# Porownaj jego metryki (dla zbioru uczacego i testowego) z metrykami poprzedniego drzewa.

dane <- read.csv2('data/winequality-red.csv',  stringsAsFactors = FALSE, dec = '.')
if (typeof(dane$quality) == "integer") dane$quality <- ifelse(dane$quality >= 6, 'high', 'low')
## Uzycie warunku na typ zmiennej zabezpiecza nas przed zepsuciem danych
## w przypadku przypadkowego wywolania tej linijki wiecej niz 1 raz.
## Nie jest konieczne, ale czyni kod bezpieczniejszym.

library(caret)
set.seed(1)

## podzial na zbior testowy i uczacy
inTraining <- createDataPartition(dane$quality, p = .8, list = FALSE)
training <- dane[ inTraining,]
training  <- na.omit(training)
testing  <- dane[-inTraining,]

## 3-krotna walidacja krzyzowa
fitControl_3 <- trainControl(
  method = "cv",
  number = 3)

treeCaret_3 <- train(quality ~ ., data = training, 
                     method = "rpart", 
                     trControl = fitControl_3)

plot(treeCaret_3)
rpart.plot(treeCaret_3$finalModel)

# Ewaluacja
confusionMatrix(data = predict(treeCaret_3, training), reference = training$quality, mode = "everything")
confusionMatrix(data = predict(treeCaret_3, testing), reference = testing$quality, mode = "everything")

## 10-krotna walidacja krzyzowa
fitControl_10 <- trainControl(
  method = "cv",
  number = 10)

treeCaret_10 <- train(quality ~ ., data = training, 
                      method = "rpart", 
                      trControl = fitControl_10)

plot(treeCaret_10)
rpart.plot(treeCaret_10$finalModel)

# Ewaluacja
confusionMatrix(data = predict(treeCaret_10, training), reference = training$quality, mode = "everything")
confusionMatrix(data = predict(treeCaret_10, testing), reference = testing$quality, mode = "everything")

#Ćwiczenia 7

# Wczytanie danych o nazwach produktow i ich obrobka z uzyciem wyrazen regularnych
# (wyrazenia regularne nie obowiazuja na kolokwium)

goods_names <- readLines("data/EB-build-goods.sql")
goods_names <- gsub("^[a-zA-Z0-9 \\(]*,'", "", goods_names, fixed = FALSE)
goods_names <- gsub("','", " ", goods_names, fixed = FALSE)
goods_names <- gsub("'.*$", "", goods_names, fixed = FALSE)

# Wczytanie i eksploracja danych o transakcjach
df_all <- read.csv("data/75000-out2.csv", header = FALSE,
                   row.names = 1)

df <- df_all[1:40000, ] # wybieramy pierwsze 40000 transakcji

# Zamiana ramki danych na macierz i nadanie nazw kolumnom 
mx <- as.matrix(df)
colnames(mx) <- goods_names
ts <- as(mx, "transactions")

# Znajdowanie regul asocjacyjnych algorytmem apriori
rules = apriori(ts, parameter=list(support=0.01, confidence=0.5))

# Podglad regul
rules
inspect(head(sort(rules, by="lift"),3))

# Wizualizacja regul asocjacyjnych - rozne sposoby

plot(rules)
head(quality(rules));
plot(rules, measure=c("support","lift"), shading="confidence")
plot(rules, shading="order", control=list(main ="Two-key plot")) # order - liczba dobr w regule

# Wybor regul asocjacyjnych z najwieksza pewnoscia 

subrules = rules[quality(rules)$confidence > 0.9]
subrules

# Rozne sposoby wizualizacji
plot(subrules, measure=c("support","lift"), shading="confidence")
plot(subrules, shading="order", control=list(main ="Two-key plot"))
plot(subrules, method="matrix", shading="lift")
plot(subrules, method="matrix", shading="confidence")
plot(subrules, method="grouped")

# Wybor regul asocjacyjnych z najwiekszym liftem 
# i kolejne sposoby wizualizacji
subrules2 = head(sort(rules, by="lift"), 3)
plot(subrules2, method="graph")
plot(subrules2, method="paracoord")

oneRule = sample(rules, 1)
inspect(oneRule)

# Zadanie 1
################################################################################

# Wybierz ostatnie 30 000 transakcji z pliku 75000-out2.csv.
# Znajdz dla tych transakcji reguly asocjacyjne o minimalnym wsparciu 0.015
# i minimalnej pewnosci 0.6.
# Zwizualizuj:
# - zaleznosci pomiedzy lift, support i confidence dla znalezionych regul
# - macierz lewych i prawych stron regul z pokazana wartoscia lift
# 
# Wybierz sposrod znalezionych 4 reguly o najwyzszej pewnosci.
# Zwizualizuj je w postaci grafow.
# Wypisz w postaci tekstowej regule o najwyzszej pewnosci.

library("arules") # do znajdowania regul
library("arulesViz") # do wizualizacji regul

# Wczytanie danych o nazwach produktow i ich obrobka z uzyciem wyrazen regularnych
# (wyrazenia regularne nie obowiazuja na kolokwium)

goods_names <- readLines("data/EB-build-goods.sql")
goods_names <- gsub("^[a-zA-Z0-9 \\(]*,'", "", goods_names, fixed = FALSE)
goods_names <- gsub("','", " ", goods_names, fixed = FALSE)
goods_names <- gsub("'.*$", "", goods_names, fixed = FALSE)

# Wczytanie i eksploracja danych o transakcjach
df_all <- read.csv("data/75000-out2.csv", header = FALSE,
                   row.names = 1)

# Wybierz ostatnie 30 000 transakcji z pliku 75000-out2.csv.
df <- tail(df_all, 30000)

# Zamiana ramki danych na macierz i nadanie nazw kolumnom 
mx <- as.matrix(df)
colnames(mx) <- goods_names
ts <- as(mx, "transactions")

# Znajdz dla tych transakcji reguly asocjacyjne o minimalnym wsparciu 0.015
# i minimalnej pewnosci 0.6.
min_support <- 0.015
min_confidence <- 0.6

# Znajdowanie regul asocjacyjnych algorytmem apriori
rules = apriori(ts, parameter=list(support=min_support, confidence=min_confidence))

# - zaleznosci pomiedzy lift, support i confidence dla znalezionych regul
plot(rules, measure=c("support","lift"), shading="confidence") # mozna tez inaczej rozmiescic te miary na wykresie

# - macierz lewych i prawych stron regul z pokazana wartoscia lift
plot(rules, method="matrix", shading="lift")

# Wybierz sposrod znalezionych 4 reguly o najwyzszej pewnosci.
subrules = head(sort(rules, by="confidence", decreasing = TRUE), 4)

# Zwizualizuj je w postaci grafow.
plot(subrules2, method="graph")

# Wypisz w postaci tekstowej regule o najwyzszej pewnosci.
inspect(subrules[1])

################################################################################
# Zadanie 2
################################################################################

# Wykonaj clustering roslin ze zbioru danych iris
# uzywajac wymiarow lisci (sepal) zamiast kwiatow (petal).
# Zwizualizuj wyniki. Jak dobrze odkryte grupy pokrywaja sie z naturalnym
# podzialem na gatunki?

# Wykonaj i zwizualizuj analogiczne grupowanie, tym razem uzywajac wszystkich
# dostepnych informacji o wymiarach roslin. Czy poprawilo to wyniki?

head(iris)

# uzywajac wymiarow lisci (sepal) zamiast kwiatow (petal).

irisCluster_sepal <- kmeans(iris[, 1:2], centers = 3, nstart = 10)
iris$Cluster_sepal <- as.factor(irisCluster_sepal$cluster)
ggplot(iris, aes(Sepal.Length, Sepal.Width, color = Species, shape = Cluster_sepal)) + geom_point()

#uzywajac wszystkich dostepnych informacji o wymiarach roslin.

irisCluster_all <- kmeans(iris[, 1:4], centers = 3, nstart = 10)
iris$Cluster_all <- as.factor(irisCluster_all$cluster)
ggplot(iris, aes(Sepal.Length, Sepal.Width, color = Species, shape = Cluster_all)) + geom_point()
ggplot(iris, aes(Petal.Length, Petal.Width, color = Species, shape = Cluster_all)) + geom_point()

table(iris$Cluster_sepal, iris$Species)
table(iris$Cluster_all,  iris$Species)

# Czy poprawilo to wyniki?
# Wzgledem Cluster_sepal - tak.


