
## Descripcion
Can you crack the password to get the flag?Download the password checker [here](https://artifacts.picoctf.net/c/10/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/10/level1.flag.txt.enc) in the same directory too.

## Hints

# Solucion

- Descargamos la flag que esta encodeada y necesita una contraseña para revelar su contenido y el script para desencodear la flag
- Primero corremos el codigo para desencodear la flag para probar y vemos que este pide una contraseña
	- ¿Como obtenemos esta constraseña?
- Analisamos el codigo del verificador de la contraseña y nos encontramos algo curioso...

```
flag_enc = open('level1.flag.txt.enc', 'rb').read()



def level_1_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    if( user_pw == "691d"):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")


```

Observamos que la contraseña esta visible en la verificacion, por lo que escribimos esta contraseña en la ejecucion del programa, y wow, obtenemos la flag :)

```
picoCTF{545h_r1ng1ng_56891419}
```

## Referencias

