## Obtener el valor máximo

```sql
-- Obtener el valor máximo del arreglo
array_max(
		-- Columnas a evaluar
		array(
			"E","F","M","Ab","My","J",	
			"Jl","Ag","S","O","N","D"
			)
)
```

![image](https://user-images.githubusercontent.com/88239150/227092525-57c19cff-ed8b-4154-8082-0e0f3b6c0a18.png)


## Obtener el campo con el valor máximo

```
-- Obtener el indice del valor máximo
with_variable(
	'indice',
	array_find(
		-- Columnas a evaluar
		array(
			"E","F","M","Ab","My","J",	
			"Jl","Ag","S","O","N","D"
		),
		"maxPrec"
	),
	array_get(
		array(
			'E','F','M','Ab','My','J',
			'Jl','Ag','S','O','N','D'
		),
		@indice
	)
)
```

![image](https://user-images.githubusercontent.com/88239150/227096523-06c39fd3-2537-4bae-bce2-8ddb24087874.png)


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
