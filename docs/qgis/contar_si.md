# Contar SI: Contar valores por un condición

Obtener el recuento de campos donde el atributo sea un valor distinto de 0.

### Procedimiento

Paso 1. Abrir la tabla de atributos

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
