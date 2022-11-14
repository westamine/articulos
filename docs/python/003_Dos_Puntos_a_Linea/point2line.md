# Crear Linea a partir de 2 puntos

Para este ejemplo, necesitamos calcular la distancia de desplazamiento entre diferentes puntos. Contamos con 2 bases, original y desplazado, teniendo llave el campo ID.

* **Paso 1.**: Importar las librerias a utilizar

```python
from shapely.geometry import Point, LineString
import pandas as pd
import geopandas as gpd
import os
```
