Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/515f19f3612bfd97cd3f0c0ba32bd864/file)? This would be really tedious to look through manually, something tells me there is a better way.

## Solucion
En este caso, el archivo descargado tiene una gran cantidad de caracteres, por lo que buscar manualmente la flag seria algo bastante tedioso y tardado, para eso hacemos uso de la herramienta: 
- grep: Sirve para buscar coincidencias segun nosotros se lo indiquemos
En este caso usamos el grep para buscar el formato de la flag `picoCTF.
- grep 'picoCTF' file
Obteniendo asi la flag.
```
picoCTF{grep_is_good_to_find_things_5af9d829
```
![[Pasted image 20250212222314.png]]
## Referencias
https://ryanstutorials.net/linuxtutorial/grep.php