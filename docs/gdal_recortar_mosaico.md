# Recortar un mosaico de imagenes con GDAL

Hace poco en un grupo de SIG lei un post donde preguntaban como recortar un mosaico de gran tamamaño de forma eficiente. El usuario indicaba que al tratar de realizar este proceso desde un SIG de escritorio el proceso tardaba horas y dias sin ejecutarse.

Existen muchas formas eficientes de abordar este problema, como usar softwares especializados en el procesamiento de imagenes satelitales. Sin embargo, en este tutorial abordaremos el uso de la biblioteca GDAL como alternativa de solución a este problema.

## ¿Porqué usar GDAL?

GDAL/OGR es una biblioteca traductora para formatos de datos geoespaciales, que además proporciona un conjunto de herramientas para el tratamiento de estos datos. Se publica bajo una licencia de código abierto de estilo MIT por parte de la Fundación Geoespacial de Código Abierto (OSGEO).

A continuación se detallan los motivos para utilizar GDAL:

* Procesar datos Geospaciales de manera eficiente.
* Repetir los pasos de procesamiento para diferentes conjuntos de datos.

## Fuente de datos

Para el desarrollo de este tutorial se utilizaron las imagenes ASTER GDEM de descarga de gratuita desde los geoservidores del Ministerio del Ambiente de Perú (MINAM). Puedes realizar la descarga del siguiente [link](https://geoservidorperu.minam.gob.pe/geoservidor/download_raster.aspx)
