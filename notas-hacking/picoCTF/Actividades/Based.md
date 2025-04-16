## Descripcion
To get truly 1337, you must understand different data encodings, such as hexadecimal or binary. Can you get the flag from this program to prove you are on the way to becoming 1337? Connect with `nc jupiter.challenges.picoctf.org 29956`.

## Hints
- I hear python can convert things.
- It might help to have multiple windows open.

## Solucion

Lo primero que debemos de hacer sera conectarnos a la maquina y observar la salida que nos da:
- `nc jupiter.challenges.picoctf.org 29956`
```
Let us see how data is stored
sludge
Please give the 01110011 01101100 01110101 01100100 01100111 01100101 as a word.
...
you have 45 seconds.....

```
Nos pide que descrifemos esta cadena de texto e ingresemos la palabra que se encuentra escondida, en este caso observamos que esta encodeada en binario, por lo que usamos la herramienta de cyberChef para descifrar y obtener la primer palabra `sludge`

Despues nos dara la siguiente instruccion: `Please give me the  143 157 155 160 165 164 145 162 as a word.`
Uso la herramienta de cyberChef y el autodetect para detectar que esa serie de numeros esta encodeada y descubrimos que dice `computer` y escribimos la palabra

Ahora tenemos la siguiente instruccion:
`Please give me the 74657374 as a word.`
	Vuelvo a utilizar el autodetect de Cyberchef y vemos que la cadena esta encodeada en hexadecimal y que la palabra es `test`

Al escribir esto nos dara la flag:
```
picoCTF{learning_about_converting_values_b375bb16}

```

## Referencias
- https://gchq.github.io/CyberChef/
