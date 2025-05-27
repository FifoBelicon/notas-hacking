# Descripcion
The one time pad can be cryptographically secure, but not when you know the key. Can you solve this? We've given you the encrypted flag, key, and a table to help `UFJKXQZQUNB` with the key of `SOLVECRYPTO`. Can you use this [table](https://jupiter.challenges.picoctf.org/static/1fd21547c154c678d2dab145c29f1d79/table.txt) to solve it?.

# Hints
- Submit your answer in our flag format. For example, if your answer was 'hello', you would submit 'picoCTF{HELLO}' as the flag.
- Please use all caps for the message.

# Solucion

Segun la forma que tiene este algoritmo de cifrado, puedo ver que se trata de un cifrado vigenere, ahora, para no buscar caracter por caracter en la tabla, hago uso de un decodificador online. Ingreso el la bandera encodeada, y le indico la clave y tengo el siguiente resultado:

```
CRYPTOISFUN
```

Armamos la flag:
- `picoCTF{CRYPTOISFUN}`

