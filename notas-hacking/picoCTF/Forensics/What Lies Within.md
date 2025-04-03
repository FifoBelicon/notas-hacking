
# Descripcion
There's something in the [building](https://jupiter.challenges.picoctf.org/static/011955b303f293d60c8116e6a4c5c84f/buildings.png). Can you retrieve the flag?

## Hints
- There is data encoded somewhere... there might be an online decoder.

# Solucion

Lo primero que hago es un analisis del codigo detras de la imagen usando cat y strings, pero nada importante.

Ahora hice uso de una herramienta de estaganografia para ver si hay datos ocultos camuflados en los datos de la imagen. La herramienta `zsteg` me ayuda en eso:

- `zsteg -a buildings.png

Con esto obtengo la flag:


## Referencias.