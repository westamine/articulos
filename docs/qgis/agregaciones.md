# Obtener el valor máximo

```
-- Obtener el valor máximo del arreglo
array_max(
		-- Columnas a evaluar
		array(
			"E","F","M","Ab","My","J",	
			"Jl","Ag","S","O","N","D"
			)
)
```

# Contar SI: Contar valores por un condición

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
