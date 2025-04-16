
## Descripcion

I accidentally wrote the flag down. Good thing I deleted it!You download the challenge files here:
- [challenge.zip](https://artifacts.picoctf.net/c_titan/77/challenge.zip)

## Hints
- Version control can help you recover files if you change or lose them!
- Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control)
- You can 'checkout' commits to see the files inside them

## Solucion

1. Debemos descargar el paquete que nos proporciona el reto
2. Descomprimir con el comando `unzip`
	1. ` unzip challenge.zip`
3. Nos dirigimos a la carpeta que nos genera:
	1. `cd drop-in`
4. Analizamos su contenido
En este caso el mensaje que encontramos es `TOP SECRET` y si hacemos un log podemos ver que primero se creo la flag y luego se borro la flag.

```
git log message.txt        
commit e1237df82d2e69f62dd53279abc1c8aeb66f6d64 (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:10:14 2024 +0000

    remove sensitive info

commit 3d5ec8a26ee7b092a1760fea18f384c35e435139
Author: picoCTF <ops@picoctf.com>
Date:   Sat Mar 9 21:10:14 2024 +0000

    create flag

```

Gracias a este comando podemos ver el identificador del commit de cuando se subio la flag. 

Hacemos uso del comando checkout para dirigirnos a esa version del repositorio cuando se creo la flag:

- ` git checkout 3d5ec8a26ee7b092a1760fea18f384c35e435139`
Una vez estamos estamos en la version del commit si hacemos un cat al mensaje deberiamos tener la flag:

```
picoCTF{s@n1t1z3_30e86d36}

```

## Referencias
- https://primer.picoctf.org/#_git_version_control
