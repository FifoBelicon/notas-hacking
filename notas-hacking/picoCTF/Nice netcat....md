## Descripcion
There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 7449`, but it doesn't speak English...

## Solucion
Lo primero que debemos hacer para resolver este reto sera conectarnos por medio de netcat a la direccion que nos da el reto y analizemos la salida:
![[Pasted image 20250213001425.png]]
Al ver esta salida y analizar la HINT podemos deducir que se estos numeros se podrian tratar a una letra en el codigo ASCII, vamos a comprobarlo:
![[Pasted image 20250213002337.png]]
Buscamos el valor que da la salida con el valor decimal a los valores ASCII y forma la siguiente palabra:
- `picoCTF{g00d_k1tty!_n1c3_k1tty!f2d7cafa}`
## Referencias

- https://www.asciitable.com/
