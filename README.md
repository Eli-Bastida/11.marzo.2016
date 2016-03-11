# 11.marzo.2016
simulación de series de datos y comparación con datos reales

### 11 de marzo de 2016 ###

## 1-. simular datos
## 2.- bajar del inegi base para convertir con st
## 3.- st multiples
## todas las graficas con formato

## en este ejemplo vamos a poner la poblacion en mexico que el valor 
## minimo seran 100, max 120, 15 datos que inicie en 2000

pob <- sample(100:120, 15, replace= FALSE) ##generar datos aleatorios
## la convertimos en serie de tiempo
pobts <- ts (pob, frequency = 1, start = (2000)) ## star: cuando comienza
plot(pobts) ## darle formato
plot(aggregate(pobts)) ## tendencia
plot(pobts, main = "poblacion (tendencia)", xlab = "año", ylab = "habitantes")

#### bajar del inegi la ocupacion de las personas.... (infolab)
## transponer los datos a columna
## importar csv

ocupa <- ts (read.csv(("C:\\Users\\SALA-C9\\Desktop\\IndicadoresENOE_2016-03-11.csv")), frequency = 4, start = 2005)
plot(ocupa, main = "porcentaje de poblacion ocupada", xlab = "año", ylab = "numero de habitantes ocupados")
plot(aggregate(ocupa), main = "porcentaje de poblacion ocupada", xlab = "año", ylab = "numero de habitantes ocupados")


### ejercicio ##
# simular la tasa de desocupacion de 3% a 8%, 2005, 40 datos, trimestral
# bajar INEGI tasa desocupacion, importar en R 
# comparar la simulacion con INEGI

tasades <- sample(3:8, 44, replace= TRUE) ##generar datos aleatorios
tasadests <- ts (tasades, frequency = 4, start = (2005)) ## star: cuando comienza, frecuencia 4 por los trimestres
tasadests
plot(tasadests, main = "Tasa de Desocupación", xlab = "Año", ylab = "Porcentaje")
plot(aggregate(pobts), main = "Tasa de Desocupación", xlab = "Año", ylab = "Porcentaje") ## tendencia

##INEGI
inegi <- ts (read.csv(("C:\\Users\\SALA-C9\\Desktop\\TASASDES.csv")), frequency = 4, start = 2005)
plot(inegi, main = "Tasa de Desocupación", xlab = "año", ylab = "Porcentaje")
plot(aggregate(inegi), main =  "Tasa de Desocupación", xlab = "año", ylab = "Porcentaje")
inegi

## para ver las dos graficas
plot (cbind(tasadests, inegi),main = "Tasa de Desocupación", xlab = "Año", ylab = "Porcentaje", col= "GREEN" )
