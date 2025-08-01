# Guía de uso de python-pandas
guía de uso de pandas para el análisis del censo.

Para usar python y pandas se usará la plataforma online Google Colab: [https://colab.research.google.com/](https://colab.research.google.com).

## Primeros pasos

Tras abrir TODO

``` py
import pandas as pd
```

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

TODO

``` py
dfNombre.sort_index()
```

TODO

``` py
# orden ascendente según los valores de la columna
dfNombre.sort_values(by=['Nombre columna'])

# orden descendente según los valores de la columna
dfNombre.sort_values(by=['Nombre columna'], ascending=False)
```

TODO

``` py
dfNombre.groupby(by='Nombre columna')
```

### Funciones de filtrado

TODO

``` py
# muestra la columna seleccionada
dfNombre['Nombre columna']

# muestra la columna seleccionada (solo funciona con nombres de columnas sin espacios)
dfNombre.columna
```

TODO

``` py
# la tabla solo con las filas que tengan un valor mayor o igual a 100 en la Columna1
dfNombre[dfNombre['Columna1'] >= 100]

# la tabla solo con las filas con el valor 'Mujer' en la Columna2 
dfNombre[dfNombre.Columna2 == 'Mujer']
```

TODO

``` py
dfNombre.filter(items=['Columna1', 'Columna2'])
```

### Funciones estadísticas


``` py

```
``` py

```
``` py

```
``` py

```

## Gráficos
