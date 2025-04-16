
## Descripcion

The factory is hiding things from all of its users. Can you login as Joe and find what they've been looking at? `https://jupiter.challenges.picoctf.org/problem/44573/` ([link](https://jupiter.challenges.picoctf.org/problem/44573/)) or http://jupiter.challenges.picoctf.org:44573

## Hints
- Hmm it doesn't seem to check anyone's password, except for Joe's?

# Solucion

1. Lo primero que debemos analizar en esta pagina es con intentar loggearse con credenciales por defecto, en este caso, sucede algo curioso, pues, si pongo cualquier usuario, y no pongo contraseña, me puedo loggear.

2. Sucede algo mas curioso, en este caso si nos intentamos loggearnos como el usuario `Joe` nos salta una advertencia que la contraseña de Joe es super segura.

3. Interceptamos la peticion por medio de burpsuite para analizar como se realiza la peticion.

4. No encontre nada sospechoso, pero intente hacer un `ataque fuerza bruta` por medio del intruder.
5. Nuevamente sin exito.
6. Ahora, es sospechoso que me pueda loggear con cualquier usuario menos con Joe. Entonces realizo el siguiente procedimiento:
	1. Me loggeo con cualquier usuario
	2. Identifico la cookie con la que me loggeo
	3. Intercambio al valor de `admin=False` a `True`
	4. Recargamos
7. Obtenemos la flag.
```
picoCTF{th3_c0nsp1r4cy_l1v3s_0c98aacc}
```


# Referencias
