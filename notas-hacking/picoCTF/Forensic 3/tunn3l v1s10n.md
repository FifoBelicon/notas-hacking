
# Descripcion
We found this [file](https://mercury.picoctf.net/static/21c07c9dd20cd9f2459a0ae75d99af6e/tunn3l_v1s10n). Recover the flag.

# Hints
- Weird that it won't display right...

# Solucion

Lo primero que hice es tratar abrir el archivo y es correcta mi hipotesis, el archivo no se puede abrir. 

Lo primero que hago es revisar que tipo de archivo es con el comando `file`, sin embargo la salida de este comando es `data`.

Intente revisar los metadatos con la herramienta `exiftool`, pero tampoco encontre informacion relevante.

Revise la firma del archivo con `hexeditor` para ver si habia algun problema con los encabezados. En este caso, me encuentro con los primeros bytes que corresponden a un archivo `BMP`, en este caso los primeros bytes si corresponden a la firma de este archivo, pero este no se puede visualizar aun. En este caso investigamos mas acerca de tipo de archivo y estos tiene una peculiaridad de tener un offset bastante estricto, verifico si este offset es el correcto. En este caso el bitmap tiene quie ser de 14 bytes, buscamos la poscion 14 en el hexadecimal y colocamos "28", 4 bytes despues volvemos a colocar "28". 

Ahora si intentamos abrir el archivo, podemos visualizar una imagen, pero esta nos muestra una leyenda, donde nos indica que no esta la bandera. 

Puede que la imagen solo muestre una parte, por medio de la firma del archivo podemos modificar el tamaño de la imagen. 
Buscamos el byte que corresponde al encargado de especificar el tamaño y modificamos con un `3`. 

Guardamos y volvemos abrir la imagen y nos encontramos con la bandera que estaba escondida en una parte que no se veia de la imagen.

## Referencias
-  https://en.wikipedia.org/wiki/BMP_file_format
- https://en.wikipedia.org/wiki/List_of_file_signatures