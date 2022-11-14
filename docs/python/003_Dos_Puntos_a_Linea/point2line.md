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
# Ruta de los archivos csv
original = 'data/original.csv'
desplazado = 'data/deplazado.csv'
```

* **Paso 3.** Convertir a dataframe

* **Paso 4.** Unir los dataframe por el campo ID

* **Paso 5*.** Funcion para crear un objeto Punto Shapely

* **Paso 6.** Funcion para crear un objeto LineString Shapely

* **Paso 7.** Calculamos la longitud, que sería la distancia entre ambos puntos.

