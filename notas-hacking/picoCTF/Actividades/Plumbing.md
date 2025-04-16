## Descripcion
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag? Connect to `jupiter.challenges.picoctf.org 7480`.

## Solucion
Lo primero a realizar este reto sera conectarnos por medio ``nc`` a la direccion y al puerto que nos da el reto y analizemos la salida:
![[Pasted image 20250212232925.png]]
Podemos ver que genera una gran salida. Una de las pistas de este reto es que podemos usar pipelines ( ' | ' ), estos nos sirven para concatenar diferentes comandos. 
Al ver que la salida es bastante grande tardaria demasiado en verificar si se encuentra la flag ahi. Por lo tanto hago uso de las redirecciones ('>').
Escribo el siguiente comando:
- ` nc jupiter.challenges.picoctf.org 7480 > salida.txt`.
Este comando redirecciona la salida que muestra en la terminal, solo que ahora guarda toda esta en el archivo `salida.txt` .
- Ahora que la salida esta guardada en el archivo `.txt` puedo hacer eso de un grep sobre este archivo para analizar y verificar si la flag esta escondida en la salida. Escribo el siguiente comando:
- `grep 'pico' salida.txt `
Este comando busca la palabra `pico` en todo el archivo.
![[Pasted image 20250212233554.png]]
Para nuestra fortuna la flag si se encontraba ahí.

## Referencias 
https://www.linfo.org/pipes.html
