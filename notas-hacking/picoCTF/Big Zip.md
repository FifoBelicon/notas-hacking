## Descripcion 
Unzip this archive and find the flag
### Hints
- Can grep be instructed to look at every file in a directory and its subdirectories?

## Solucion

Para resolver este reto, se nos proporciona un archivo zip el cual lo primero es descomprimirlo para ver su contenido, esto se logra con el comando `unzip big-zip-files `.
Al ver que son bastantes archivos, usamos un `grep` recursivo, que se indica con el parametro  `-r`, esto lo que hace es buscar recursivamente en los directos, por lo si escribo el siguiente comando me es posible encontrar la flag entre todos los directorios:
- `grep -r 'picoCTF`
flag:  
- picoCTF{gr3p_15_m4g1c_ef8790dc}
## Referencias




