## Descripcion
Do you know how to move between directories and read files in the shell? Start the container, `ssh` to it, and then `ls` once connected to begin. Login via `ssh` as `ctf-player` with the password, `6d448c9c`

Additional details will be available after launching your challenge instance.

## Hints
Finding a cheatsheet for bash would be really helpful!

## Solucion

Lo primero que debemos de realizar, es conectarnos a la maquina que nos indica el reto, en este caso ya nos da el comando para conectarnos, el cual es el siguiente:
- `ssh -p 65193 ctf-player@saturn.picoctf.net`
- Escribimos la contraseña es 6d448c9c

Una vez conectados hacemos un `ls` para ver que tenemos. Tenemos la primera parte de la flag y las instrucciones.

Las instrucciones nos dice que nos movamos a la raiz, esto se logra con 
- `cd /`
Aqui encontramos la segunda parte de la flag y la siguiente instruccion.
- La siguiente instruccion nos pide movernos a la carpeta home del usuario:
	- `cd ~`
	- Aqui encontramos la tercera parte de la flag

`picoCTF{xxsh_0ut_0f_\/\/4t3r_5190b070}`

## Referencias
