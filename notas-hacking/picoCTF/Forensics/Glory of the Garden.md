
# Descripcion

  
This [garden](https://jupiter.challenges.picoctf.org/static/43c4743b3946f427e883f6b286f47467/garden.jpg) contains more than it seems.

# Hints
- What is a hex editor?

# Solucion

Lo que nos descarga el reto es una imagen. Hay que analizarla para verificar por donde atacar. Lo primero que analizamos es si hay algo escondido en la imagen, en este caso en la imagen no hay nada sospechoso, lo que sigue es ver si hay algo algo en los bytes de la imagen, por lo que hacemos un cat:

- `cat garden.jpg` : En este caso la salida muestra una gran cantidad de caracteres ilegibles, por lo que si queremos mostrar caracteres legibles usamos el comando `strings` 

- `strings garden.jpg` Aqui encontramos la flag:


```
Here is a flag "picoCTF{more_than_m33ts_the_3y3657BaB2C}"

```

## Referencias

