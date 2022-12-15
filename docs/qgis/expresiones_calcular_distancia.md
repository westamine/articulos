# Expresiones en QGIS

![image](https://user-images.githubusercontent.com/88239150/207866370-0f133589-22bf-4879-b287-d6ce4364e801.png)

Basada en datos de capa y funciones predefinidas o definidas por el usuario, las **expresiones** ofrecen una forma poderosa de manipular el valor del atributo, la geometría y las variables para cambiar dinámicamente el estilo de la geometría, el contenido o la posición de la etiqueta, seleccionar algunas entidades, calcular valores en un campo, etc.

Para esete ejemplo buscaremos responder la siguiente pregunta realizada en un foro de GIS: **¿Es posible calcular la distancia mas contra entre un punto y una carretera?**

## Datos

Para este ejemplo contamos con una capa de puntos de interes `pois` y una capa de rutas `Ciclovías`. Necesitamos visualizar la distancia mas corta entre ambas capas y calcular en la capa de Puntos: Las coordenadas del punto mas cercano y la distancia en metros a la ciclovía.

## 1. Visualización

### 1.1. Visualizar el punto mas cercano de la capa de `pois` a la `ciclovía`

En propieddad de la capa `pois` ir a simbología, agregar una capa de simbolo y en tipo de capa de simbolo seleccionar **`Generador de Geometría`** y en tipo de Geometría seleccionar la opción **`Punto/Multipunto`**

![image](https://user-images.githubusercontent.com/88239150/207869085-98665583-24dc-4420-8f0c-8a255b8e8a77.png)

Luego, pegar la siguiente `expresión` en la ventana de expresiones y Aceptar.

```sql
closest_point(
	array_first(overlay_nearest('Ciclovias', $geometry)), 
	$geometry
)
```

![image](https://user-images.githubusercontent.com/88239150/207869663-9672d7d9-c5c8-41f9-a01c-4e9e4b6f2ce7.png)

Visualizamos los resultados:

![image](https://user-images.githubusercontent.com/88239150/207870306-0eb04648-a939-43b8-a27b-f62a9fd278a5.png)


### 1.2. Visualizar el segmento mas corto

Nuevamente, en la capa de `pois` agregar una nueva de capa de simbolo, en el tipo de capa de simbolo seleccionar **`Generador de Geometría`** y en tipo de Geometría seleccionar la opción **`CadenaDeLinea/CadenaMultiLinea`**. Luego, pegar la siguiente `expresión` en la ventana de expresiones y Aceptar.

```sql
make_line(
	closest_point(
		array_first(overlay_nearest('Ciclovias', $geometry)), 
		$geometry
		),
	$geometry
)
```

![image](https://user-images.githubusercontent.com/88239150/207870999-6bbd662d-a35a-4cc2-ba39-d382ef24d49e.png)

Finalmente, visualizamos en resultado:

![image](https://user-images.githubusercontent.com/88239150/207871246-07de4d7f-00a3-4a3a-b3c3-a753e877ca3d.png)


## 2. Etiquetado



## 3. Calculo de atributos



