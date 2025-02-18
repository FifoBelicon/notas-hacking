## Descripcion
Can you find the flag in [file](https://jupiter.challenges.picoctf.org/static/5bd86036f013ac3b9c958499adf3e2e2/strings) without running it?

### Hints
strings

## Solucion
El comando strings es similar al comando 'cat' y este tambien sirve para leer archivos...
- Aplicamos el comando strings para leer el archivo 'strings' que descargamos
- `strings strings`
Al ejecutar este comando observamos que nos muestra la salida del archivo strings, el cual es bastante extensa, por lo que buscamos concatenar un comando para ver si la flag se encuentra escondida en ese archivo:
- `strings strings | grep 'picoCTF' `
Obtenemos la siguiente salida:
```
picoCTF{5tRIng5_1T_827aee91}

```

## Referencias
https://linux.die.net/man/1/strings