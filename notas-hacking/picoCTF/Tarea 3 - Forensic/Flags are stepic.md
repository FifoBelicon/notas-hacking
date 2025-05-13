## Description

A group of underground hackers might be using this legit site to communicate. Use your forensic techniques to uncover their messageTry it [here](http://standard-pizzas.picoctf.net:59908/)!

## Hint

- In the country that doesn't exist, the flag persists
## Solution

Se busca el país que no existe.

Al hacer una búsqueda rápida, el país upanzi no existe. Por lo tanto inspeccionamos el código para buscar la ruta.

```
{} name: "Upanzi, Republic The",img: "flags/upz.png", style:"width: 120px!important; height: 90px!important;" },
```

Descargamos la imágen

```
└─$ wget http://standard-pizzas.picoctf.net:59908/flags/upz.png

```

La herramieta `stepic` es una herramienta de estenografía para imágenes que permite ocultar y extraer imágenes dentro de bits menos significativos. Con `-d` le indica que debe decodificar un mensaje oculto, y con `-i` se especifica que la imagen de entrada es upz.png.

```
└─$ stepic -d -i upz.png              
/usr/lib/python3/dist-packages/PIL/Image.py:3402: DecompressionBombWarning: Image size (150658990 pixels) exceeds limit of 89478485 pixels, could be decompression bomb DOS attack.
  warnings.warn(
picoCTF{fl4g_h45_fl4g4a37da4c}                                                       
```

```
picoCTF{fl4g_h45_fl4g4a37da4c}

```

## Referencias

