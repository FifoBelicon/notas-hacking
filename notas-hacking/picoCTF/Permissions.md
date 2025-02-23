
## Descripcion
Can you read files in the root file?

Additional details will be available after launching your challenge instance.

## Hints
- What permissions do you have?


## Solucion

En este reto, tiene la tematica de escalada de privilegios. Una de las cosas que siempre se deben ejecutar cuando se trata de escalar privilegios es usar el comando: 
- `sudo -l`
Este comando me mostrara todos los binarios que se ejecutan como vi, esto es un vector de ataque ya que podemos ejecutar estos comandos como un usario root. 
Por lo tanto ejecutamos `sudo -l` en el servidor:

```
/$ sudo -l
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi

```

Obtenemos esta salida y significa que tenemos que el binario vi se ejecuta como root.

Ahora, ¿Que podemos hacer con vi?

Vi es un editor de texto en linea de comandos.

Por lo tanto si tenemos un editor de texto podemos escalar a un RCE (REMOTE CODE EXECUTION) es decir, podemos escribir comandos y ejecutarlos, en este caso como vi se ejecuta como root podemos escribir un comando en vi y ejecutarlo como root y asi escalar privilegios. Para esta ejecucion usamos el siguiente comando: 

-  `:!/bin/bash`
	- Primero, el `:` para poder escribir en vi
	- el `!` es un simbolo que se usa para ejecutar un comando del sistema dentro de vi
	- `/bin/bash`  es la ruta al interprete de comandos bash, es decir, es el interprete de comandos en el sistema, en este caso, si le indico a vi ejecutar el  `/bin/bash` le indico a vi que use bash para ejecutar lo siguiente, pero, como vi se ejecuta como root, en este caso estaria ejecutando los siguientes comando como root y asi podria escalar privilegios

- Para ejecutar el binario como root:
- `sudo /usr/bin/vi` 
Una vez escrito nuestro payload (`:!/bin/bash`), accedemos a una shell root, y ahora tenemos que leer la flag
- Nos dirigimos al directorio root:
	- `cd /root`
	- Hacemos un ls para ver que hay
	- Vemos que no tenemos nada, por lo tanto hacemos un `ls -la` para ver los archivos ocultos
	- Nos encontramos con el archivo `.flag.txt` 
	- Leemos este archivo:
```
root@challenge:~# cat .flag.txt 
picoCTF{uS1ng_v1m_3dit0r_021d10ab}

```


## Referencias

