
## Descripcion
Fix the syntax error in this Python script to print the flag.

## Hints

# Solucion

- Lo primero que tenemos que realizar es descargar el script de python que el reto nos da.
- Segun la descripcion hay un error de SINTAXIS y necesitamos arreglarlo para mostrar la flag
- Hago uso de la herramienta `nano` para visualizar y editar el script.
- Hacemos un analisis del codigo
- Encontramos que no hay nada sospechoso en la funcion, pero justo al final para imprimir la bandera hay algo raro, unos cuantos espacios. En python la identacion es bastante importante ya que esta es la encargada dee encapsular codigo, cuando una linea esta indentada y esta linea no esta dentro de una sentencia de control esta linea dara un error.
- En este caso hay que eliminar estos espacios para que el script funcione

```
import random



def str_xor(secret, key):
    #extend key to secret length
    new_key = key
    i = 0
    while len(new_key) < len(secret):
        new_key = new_key + key[i]
        i = (i + 1) % len(key)        
    return "".join([chr(ord(secret_c) ^ ord(new_key_c)) for (secret_c,new_key_c) in zip(secret,new_key)])


flag_enc = chr(0x15) + chr(0x07) + chr(0x08) + chr(0x06) + chr(0x27) + chr(0x21) + chr(0x23) + chr(0x15) + chr(0x5a) + chr(0x07) + chr(0x00) + chr(0x46) + chr(0x0b) + chr(0x1a) + chr(0x5a) + chr(0x1d) + chr(0x1d) + chr(0x2a) + chr(0x06) + chr(0x1c) + chr(0x5a) + chr(0x5c) + chr(0x55) + chr(0x40) + chr(0x3a) + chr(0x58) + chr(0x0a) + chr(0x5d) + chr(0x53) + chr(0x43) + chr(0x06) + chr(0x56) + chr(0x0d) + chr(0x14)

  
flag = str_xor(flag_enc, 'enkidu')
  print('That is correct! Here\'s your flag: ' + flag)
  ^ Aqui esta el error de indentacion

```

- Arreglado este problema obtenemos la flag;
```
That is correct! Here's your flag: picoCTF{1nd3nt1ty_cr1515_6a476c8f}
```