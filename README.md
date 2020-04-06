Tarea de programacion numero 3
================

``` r
library(tidyverse)
vocales = read_csv("data/vowel_data.csv")
```

## Cifras

Promedio y desviacion estandar de primer formante (f1), segundo formante
(f2), y longitud de trayecto (tl)

``` r
vocales %>%
    summarise(promedio_f1 = mean(f1_cent), de_f1 = sd(f1_cent), promedio_f2 = mean(f2_cent), de_f2 = sd(f2_cent),  promedio_tl = mean(tl), ds_tl = sd(tl)) 
```

    ## # A tibble: 1 x 6
    ##   promedio_f1 de_f1 promedio_f2 de_f2 promedio_tl ds_tl
    ##         <dbl> <dbl>       <dbl> <dbl>       <dbl> <dbl>
    ## 1        525.  227.       1701.  582.        424.  970.

## Graficas

### Longitud de trayecto de vocales en funcion de lengua:

``` r
  ggplot(vocales, aes(fill= language, y=tl, x=vowel)) + 
  geom_bar(position="dodge", stat="identity")
```

![](README_files/figure-gfm/unnamed-chunk-3-1.png)<!-- -->

### Primer formante de vocales en funcion de vocal y lengua

``` r
ggplot(vocales, aes(fill= language, y=f1_cent, x=vowel)) + 
  geom_bar(position="dodge", stat="identity")
```

![](README_files/figure-gfm/unnamed-chunk-4-1.png)<!-- -->

### Segundo formante de vocales en funcion de vocal y lengua

``` r
ggplot(vocales, aes(fill= language, y=f2_cent, x=vowel)) + 
geom_bar(position="dodge", stat="identity")
```

![](README_files/figure-gfm/unnamed-chunk-5-1.png)<!-- -->

## Preguntas

1.  El codigo sirve para darnos una idea de como una vocal evoluciona en
    diferentes momentos de su articulacion. Para hacerlo, es necesario
    entender donde empieza y donde termina la vocal dentro del estimulo
    grabado. Despues, se puede programar un codigo que mide los valores
    formanticos en diferentes momentos dados (i.e. 20% de la duracion
    total de la vocal) para ver como progresa a traves de su produccion.
    Este tipo de calculacion ofrece mas informacion sobre la variacion
    en la produccion de vocales entre lenguas, dialectos, y hablantes,
    ya que lo tipico es medir el centroide, una medida que no ilustra de
    manera completa como las propiedades acusticas de una vocal cambian
    a traves de su duracion.

2.  Hay tres partes del script. La primera parte se trata de buscar el
    estimulo en el directorio que hicimos en RStudio al inicio del
    proyecto, y crear un archivo de CSV – es decir, sirvio para que
    concretaramos el input y el output para el resto del script. Tambien
    concretamos las columnas que ibamos a utilizar. La segunda parte fue
    el codigo necesario para sacar la informacion del textgrid de PRAAT
    y entregar los datos en las columnas relevantes del CSV para una de
    las vocales del estimulo. Por ultimo, la tercera parte del script
    sirvio para que el proceso se repitiera con los demas estimulos
    segun se hizo en la parte anterior. Con estas tres partes,
    conseguimos localizar la fuente de datos (nuestro estimulo en forma
    de textgrid) y sacar los datos del estimulo para que se
    representasen en un archivo CSV. Despues, nos fue posible analizar y
    manipular estos datos en RStudio.

3.  En la tarea anterior, medimos el punto medio de la vocal mediante el
    point tier, y esta semana, usamos el point tear para congretar la
    lengua del estimulo. En el estimulo de la tarea de programacion
    numero 2, generamos datos para la intensidad, la duracion, y el
    tono, y calculamos nuestros datos en funcion de la acentuacion
    (llana o aguda). Sin embargo, esta vez creamos funciones para la
    lengua y la vocal (a i u). La ventaja de calcular la longitud del
    trayecto es el fenomeno que he explicado en la pregunta \#1 (es
    mejor dar una vista mas completa de la progresion de la vocal en vez
    de los valores de tono/intonacion a su centroide), pero la
    desventaja es que no medimos la acentuacion, el tono, y la
    intonacion de nuestras vocales. Es decir, buscamos diferentes
    variables: la primera tarea fue mas general, pero dentro de la
    duracion, conseguimos demostrar como las vocales progresan por el
    tiempo mediante el uso de la longitud de trayecto. Una ultima
    diferencia es que calcamos la desviacion estandar ademas del
    promedio en la tarea numero 3, pero no en la 2.