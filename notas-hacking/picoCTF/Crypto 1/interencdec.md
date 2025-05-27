# Descripcion

Can you get the real meaning from this file.Download the file [here](https://artifacts.picoctf.net/c_titan/111/enc_flag).

# Hints
- Engaging in various decoding processes is of utmost importance

# Solucion

Lo primero que hacemos es descargar el archivo. Este nos dice que es la bandera pero esta encodeada.

Lo primero que tenemos que hacer es ver el contenido usando el comando strings:

```
strings enc_flag                         
YidkM0JxZGtwQlRYdHFhR3g2YUhsZmF6TnFlVGwzWVROclh6ZzVNR3N5TXpjNWZRPT0nCg==

```

Viendo el `==`, veo que se puede tratar de base64. Uso el comando `base64` de linux para decodear cadenas en base 64

```

base64 -d enc_flag 
b'd3BqdkpBTXtqaGx6aHlfazNqeTl3YTNrXzg5MGsyMzc5fQ=='

```

Aqui hay algo sospechoso, ya que muchas veces de la que se trabaja con codificadores, le tienes que indicar con el caracter `b` cadena en bits. Por lo que el texto encodeado esta entre las comillas. Esta cadena igual termina con `==`. Por  lo que vuelvo a hacer un base64. Obteniendo la siguiente salida:

```
wpjvJAM{jhlzhy_k3jy9wa3k_890k2379}

```

Veo que tiene dos corchetes, igual que el formato de la flag. Intento por el cifrado caesar en fuerza bruta. Este despuesde 19 rotaciones da el siguiente resultado:

```
picoCTF{caesar_d3cr9pt3d_890d2379}
```

