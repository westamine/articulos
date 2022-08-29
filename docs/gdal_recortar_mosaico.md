# Recortar un mosaico de imagenes con GDAL

Hace poco en un grupo de SIG lei un post donde preguntaban como recortar un mosaico de gran tamamaño de forma eficiente. El usuario indicaba que al tratar de realizar este proceso desde un SIG de escritorio el proceso tardaba horas e incluso dias sin ejecutarse.

Existen muchas formas eficientes de abordar este problema, como usar softwares especializados en el procesamiento de imagenes satelitales. Sin embargo, en este tutorial abordaremos el uso de la biblioteca GDAL como alternativa de solución a este problema.

## ¿Porqué usar GDAL?

GDAL/OGR es una biblioteca traductora para formatos de datos geoespaciales, que además proporciona un conjunto de herramientas para el tratamiento de estos datos. Se publica bajo una licencia de código abierto de estilo MIT por parte de la Fundación Geoespacial de Código Abierto (OSGEO).

A continuación se detallan los motivos para utilizar GDAL:

* Procesar datos Geospaciales de manera eficiente.
* Repetir los pasos de procesamiento para diferentes conjuntos de datos.

## Fuente de datos

Para el desarrollo de este tutorial se utilizaron las imagenes ASTER GDEM de descarga de gratuita, desde los geoservidores del Ministerio del Ambiente de Perú (MINAM). Puedes realizar la descarga del siguiente [link](https://geoservidorperu.minam.gob.pe/geoservidor/download_raster.aspx)

## Empezemos...

Como primer paso debemos guardar todas las imagenes en una carpeta de trabajo

![image](https://user-images.githubusercontent.com/88239150/187310580-223a2d50-6d87-46ed-b39a-bd4d274d1d1c.png)

Accederemos a esta carpeta utilizando el simbolo del sistema de windows (cmd)

```
>D:
>cd <ruta_de_la_carpeta>
```
![image](https://user-images.githubusercontent.com/88239150/187311414-a384a806-f2f0-4fad-be21-17f8d038c03d.png)


Inspeccionaremos las imagenes con `gdalinfo` para comprobar que tengan las misma carácteristicas como: El número de bandas (1 porque son DEM), sistemas de referencia, tamaño del pixel, entre otros.

```
gdalinfo -
```
