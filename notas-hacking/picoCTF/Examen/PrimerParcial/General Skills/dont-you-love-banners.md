
## Descripcion

Can you abuse the banner?The server has been leaking some crucial information on `tethys.picoctf.net 63591`. Use the leaked information to get to the server.To connect to the running application use `nc tethys.picoctf.net 51756`. From the above information abuse the machine and find the flag in the /root directory.

## Hints
- Do you know about symlinks?
- Maybe some small password cracking or guessing

# Solucion

Analizamos la descripcion. Se nos proporcionan dos servidores diferentes. Analizamos cada uno para ver que hacen

1. Server 1
	`nc tethys.picoctf.net 63591`
	Nos conectamos y analizamos la respuesta del servidor:
	```
	SSH-2.0-OpenSSH_7.6p1 My_Passw@rd_@1234
	```
	Encontramos que suelta `My_Passw@rd_@1234` y no hace nada mas.

Ahora analizamos el segundo server

2.  Server 2
	Una vez que nos conectamos encontramos lo siguiente:
	```
	*************************************
**************WELCOME****************
*************************************

	what is the password? 

	```
Si ponemos `My_Passw@rd_@1234` el servidor nos pregunta:

```
What is the top cyber security conference in the world?

```
``
Buscamos en internet esta pregunta y nos da un top.
Probamos una por una, hasta que con `DEFCON` pasamos a la siguiente pregunta.

```
the first hacker ever was known for phreaking(making free phone calls), who was it?

```

Buscamos esta pregunta en internet y nos arroja a `John Draper` y esta nos permite conectar una bash al servidor.

Somos el usuario `player` y analizamos el contenido del server.
Hacemos un ls  al directorio actual y encontramos lo siguiente:
- `banner  text`

Hacemos un cat a cada archivo pero no encontramos nada interesante. 
Ahora si leemos la hint, habla de hacer enlaces simbolicos. Estos enlaces permiten hacer referencia a directorios y archivos, por lo que intento hacer un enlace simbolico al directorio `root`, por que ahi se encuentra la flag.

- `ln -s /root root2`
si hacemos un ls al directorio actual podemos ver que si se creo el directorio `root2`. Si nos movemos ahi con `cd` observamos que si podemos acceder y ver su contenido, este contiene dos archivos.

-  `flag.txt    script.py`
SI hacemos un cat a flag.txt nos dara un error por que no tenemos permiso. Pero si le hago un cat a `script.py` encontramos el codigo fuente de lo que nos muestra cuando nos conectamos al servidor. Al principio dice que carga `banner` del directorio home del usuario, y esa carga la hace con permisos de root. Entonces, como le hacemos para leer la flag.

Se me ocurrio borrar el banner y crear un enlace simbolico que tambien se llame banner pero que este enlace apunte a flag.txt. Asi cuando se vuelva a correr el servidor va a cargar leer la flag ya con privilegios y la va a mostrar cuando me contecte.
`rm banner`
`ln -s /root/flag.txt banner`
`ctrl + c`
`nc tethys.picoctf.net 50335`
``
```
picoCTF{b4nn3r_gr4bb1n9_su((3sfu11y_218ef5d6}

what is the password? 

```

## Referencias

