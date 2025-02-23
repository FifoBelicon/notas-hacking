## Descripcion
What was I last working on? I remember writing a note to help me remember...You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/163/challenge.zip)

### Hints

- The `cat` command will let you read a file, but that won't help you here!
- Read the chapter on Git from the picoPrimer [here](https://primer.picoctf.org/#_git_version_control).
- When committing a file with git, a message can (and should) be included.
# Solucion

1. Debemos descargar el paquete que nos proporciona el reto
2. Descomprimir con el comando `unzip`
	1. ` unzip challenge.zip`
3. Nos dirigimos a la carpeta que nos genera:
	1. `cd drop-in`
4. Analizamos su contenido

si hacemos un `cat`al mensaje obtenemos lo siguiente:

```
$ cat message.txt                   
This is what I was working on, but I'd need to look at my commit history to know why...     
```

Si deseamos ver el comentario con el que se crea el commit necesitamos hacer uso del comando `log`
`└─$ git log message.txt  `

```
commit e65fedb3a72a16c577f4b17023b63997134b307d (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:29 2024 +0000

    picoCTF{t1m3m@ch1n3_88c35e3b}

```

## Referencias
