# Estadística descriptiva con python

La estadística descriptiva es una rama fundamental de las matemáticas que se encarga de resumir y describir características importantes de un conjunto de datos. 

En el nivel más simple, la estadística descriptiva resume y describe características básicas pero esenciales de un conjunto de datos. Proporcionan una instantánea de las características de su conjunto de datos y permiten comprender mejor cómo es la "forma" de los datos. Por ejemplo, una estadística descriptiva podría incluir la proporción de hombres y mujeres dentro de una muestra o los porcentajes de diferentes grupos de edad dentro de una población. 

La estadística descriptiva ayuda a comprender las características clave de una muestra sin perderse en grandes cantidades de datos sin procesar y proporciona una base para su análisis. Además, permite identificar rápidamente problemas potenciales dentro de su conjunto de datos, por ejemplo, valores atípicos sospechosos, respuestas faltantes, etc. Igual de importante es que las estadísticas descriptivas informan el proceso de toma de decisiones cuando se trata de elegir qué estadísticas inferenciales se ejecutaran, ya que cada prueba inferencial tiene requisitos específicos con respecto al tipo de datos.

Entre las herramientas más utilizadas en este campo se encuentran las medidas de tendencia central y las medidas de varianza, que proporcionan información valiosa sobre la distribución y la dispersión de los datos. 

Las medidas de tendencia central describen el centro o la "sección media" de un conjunto de datos. En otras palabras, proporcionan alguna indicación de cómo se ve un punto de datos “típico” dentro de un conjunto de datos determinado. Las tres medidas más comunes son:
La media, que es el promedio matemático de un conjunto de números; en otras palabras, la suma de todos los números dividida por el recuento de todos los números.
    
La mediana, que es el número intermedio en un conjunto de números, cuando esos números están ordenados de menor a mayor.

La moda, que es el número que aparece con más frecuencia en un conjunto de números (en cualquier orden). Naturalmente, un conjunto de datos puede tener una moda, ninguna moda (ningún valor aparece más de una vez) o múltiples modas.

Veamos un ejemplo. En python podemos usar el paquete statistics que, ya incorporado.

    import statistics as stat
    edades = [21, 22, 30, 33, 21, 39, 29, 21, 29, 28, 31, 35]

    media = stat.mean(edades)
    mediana = stat.median(edades)
    moda = stat.mode(edades)

    print("Media: ", media, 
        "Mediana: ", mediana, 
        "Moda:", moda)

En caso de que necesitemos analizar un dataset o una matriz de datos, podemos usar pandas. De manera rapida podemos obtener la media y mediana así como otras medidas que van a complementar la información, como valor minimo, valor máximo y cuartiles.

    import pandas as pd

    df_salud = pd.read_excel("data_salud.xlsx")

    df_salud.describe()

En este caso no nos muestra la moda, pero podemos obtenerla mediante

    df_salud.mode()

A partir de los ouputs podemos ver, por ejemplo, que de esta muestra la persona más joven tiene 19 años, la más grande 70 y que el promedio de edad es de 42 años. También sabemos que es una muestra donde la mitad de las personas tiene 39 años o menos y que la edad que más se repite es 35 años. 
Si nos fijamos en la columna del dataset "fumador" es de tipo cualitativa, por lo que no podemos obtener medidas como la media o la mediana, pero si podemos obtener la moda, en este caso el valor que más se repite es "False".

Si bien las medidas de tendencia central brindan información sobre qué tan “centrado” está el conjunto de datos, también es importante comprender qué tan disperso está ese conjunto de datos. En otras palabras, hasta qué punto los datos se agrupan hacia el centro (específicamente, hacia la media). En algunos casos, la mayoría de los puntos de datos estarán muy cerca del centro, mientras que en otros casos estarán dispersos por todas partes. Las medidas de dispersión son:

Rango, que mide la diferencia entre el número más grande y el más pequeño del conjunto de datos. En otras palabras, indica cuán disperso está realmente el conjunto de datos.

Varianza, que mide cuánto varía cada número en un conjunto de datos con respecto a la media (promedio). Más técnicamente, calcula el promedio de las diferencias al cuadrado entre cada número y la media. Una varianza más alta indica que los puntos de datos están más dispersos, mientras que una varianza más baja sugiere que los puntos de datos están más cerca de la media.

Desviación estándar, que es la raíz cuadrada de la varianza. Tiene los mismos propósitos que la varianza, pero es un poco más fácil de interpretar ya que presenta una cifra que está en la misma unidad que los datos originales.

En el caso de pandas, podemos obtener estas medidas de una de las columnas del dataset de la siguiente manera

    rango = rango = df_salud['edad'].max() - df_salud['edad'].min()

    varianza = df_salud["edad"].var()

    des_estan = df_salud["edad"].std()

Como muestra el output, el rango de 51 refleja la diferencia entre la edad más alta y la edad más baja. La desviación estándar de 14,80 nos indica que, en promedio, los resultados dentro del conjunto de datos están a 14,80 de la media (de 39), lo que refleja un conjunto de datos relativamente disperso.

En resumen, el rango, la varianza y la desviación estándar proporcionan una indicación de cuán dispersos están los datos. Estas medidas son importantes porque le ayudan a interpretar las medidas de tendencia central dentro de su contexto. En otras palabras, si sus medidas de dispersión son todas cifras bastante altas, debe interpretar sus medidas de tendencia central con cierta cautela, ya que los resultados no están particularmente centrados. Por el contrario, si todos los datos están estrechamente agrupados alrededor de la media (es decir, baja dispersión), la media se convierte en una estadística mucho más “significativa”.


