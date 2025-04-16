## Descripcion
Someone's commits seems to be preventing the program from working. Who is it?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/74/challenge.zip)

## Hints
- In collaborative projects, many users can make many changes. How can you see the changes within one file?
- Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control).
- You can use `python3 <file>.py` to try running the code, though you won't need to for this challenge.

# Solucion

En este reto tenemos que saber quien fue la persona que hizo cmabios al documento que se encuentra en el paquete que nos da el reto. 
Hacemos uso del comando `unzip` para descomprimir el paquete. 
Ahora nos dirigimos a la carpeta:
- `cd drop-in`
Observamos que tenemos un solo archivo, pero que en su interior no tiene nada que nos interese por lo tanto.
- Hacemos uso del comando `log`en el cual git muestra el historial de las personas que hicieron cambios en el documento y vemos cual es el resultado:

```
git log message.py  
commit 0fe87f16cbd8129ed5f7cf2f6a06af6688665728
Author: picoCTF{@sk_th3_1nt3rn_ea346835} <ops@picoctf.com>
Date:   Sat Mar 9 21:09:25 2024 +0000

    optimize file size of prod code

commit 7e8a2415b6cca7d0d0002ff0293dd384b5cc900d
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:09:25 2024 +0000

    create top secret project

```
Obtenemos la flag :D

## Referencias

- https://primer.picoctf.org/#_git_version_control
