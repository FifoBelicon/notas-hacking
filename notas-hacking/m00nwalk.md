# Descripcion
Decode this [message](https://jupiter.challenges.picoctf.org/static/fc1edf07742e98a480c6aff7d2546107/message.wav) from the moon.

## Hints
- How did pictures from the moon landing get sent back to Earth?
- What is the CMU mascot?, that might help select a RX option

# Solucion

En este caso cuando descargamos el mensaje de la luna obtenemos un archivo `.wav`, esto nos quiere decir que es un archivo de audio. Por lo tanto tenemos que encontrar la flag aqui. 
Lo que hago es analizar el espectrograma del audio, en busca de tecnicas de esteganografia, usando la aplicacion de audacity. Pero desafortunadamente no encontre nada escondido en el espectro. Ahora usando una herramienta para decodificar señales sstv, que son las que se usan para mandar mensajes a la tierra, entonces, hago uso de esta herramienta.

Despues de la instalacion, hago uso del siguiente comando:
- `sstv -d message.wav -o result.png` 

```
[sstv] Searching for calibration header... Found!    
[sstv] Detected SSTV mode Scottie 1
[sstv] Decoding image...   [##############################################] 100%
[sstv] Drawing image data...
[sstv] ...Done!

```

Ahora abrimos la imagen:

![](images/result.png)

## Referencias

https://github.com/colaclanth/sstv 

