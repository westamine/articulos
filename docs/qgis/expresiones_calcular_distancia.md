# Expresiones en QGIS

![image](https://user-images.githubusercontent.com/88239150/207866370-0f133589-22bf-4879-b287-d6ce4364e801.png)

Basada en datos de capa y funciones predefinidas o definidas por el usuario, las **expresiones** ofrecen una forma poderosa de manipular el valor del atributo, la geometría y las variables para cambiar dinámicamente el estilo de la geometría, el contenido o la posición de la etiqueta, seleccionar algunas entidades, calcular valores en un campo, etc.

Para esete ejemplo buscaremos responder la siguiente pregunta realizada en un foro de GIS: **¿Es posible calcular la distancia mas contra entre un punto y una carretera?**

## Datos

Para este ejemplo contamos con una capa de puntos de interes `pois` y una capa de rutas `Ciclovías`. Necesitamos visualizar la distancia mas corta entre ambas capas y calcular en la capa de Puntos: Las coordenadas del punto mas cercano y la distancia en metros a la ciclovía.

## 1. Visualización

### 1.1. Visualizar el punto mas cercano de la capa de `pois` a la `ciclovía`

En propieddad de la capa `pois` ir a simbología, agregar una simbología simple y en tipo de capa de simbolo seleccionar **`Generador de Geometría`** y en tipo de Geometría seleccionar la opción **`Punto/Multipunto`**

![image](https://user-images.githubusercontent.com/88239150/207869085-98665583-24dc-4420-8f0c-8a255b8e8a77.png)


```sql
closest_point(
	array_first(overlay_nearest('Ciclovias', $geometry)), 
	$geometry
)
```


## 2. Etiquetado



## 3. Calculo de atributos



