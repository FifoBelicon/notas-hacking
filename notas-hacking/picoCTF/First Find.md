
## Descripcion

Unzip this archive and find the file named 'uber-secret.txt'
### Hints

## Solucion

Usamos el comando find que sirve para encontrar archivos en una ruta determinada. 
- 1.- Descomprimir el archivo
	- `unzip files`
- 2.- Usar el comando find para encontrar el archivo `uber-secret-txt`
	- `find -type f -name "uber-secret.txt"`
	- `-type` para indicar de que tipo el archivo que buscamos, en este caso f de `file` 
- 3.- Una vez que tenemos en donde se encuentra el archivo, necesitamos leer el archivo con el comando `cat`
	- `cat adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/uber-secret.txt `
- 4.- Ingresar la flag:
	- `picoCTF{f1nd_15_f457_ab443fd1}`   

## Referencias
