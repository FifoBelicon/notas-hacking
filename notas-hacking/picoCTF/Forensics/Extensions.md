# Descripcion
This is a really weird text file [TXT](https://jupiter.challenges.picoctf.org/static/e7e5d188621ee705ceeb0452525412ef/flag.txt)? Can you find the flag?

## Hints
- How do operating systems know what kind of file it is? (It's not just the ending!
- Make sure to submit the flag as picoCTF{XXXXX}

# Solucion

En este reto descargamos un archivo txt, en el cual se menciona que hay algo raro con la extension txt.

Lo primero que hice fue usar el comando `file` para saber en realidad que tipo de archivo es:
- `file flag.txt`
La salida de este comando me dice que es un archivo png. 
Cambiamos la extension al tipo de archivo correcto:

- `mv flag.txt flag.png`

Y analizamos la imagen:

![[images/flagExtension.png]]

## Referencias
