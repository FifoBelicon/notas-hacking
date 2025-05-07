
# Descripcion

Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [this](https://mercury.picoctf.net/static/b6205dd933ec01c022c4e6acbdf11116/dolls.jpg)

# Hints
- Wait, you can hide files inside files? But how do you find them?
- Make sure to submit the flag as picoCTF{XXXXX}

# Solucion

Este reto hace referencia a una muñeca rusa que contiene muñecas mas pequeñas en su interior. En este caso nos da una imagen. 
Existe una forma de ocultar multiples archivos en una imagen, este proceso es parecido a comprimir un archivo como un zip. Por lo que le hago un `unzip` a la imagen.

Esto nos genera una carpeta llamada `base_images.`

Si nos dirigimos al interior de este directorio nos encontramos otra imagen. Si la visualizamos nos damos cuenta que es una imagen mas pequeña de la primera imagen, esto simbolizando que ya descubrimos una 'capa', entonces, seguimos aplicando el comando `unzip` hasta que ya no haya mas imagenes.

Nos damos cuenta que alrededor de la cuarta imagen nos suelta un archivo llamado `flag.txt`

Si hacemos un cat a este fichero nos da lo siguiente:

```
└─$ cat flag.txt                     
picoCTF{4f11048e83ffc7d342a15bd2309b47de}      

```

# Referencias
- https://www.wikihow.com/Hide-a-File-in-an-Image-File
