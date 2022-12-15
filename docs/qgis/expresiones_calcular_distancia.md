# Expresiones en QGIS

![image](https://user-images.githubusercontent.com/88239150/207866028-7748b26b-cace-40be-8cc7-e72cb59314cd.png)


Basada en datos de capa y funciones predefinidas o definidas por el usuario, las **expresiones** ofrecen una forma poderosa de manipular el valor del atributo, la geometría y las variables para cambiar dinámicamente el estilo de la geometría, el contenido o la posición de la etiqueta, seleccionar algunas entidades, calcular valores en un campo, etc.


### Ejemplo: Calcular la distanca mas corta entre un Punto y un Línea

**Datos**: Para este ejemplo contamos con una capa de puntos de nombre `pois` (puntos de interes) y una capa de línea de rutas `Ciclovias`. Necesitamos visualizar la distancia mas corta entre ambas capas y el calculo en la capa de Puntos de: Coordenadas del punto mas cercanos y la distancia mas corta hacia la línea.


