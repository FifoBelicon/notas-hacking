## Descripcion
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/71/challenge.zip)

### Hints
- `git branch -a` will let you see available branches
- How can file 'diffs' be brought to the main branch? Don't forget to `git config`!
- Merge conflicts can be tricky! Try a text editor like nano, emacs, or vim.

# Solucion

1. Debemos descargar el paquete que nos proporciona el reto
2. Descomprimir con el comando `unzip`
	1. ` unzip challenge.zip`
3. Nos dirigimos a la carpeta que nos genera:
	1. `cd drop-in`
4. Analizamos su contenido
En este caso el contenido lo que encontramos es la flag, pero si la ejecutamos solo nos encontramos con un mensaje de control, pero no con la flag. 

- Tenemos que fijarnos si tiene mas ramas aparte de la original o la descripcion del commit
-  Ver las ramas:
	- ` git branch -a ` 
Podemos ver que hay algo curioso en estas ramas, y es que muestra una caracteristica por partes (partes 1,2 y 3), para poder ver el contenido que hay en esas ramas usamos el comando checkout.
- `git checkout feature/part-1  `
Ahora si corremos el script que viene obtendremos la primera parte de la flag:
```
Printing the flag...
picoCTF{t3@mw0rk_ 
```

Por lo tanto ahora tenemos que movernos entre las ramas para obtener la flag completa:

flag:
```
1) parte: picoCTF{t3@mw0rk_ 
2) parte: m@k3s_th3_dr3@m_   
3) parte: w0rk_4c24302f}

picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_4c24302f}

```

## Referencias
