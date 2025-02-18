## Descripcion
There's an interesting script in the user's home directory

Additional details will be available after launching your challenge instance.

## Hints
None

## Solucion
Lo primero que debemos de realizar es activar la instancia privada. 
Una vez que se prendio la instancia, nos da la informacion para conectarnos a la maquina por medio de ssh. 
Nos conectamos por medio del siguiente comando: 
- `ssh -p 65193 picoplayer@saturn.picoctf.net`
Enseguida nos pedira la contraseña del usuario picoplayer que tambien es proporcionada, esta es `password`.
La descripcion nos dice que hay un script y que lo analicemos.
- Primero aplicamos un `cat` para ver el contenido del script
```
!/bin/bash
# Basic mathematical operations via command-line arguments

if [ $# != 3 ]
then
  echo "Read the code first"
else
	if [[ "$1" == "add" ]]
	then 
	  sum=$(( $2 + $3 ))
	  echo "The Sum is: $sum"  

	elif [[ "$1" == "sub" ]]
	then 
	  sub=$(( $2 - $3 ))
	  echo "The Substract is: $sub" 

	elif [[ "$1" == "div" ]]
	then 
	  div=$(( $2 / $3 ))
	  echo "The quotient is: $div" 

	elif [[ "$1" == "mul" ]]
	then
	  mul=$(( $2 * $3 ))
	  echo "The product is: $mul" 

	else
	  echo "Read the manual"
	 
	fi
fi

```
Analizando este script vemos que le tenemos que pasar tres parametros, estos parametros deben de ser la operacion a realizar, y los numeros con los cuales realizara la operacion, Pero en realidad este script no tiene la flag. 
Para obtener la flag, use el comando `man` que es el manual que viene en diferentes scripts y en este manual viene escondida la flag:

`picoCTF{us3l3ss_ch4ll3ng3_3xpl0it3d_5657}`

## Referencias

