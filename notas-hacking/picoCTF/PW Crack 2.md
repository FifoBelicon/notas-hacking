Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/10/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/10/level1.flag.txt.enc) in the same directory too.

## Hints

# Solucion

- Descargamos la flag que esta encodeada y necesita una contraseña para revelar su contenido y el script para desencodear la flag
- Primero corremos el codigo para desencodear la flag para probar y vemos que este pide una contraseña
	- ¿Como obtenemos esta constraseña?
- Analisamos el codigo del verificador de la contraseña y nos encontramos algo curioso...

```

flag_enc = open('level2.flag.txt.enc', 'rb').read()



def level_2_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == chr(0x33) + chr(0x39) + chr(0x63) + chr(0x65) ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_2_pw_check()



```

Observamos que la contraseña esta oculta  en la verificacion, pero la verificacion muestra cada caracter del codigo ASCII, por lo que podemos buscar los caracteres en la tabla ASCII y armar la contraseña.
- chr(0x33) = 3
- chr(0x39) = 9
- chr(0x63) = c
- chr(0x65) = e
Armamos la contraseña `39ce` y la ingresamos.
- Asi obtenemos la flag:

```
picoCTF{tr45h_51ng1ng_502ec42e}
```

## Referencias

