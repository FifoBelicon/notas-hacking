
## Descripcion

Who doesn't love cookies? Try to figure out the best one. [http://mercury.picoctf.net:6418/](http://mercury.picoctf.net:6418/)

## Hintes
None

## Solucion

Lo primero que tenemos que hacer en este caso, es analizar la pagina que se nos muestra y entender lo que hace.
En este caso solo tenemos un buscador en la cual nos pide ingresar un tipo de galleta. 

Una vez que ingresamos una galleta que esta en registrada solo regresa un enunciado que dice que le gustan las galletas.

Por el nombre del reto "cookies", pienso que el reto que sera algo que ver con las cookies. En este caso si analizamos la cookie que tiene la pagina tiene una que se llama 'name' y tiene un numero asignado segun el nombre que ingresamos. 

En este caso, si ingresamos 'snickerdoodle' la cookie cambia a 1, si ponemos 'chocolate chips', tenemos que la cookie cambia a 2.

Ir probando galleta por galleta puede ser tardado, para esto hago uso de la herramienta  `burpsuite` 

1. Me dirijo a la pantalla de Proxy
2. Abro el navegador de burpsuite
3. Abro el sitio web del reto
4. Ingreso la cookie 'snickerdoodle' e intercepto la peticion
5. Mando esta peticion al `intruder` 
6. Selecciono el numero que corresponde la `cookie name`
7. Configuro el payload, como una serie numeria , que vaya del 1 en 1 hasta 100.
8. Analizo las peticiones para encontrar la flag

En este caso veo que la flag se encontro cuando el valor de `name` es 18.

```
picoCTF{3v3ry1_l0v3s_c00k135_88acab36}
```

### Referencias
