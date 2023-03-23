# Funciones de arreglo

Las funciones de arreglos nos permiten **crear y manipular matrices**. Cada valor dentro de la matriz se identifica por la posición que ocupa dentro de esta, por tal motivo. para este tipo de estructura, el orden especificado es de vital importancia.

A continuación se detallan algunos ejemplos de usos de arreglos dentro de la calculadora de campos de QGIS.

## Datos utilizar

Para el desarrollo de los ejemplos se utilizarán los datos de `precipitación` de la comunidad de Aragon en España. Esta capa cuenta con campos que almacenan los valores de la precipitación medida para cada mes:

![image](https://user-images.githubusercontent.com/88239150/227383279-d40efb07-ec98-4142-9617-1c967f5edf55.png)

## Obtener el valor máximo de un arreglo

Obtener el valor de la precipitación máxima del año:

```sql
array_max(
	array(
		"E","F","M","Ab","My","J",	
		"Jl","Ag","S","O","N","D"
	)
)
```

Donde:

* **array_max**: Devuelve el valor máximo de una matriz
* **array**: Devuelve un arreglo que contiene todos los valores pasados como parámetro. Para este ejemplo, pasamos los valores de precipitación de cada mes

Calculo:

![image](https://user-images.githubusercontent.com/88239150/227384907-2a8a334b-7b4c-44bb-841c-47ff207e9ae9.png)

Resultados:

![image](https://user-images.githubusercontent.com/88239150/227385052-080d31d4-10ea-49fd-bfea-ae5fe62a67cc.png)

## Obtener el mes con la máxima precipitación

Obtener la descripción del mes donde ocurre la precipitación máxima. 

Para este ejemplo, utilizaremos la función **with_variable** que permite crear y establecer el valor de una variable para ser utilizado en un tercer argumento

```
with_variable(nombre, valor, expresión)
```

Donde:

* **nombre**: El nombre de la variable a establecer
* **valor**: El valor a establecer
* **expresión**: La expresión para la cual la variable estará disponible

Volviendo al ejemplo, la expresión a utilizar será la siguiente:

```
with_variable(
	-- nombre
	'index_maxPrec',
	
	-- valor
	array_find(
		array(
			"E","F","M","Ab","My","J",	
			"Jl","Ag","S","O","N","D"
		),
		"maxPrec" --campo maxPrec calculado previamente
	),
	-- expresión
	array_get(
		array(
			'E','F','M','Ab','My','J',
			'Jl','Ag','S','O','N','D'
		),
		@index_maxPrec  --Indice a devolver
	)
)
```

Donde:

* **index_maxPrec**: Nombre de la variable a establecer
* **array_find**: Devuelve el índice (0 para el primero) de un valor dentro de un arreglo. Para este ejemplo, busca el valor del campo **`maxPrec`** devolviendo la posición dentro del arreglo especificado.
* **array_get**: Devuelve el valor "N" dentro de un arreglo en función del índice indicado

Calculo:

![image](https://user-images.githubusercontent.com/88239150/227388339-e183624c-fe47-4066-a1fb-4ca62201d63d.png)

Resultados:

![image](https://user-images.githubusercontent.com/88239150/227388453-7f7e03ca-1bc3-479d-89b6-b0341ff8ccc7.png)

## Contar valores por un condición

```
with_variable(
	'campos',
	array(
		"E","F","M","Ab","My","J",		  
		"Jl","Ag","S","O","N","D"
		),
	(
	  array_length(@campos) -
	  array_count(@campos, 0)
	)
)
```
