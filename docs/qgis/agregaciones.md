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
	case when @indice = 0 then 'E'
		 when @indice = 1 then 'F'
		 when @indice = 2 then 'M'
		 when @indice = 3 then 'Ab'
		 when @indice = 4 then 'My'
		 when @indice = 5 then 'J'
		 when @indice = 6 then 'Jl'
		 when @indice = 7 then 'Ag'
		 when @indice = 8 then 'S'
		 when @indice = 9 then 'O'
		 when @indice = 10 then 'N'
		 when @indice = 11 then 'D'
	end
)
```

![image](https://user-images.githubusercontent.com/88239150/227094992-55d70f1a-6659-4dce-a227-f3f080db189e.png)

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
