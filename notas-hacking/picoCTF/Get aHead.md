
# Descripcion

Find the flag being held on this server to get ahead of the competition [http://mercury.picoctf.net:45028/](http://mercury.picoctf.net:45028/)

## Hints
- Maybe you have more than 2 choices
- Check out tools like Burpsuite to modify your requests and look at the responses

## Solucion
Lo primero que debemos de hacer es interactuar con la pagina y analizar lo que esta haciendo.

En este caso observo que la pagina mas que nada solo tiene la opcion de cambiar el color del fondo.  
Enciendo el proxy de burpsuite para analizar como se mandan las peticiones:

1. Enciendo el interceptador
2. Eligo la opcion red y analizo la peticion en burpsuite
3. Hago un `ctrl + R` para enviar esta peticion al repetidor
4. Eligo la opcion `Send`para ver que como responde la pagina.
5. Repito el proceso para el fondo azul

En este caso, observo que las dos peticiones se hacen por el metodo POST, y por el nombre me suena que el reto puede ir por las cabeceras. En este caso, dice Get a Head, entonces se me ocurre probar poner HEAD en lugar de POST y le mando esta peticion por medio del repeater. 

Y con esto me encontre la flag:

```
picoCTF{r3j3ct_th3_du4l1ty_775f2530}
```

## Referencias
