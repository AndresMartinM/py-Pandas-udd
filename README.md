# Guía de uso de python-pandas
guía de uso de pandas para el análisis del censo.

Para usar python y pandas se usará la plataforma online Google Colab: [https://colab.research.google.com/](https://colab.research.google.com). Esta permite la ejecución de código python desde la nube, por lo que se puede usar en cualguier dispositivo con navegador web.

## Primeros pasos

Tras abrir Google Colab hay que crear un nuevo notebook en el que se desarrollará el análisis, dentro el entorno es parecido al de Google Docs, arriba se muestra el nomre del archivo (haciendo click en él se puede cambiar), hay una nube que indica si el archivo está guardado, también esta la barra de opciones; y ya más abajo debería aparecer una celda de código (con un ícono de *play*); existen 2 tipos de celdas, las de código y las de texto, estas se pueden agregar con el botón del menú de opciones o con los botones que aparecen al poner el cursor bajo una celda. En cada celda de código se puede escribir y ejecutar python.

Como primer paso para comenzar a trabajar con Pandas, hay que traer la biblioteca de código 'pandas', esto se hace con la siguiente línea de código:

``` py
import pandas as pd
```

Luego lo adecuado sería comenzar a declarar variables relacionadas a los datos que se usarán, las indicaciones para ello están en los siguientes puntos Datos y Variables.

## Datos

Las tablas estadísticas con los resultados del censo 2024 se encuentran disponibles en la página del censo dispuesta por el INE, además están respaldadas en este repositorio. Cada archivo está en los links a continuación para su uso en Google Colab.

**Población censada por sexo y edad en grupos quinquenales:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/D1_Poblacion-censada-por-sexo-y-edad-en-grupos-quinquenales.xlsx 
```
**Índice de envejecimiento por sexo:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/D2_Indice-de-envejecimiento-por-sexo.xlsx
```
**Población censada por tipo de operativo:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/D3_Poblacion-censada-por-tipo-de-operativo.xlsx
```
**Inmigración internacional:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/D4_Inmigracion-Internacional.xlsx
```
**Migración interna:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/D5_Migracion-interna.xlsx
```
**Fecundidad:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/D6_Fecundidad.xlsx
```
**Servicios básicos, hogar y tenencia de vivienda:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/H1_Servicios-basicos-hogar-y-tenencia-vivienda.xlsx
```
**Discapacidad:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/P1-Discapacidad.xlsx
```
**Pueblos indígenas:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/P2-Pueblos-indigenas.xlsx
```
**Lenguas indígenas:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/P3_Lenguas-indigenas.xlsx
```
**Afrodecendencia:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/P4-Afrodescendencia.xlsx
```
**Género:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/P5_Genero.xlsx
```
**Religión o credo:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/P6_Religion-o-credo.xlsx
```
**Educación:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/P7_Educacion.xlsx
```
**Escolaridad en población inmigrante internacional:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/P8-Escolaridad-poblacion-inmigrante-internacional.xlsx
```
**Viviendas y hogares censados:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/V1_Viviendas-y-hogares-censados.xlsx
```
**Características de vivienda y viviendas irrecuperables:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/V2_Caracteristicas-vivienda-y-viv-irrecuperables.xlsx
```
**Número de dormitorios, hacinamiento y viviendas con más de un hogar:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/V3_N-de-dormitorios-hacinamiento-y-viv-con-mas-de-un-hogar.xlsx
```
**Servicios básicos de la vivienda:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/V4_Servicios_basicos_de_la_vivienda.xlsx
```
**Tipologías de viviendas censadas:**
```
https://github.com/exploratec-udd/py-Pandas/raw/refs/heads/main/xlsx/V5_Tipologias-de-viviendas-censadas.xlsx
```

**[Fuente Censo 2024 INE](https://censo2024.ine.gob.cl/estadisticas/)**

Para usar estos datos en la plataforma de Google Colab se debe copiar el vínculo de la tabla que se quiera usar, e ingresarlo de la siguiente forma:

``` py
pd.read_excel("aquí el link entre comillas", sheet_name='1', header=3, index_col='Código región')
```

Ahí en `sheet_name` se pone el nombre de la hoja que se va a usar, `header` sirve para escoger la fila en que comienza la tabla (en el caso de las tablas del censo es la fila 3), en `index_col` se pone el nombre de la cabecera de la colúmna que se quiera usar como índice, en este caso se usa la colúmna 'Código región'.

## Variables

Para la agilización del uso de pandas se recomienda darle un nombre de variable a cada tabla con la que se vaya a trabajar (usualmente llamadas *data frames*), para ello se usa la siguiente estructura:

``` py
dfNombre = pd.read_excel("aquí el link entre comillas", sheet_name='1', header=3, index_col='Código región')
```

Se recomienda usar el prefijo df en el nombre de la variable para indicar que es un *data frame* de pandas, luego se usa la función `read_excel()` para leer el archivo que se vaya a usar (como se explica en el punto anterior), esto permitirá más adelante usar el nombre de la variable `dfNombre` para acceder a los datos de la tabla. En el caso de trabajar con más de una *data frame* se pueden declarar múltiples variables en el principio para luego usarlas.

``` py
title = 'Nombre columna'

columnas = ['Columna1', 'Columna2', 'Columna3']
```

También se pueden declarar variables de otros tipos para por ejemplo guardar el valor de una o múltiples cabeceras de colúmna que se vaya a usar como aparece arriba, o un valor dentro de una tabla, o una porción de una tabla, etc. Varias de las funciones que se podrían usar para esto se recopilan en la siguiente sección.


## Funciones

Pandas cuenta con funciones para la lectura y exportación de archivos de datos, y sobre todo para el análisis de estos datos. Para su suso se recomienda estudiar la documentación de la página web de pandas ([**documentación de Pandas**](https://pandas.pydata.org/docs/reference/index.html)). De todas maneras a continuación hay un resumen de las principales funciones:

### Funciones *read*

Pandas tiene funciones para leer distintos tipos de archivo, aunque en esta guía se usa `read_excel()` hay otras que conviene conocer:

``` py
# para leer .xlsx
pd.read_excel()

# para leer .csv
pd.read_csv()

# para leer .json
pd.read_json()

# para leer .xml
pd.read_xml()
```

### Funciones de orden

Para ordenar los datos hay un par de funciones que conviene conocer, la primera de ellas `sort_index()` ordena los datos de acuerdo al valor del índice de la tabla (para ello es importante que no hayan valores de índice repetidos).

``` py
dfNombre.sort_index()
```

La siguiente función `sort_values()` permite ordenar una tabla de acuerdo a los valores de una o más columnas, de manera ascendente o descendente.

``` py
# orden ascendente según los valores de la columna
dfNombre.sort_values(by=['Nombre columna'])

# orden descendente según los valores de la columna
dfNombre.sort_values(by=['Nombre columna'], ascending=False)
```

La siguiente función `groupby()` agrupa las filas según los valores de una de las columnas, esto puede ser útil cuando hay valores cualitativos o que permiten una clasificación.

``` py
dfNombre.groupby(by='Nombre columna')
```

### Funciones de filtrado

Para ver de forma parcial los datos, hay varias opciones de filtrado, la más simple es la que nos permite ver solo una columna de la tabla es de la siguiente forma:

``` py
# muestra la columna seleccionada
dfNombre['Nombre columna']

# muestra la columna seleccionada (solo funciona con nombres de columnas sin espacios)
dfNombre.columna
```

Eso por el lado de las colúmnas, pero tambien se pueden filtrar filas según los valores que tengan en una columna. 

``` py
# la tabla solo con las filas que tengan un valor mayor o igual a 100 en la Columna1
dfNombre[dfNombre['Columna1'] >= 100]

# la tabla solo con las filas con el valor 'Mujer' en la Columna2 
dfNombre[dfNombre.Columna2 == 'Mujer']
```

Por último la función `filter()` permite filtrar considerando múltiples variables, en el siguiente ejemplo se usa para ver únicamente la 2 columnas.

``` py
dfNombre.filter(items=['Columna1', 'Columna2'])
```

Cabe decir que todas estas funciones se pueden combinar.

### Funciones estadísticas

Para obtener resultados estadísticos se pueden usar el siguiente conjunto de funciones:

``` py
# el valor mínimo de la Columna1
dfNombre.Columna1.min()

# el valor de la mediana de Columna1
dfNombre.Columna1.median()

# el valor máximo de la Columna1
dfNombre.Columna1.max()

# el valor promedio o media aritmética de la Columna1
dfNombre.Columna1.mean()
```

También se pueden ver estos valores de manera agregada en una misma tabla usando la función `agg()`.

``` py
dfNombre.agg(['sum', 'max', 'min'])
```

Para ver los resultados estadísticos completos basta con usar la función `describe()`. 

``` py
dfNombre.describe()
```
---
Pandas cuenta con una función que permite conocer la correlación entre los datos, donde un valor cercano a 1 indica una correlación directa, un valor cercano a -1 una correlación inversa, y un valor cercano a 0 una no correlación.

``` py
# muestra la correlación entre los valores de la Columna1, Columna2 y Columna3
dfNombre.filter(items=['Columna1', 'Columna2', 'Columna3']).corr()
```

Sabiendo estas funciones ya se puede comenzar a analizar los datos de las tablas mezclándolas de la siguiente manera:

``` py
import pandas as pd

dfNombre1 = pd.read_excel("aquí el link entre comillas", sheet_name='1', header=3, index_col='Código región')

dfNombre2 = pd.read_excel("aquí el link entre comillas", sheet_name='2', header=3, index_col='Código región')

dfDatos1 = dfNombre1.filter(items=['Columna1', 'Columna6', 'Columna8'])

dfDatos2 = dfNombre2.filter(items=['Columna3', 'Columna4'])

dfDatos1.agg(['sum', 'max', 'min'])
```
Google Colab siempre mostrará los datos de la última línea ingresada en la celda de código, mientras no sea la declaración de una variable. Por lo que basta con poner algo del siguiente estilo para que entregue los valores solicitados luego de presionar `shift+Enter` o el botón de play al costado izquierdo:

``` py
dfDatos2.describe()
```

## Gráficos

Cada vez que Google Colab responde una celda de código con una tabla muestra la opción de generar tablas de manera automática, esta opción es bastante útil para entender los valores de la tabla de otra forma, pero al ser automáticas no se tiene mucho control de lo que se visualiza en ellas, por lo que es recomendable hacer tablas con ayuda de plotly ([Documentación de plotly](https://plotly.com/python/)). A continuación hay un pequeño ejemplo de como se usa:

``` py
import plotly.express as px
```
TODO

---

TODO
