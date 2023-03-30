# Unir archivos

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
import geopandas as gpd
import pandas as pd
import glob
```
