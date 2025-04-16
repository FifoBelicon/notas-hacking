## Descripcion

Can you crack the password to get the flag?
Download the password checker here and you'll need the encrypted flag and the hash in the same directory too.
There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

## Hints

# Solucion
1. Descargamos el password checker, el hash y la flag encodeada que nos proporciona el reto.
2. Analizamos los archivos
	1. El hash y la flag viene con simbolos que no podemos entender
	2. Lo unico que tenemos es el script, que contiene 7 contraseñas que solo 1 es correcta
3. Podemos probar todas las contraseñas una por una, pero seria bastante tardado
4. Modificar el script para que itinere en cada contraseña de la lista de las contraseñas y me de la contraseña al ejecutar el script

Script original: 
```
flag_enc = open('level3.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level3.hash.bin', 'rb').read()


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_3_pw_check():
    user_pw = input("Please enter correct password for flag: ")
    user_pw_hash = hash_pw(user_pw)
    
    if( user_pw_hash == correct_pw_hash ):
        print("Welcome back... your flag, user:")
        decryption = str_xor(flag_enc.decode(), user_pw)
        print(decryption)
        return
    print("That password is incorrect")



level_3_pw_check()


# The strings below are 7 possibilities for the correct password. 
#   (Only 1 is correct)
pos_pw_list = ["f09e", "4dcf", "87ab", "dba8", "752e", "3961", "f159"]

```

Script modificado:
```

flag_enc = open('level3.flag.txt.enc', 'rb').read()
correct_pw_hash = open('level3.hash.bin', 'rb').read()
pos_pw_list = ["f09e", "4dcf", "87ab", "dba8", "752e", "3961", "f159"]


def hash_pw(pw_str):
    pw_bytes = bytearray()
    pw_bytes.extend(pw_str.encode())
    m = hashlib.md5()
    m.update(pw_bytes)
    return m.digest()


def level_3_pw_check():

    for password in pos_pw_list:
 
        password_hash = hash_pw(password)       

        if password_hash == correct_pw_hash:
            print("Welcome back... your flag, user:")
            decryption = str_xor(flag_enc.decode(), password)
            print(decryption)
            return 



level_3_pw_check()

```

Resultado:
```
picoCTF{m45h_fl1ng1ng_cd6ed2eb}

```

