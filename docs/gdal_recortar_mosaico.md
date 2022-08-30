# Recortar un mosaico de imagenes con GDAL

Hace poco en un grupo de SIG lei un post donde preguntaban como recortar un mosaico de gran tamaño de forma eficiente. El usuario indicaba que al tratar de realizar este proceso desde un SIG de escritorio el proceso tardaba horas e incluso dias sin ejecutarse.

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

<p align="center"><img src = "https://user-images.githubusercontent.com/88239150/187310580-223a2d50-6d87-46ed-b39a-bd4d274d1d1c.png"/></p>

Acceder a esta carpeta utilizando el simbolo del sistema de windows (cmd)

```
>D:
>cd <ruta_de_la_carpeta>
```

<p align="center"><img src = "https://user-images.githubusercontent.com/88239150/187311414-a384a806-f2f0-4fad-be21-17f8d038c03d.png"/></p>

Podemos inspeccionar las imagenes con `gdalinfo` para comprobar que tengan las misma carácteristicas: Número de bandas (Como son DEM tienen 1 banda), sistemas de referencia, tamaño del pixel, entre otros.

```
gdalinfo ASTGTM_S12W077_dem.tif
```

<p align="center"><img src = "https://user-images.githubusercontent.com/88239150/187316082-41072101-0712-4263-b389-ac67a7b97196.png"/></p>

Para generar el mosaico de imagenes utilizaremos el programa `gdalbuildvrt`. Este programa construye un conjunto de datos virtual (VTR) a partir de una lista de conjuntos de datos de entrada. La lista de conjuntos de datos se puede especificar al final de la línea de comando, o colocarse en un **archivo de texto** para listas muy largas.

> Es necesario indicar que `gdalbuildvrt` realiza una serie de comprobaciones para asegurarse de que todos los archivos que se colocarán en el VRT resultante tengan características similares: número de bandas, sistema de referencia, interpretación del color. De lo contrario, se omitirán los archivos que no coincidan con las características comunes.

Para este ejercicio utilizaremos un archivo de texto con el nombre de los archivos de entrada que formaran el mosaico. Para esto debemos ejecutar, desde el simbolo del sistema, el comando dir con un patron que liste los archivos .tif como se muestra a continuación:

```
dir /b *.tif > lista_archivos.txt
```

<p align="center"><img src = "https://user-images.githubusercontent.com/88239150/187313769-12dbc851-ba9d-4db6-a1fb-2b463642efcb.png"/></p>

Verificar que el archivo contenga los nombres de los archivos .tif que formaran el mosaico

```
type lista_archivos.txt
```

<p align="center"><img src = "https://user-images.githubusercontent.com/88239150/187313806-3f39c078-8577-4ddf-a354-cc6633503757.png"/></p>

Con esto, ya estamos listo para generar el mosaico virtual, para ello ejecutar el siguiente comando:

```
gdalbuildvrt -input_file_list lista_archivos.txt mosaico.vrt
```

<p align="center"><img src = "https://user-images.githubusercontent.com/88239150/187316221-1f49c726-00a5-489e-a8e5-d376ee4b5fde.png"/></p>

Podemos comparar las imagenes originales y el mosaico virtual que hemos fusionado.

<p align="center"><img src = "https://user-images.githubusercontent.com/88239150/187317035-9faf4638-d606-4807-ab16-0a22944b976b.png"/></p>

Ahora, con la utilidad `gdalwarp` vamos a recortar el mosasico virtual. El recorte se realizará con la capa de área de influencia (ADI.shp)

```
gdalwarp -cutline ADI.shp -crop_to_cutline mosaico.vrt mosaico_adi.tif
```

<p align="center"><img src = "https://user-images.githubusercontent.com/88239150/187318158-889fc819-a7c0-4e5c-a5d7-2a978ae84fd7.png"/></p>

Una vez finalizado el proceso, tendremos como resultaod la imagen recortada y en formato TIF

<p align="center"><img src = "https://user-images.githubusercontent.com/88239150/187318438-8c06bd86-6537-4ab2-bba0-49b9185f575b.png"/></p>

## Referencias

https://gdal.org/programs/gdalbuildvrt.html

https://gdal.org/programs/gdalwarp.html

https://courses.spatialthoughts.com/gdal-tools.html


