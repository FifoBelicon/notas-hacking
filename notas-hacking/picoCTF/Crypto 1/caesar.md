# Descripcion
Decrypt this [message](https://jupiter.challenges.picoctf.org/static/49f31c8f17817dc2d367428c9e5ab0bc/ciphertext).

# Hints
- caesar cipher [tutorial](https://learncryptography.com/classical-encryption/caesar-cipher)

# Solucion

Lo primero que hacemos es descargar el archivo. Este viene de la siguiente forma:

```
┌──(cyberchef㉿kali)-[~/Downloads/caesar]
└─$ cat ciphertext 
picoCTF{ynkooejcpdanqxeykjrbdofgkq}  
```

Solo lo que esta dentro de las llaves esta encodeado, entonces solo meto esto en un decoder online de ceasar. Cambie de rotacion hasta encontrar una cadena de texto legible y fue:

`crossingtherubiconvfhsjkou`

Armo la flag:
picoCTF{crossingtherubiconvfhsjkou}

