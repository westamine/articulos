# Crear Linea a partir de 2 puntos

Para este ejemplo, necesitamos calcular la distancia de desplazamiento entre diferentes puntos. Contamos con 2 bases, original y desplazado, teniendo llave el campo ID.

* **Paso 1.**: Importar las librerias a utilizar

```python
from shapely.geometry import Point, LineString
import pandas as pd
import geopandas as gpd
import os
```

* **Paso 2.** Especificar la ruta de los archivos csv

```python
original = 'data/original.csv'
desplazado = 'data/desplazado.csv'
```

* **Paso 3.** Convertir a dataframe

```python
dfOrg = pd.read_csv(original, sep=';')
dfDpz = pd.read_csv(desplazado, sep=';')
```

Visualizamos los archivos:

```python
dfOrg.head(3)
```

![image](https://user-images.githubusercontent.com/88239150/201785553-b7868061-b7fe-43a7-bde1-d35f1d1190e3.png)


```python
dfDpz.head(3)
```

![image](https://user-images.githubusercontent.com/88239150/201785598-1c4505c2-28bb-492e-9060-72d7e3faf34c.png)

* **Paso 4.** Unir los dataframe por el campo `id`

```python
# Merge: Unir dataframes
dfMerge = dfOrg.merge(dfDpz, on='id', how='left', suffixes=('_org', '_dpz'))

# Visualizar resultados
dfMerge.head()
```

![image](https://user-images.githubusercontent.com/88239150/201786009-e85a65da-d839-496c-9147-cb2792e7ba00.png)

* **Paso 5.** Funcion para crear un objeto LineString Shapely a partir de un par de coordenadas.

```python
funLineString = lambda lon_org, lat_org, lon_dpz, lat_dpz: LineString([(lon_org, lat_org), (lon_dpz, lat_dpz)])
```

* **Paso 6.** Aplicar la función al dataframe

```python
dfMerge['geometry'] = dfMerge.apply(lambda row: funLineString(row['lon_org'],
                                                              row['lat_org'],
                                                              row['lon_dpz'], 
                                                              row['lat_dpz']
                                                             ),                                    
                                    axis=1)
```

* **Paso 7.** Calculamos la longitud, que sería la distancia entre ambos puntos.

