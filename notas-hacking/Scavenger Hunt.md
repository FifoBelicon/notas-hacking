
## Descripcion

There is some interesting information hidden around this site [http://mercury.picoctf.net:39698/](http://mercury.picoctf.net:39698/). Can you find it?

## Hints
- You should have enough hints to find the files, don't run a brute forcer.

## Solucion

1. Analizamos la pagina web
 En este caso esta pagina es muy parecida a una que ya hemos trabajado en un reto anterior.
 2. Analizamos el codigo fuente de la pagina con  `ctrl + u`
Aqui encontramos la primera parte de la bandera: 

```
picoCTF{t
```

3. Analizamos el archivo css que esta en el codigo fuente:
Aqui encontramos otra parte de la bandera:

```
h4ts_4_l0
```

4. Analizamos el archivo`.js`que viene en el codigo fuente
Encontramos la siguiente pista: ` How can I keep Google from indexing my website? */`

5. Una de las cosas que no se indexan en google es el archivo  `robots.txt`y probamos ea ver si tiene
	- Encontramos la siguiente parte
```
t_0f_pl4c
```
Viene con la pista `# I think this is an apache server... can you Access the next flag?`

- Los servidores de apache server suelen tener un archivo oculto llamado .htaccess, en el cual en ocasiones puede estar publico
6. Buscamos el archivo `.htaccess`
Encuentro la cuarta parte de la flag:

```
3s_2_lO0k
```
Tambien nos da la siguiente pista: `I love making websites on my Mac, I can Store a lot of information there.`

Nos dice que la pagina se hizo en una mac, en este caso Mac tiene un archivo oculto que genera a todos los archivos en donde guarda los metadatos para poder mostrarlos en el Finder. Este archivo se llama `DS_Store`, por lo que buscare ese archivo a ver si encuentro algo:

```
_fa04427c}
```

Asi obtenemos toda la flag:

```
picoCTF{th4ts_4_l0t_0f_pl4c3s_2_lO0k_fa04427c}

```

## Referencias
