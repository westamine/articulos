# UNIR ARCHIVOS

Para el siguiente ejemplo vamos a unir archivos espaciales en formato **`.json`** ubicados en directorios diferentes:

```
* datos
  * lotes1
    * lotes_11000.json
    * lotes_12000.json
    * lotes_13000.json
    * ...
  * lotes2
    * lotes_100000.json
    * lotes_101000.json
    * lotes_102000.json
    * ...
  * lotes3
    * lotes_200000.json
    * lotes_201000.json
    * lotes_202000.json
  * ...  
```

![image](https://user-images.githubusercontent.com/88239150/228713934-4a102414-9cab-44fb-98b1-bf5209f3573c.png)

## 1. Importar módulos

Comenzaremos importando los siguientes módulos:

* **pandas**: para la manipulación y el análisis de datos
* **geopandas**: para la manipulación y análisis de datos espaciales 
* **glob**: para econtrar los nombres de rutas que se asemejan a un patrón especificado

```python
# Importando módulos
import geopandas as gpd
import pandas as pd
import glob
```

## 2. Lectura de la ruta de los archivos

Mediante el módulo **`glob`** buscaremos los nombres de rutas que se asemejan al siguiente patron:

```python
# Guardar la ruta de todos los archivos que terminen en .json
# dentro del directorio "datos":
archivos = glob.glob('datos/**/*.json', recursive=True)
```

Podemos verificar que la variable **`archivos`** es de tipo lista

```python
type(archivos)
```

![image](https://user-images.githubusercontent.com/88239150/228715200-503d1cd8-2f05-4590-b20f-fe4a5290b8ac.png)

Tambien contaremos la cantidad de elementos que tiene la lista:

```python
len(archivos)
```

![image](https://user-images.githubusercontent.com/88239150/228715316-412954d6-1dec-4bfb-874e-7107252fab10.png)


Y por último imprimiremos una muestra para verificar que los elementos guardados en la lista sean las rutas de los archivos **`.json`**

```python
for archivo in archivos[0:5]:
    print(archivo)
```

![image](https://user-images.githubusercontent.com/88239150/228715547-42d89991-3575-41f1-bb25-2f251b16b357.png)

## 3. Unión de los archivos

Como siguiente paso vamos a recorrer todas las rutas, convertirlos en `GeoDataFrame` y concatenarlas en un solo `GeoDataFrame`

```python
# Bucle para recorrer todas las rutas, convertirlos en geodataframe y unirlos
dfConsolidado = gpd.GeoDataFrame()  # GeoDataFrame donde se almacenará el resultado
for archivo in archivos:
    df = gpd.read_file(archivo, encoding='UTF-8')
    dfConsolidado = pd.concat([dfConsolidado, df])
```

