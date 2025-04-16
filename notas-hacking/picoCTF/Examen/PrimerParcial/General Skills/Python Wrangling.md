# Descripcion
Python scripts are invoked kind of like programs in the Terminal... Can you run [this Python script](https://mercury.picoctf.net/static/8e33ede04d02f3765b8c6a6e24d72733/ende.py) using [this password](https://mercury.picoctf.net/static/8e33ede04d02f3765b8c6a6e24d72733/pw.txt) to get [the flag](https://mercury.picoctf.net/static/8e33ede04d02f3765b8c6a6e24d72733/flag.txt.en)?

# Hints
- Get the Python script accessible in your shell by entering the following command in the Terminal prompt: `$ wget https://mercury.picoctf.net/static/8e33ede04d02f3765b8c6a6e24d72733/ende.py`
- $ man python

# Solucion

Lo primero que tenemos que hacer es descargar los tres archivos de este reto, uno que es el script de python, la contraseña y la bandera encriptada.

Una vez que realizamos esto probamos el funcionamiento del script de python:

```
$ python3 ende.py   
Usage: ende.py (-e/-d) [file]
```

Aqui nos dice la forma de usar el script, en este caso nos presenta dos parametros para el documento que le tenemos que mandar. En este caso como nos manda una bandera encriptada, supongo que la `d` significa `decode` y la `e` `encode`, por lo tanto elijo la opcion d

```
python3 ende.py -d flag.txt.en 
Please enter the password:
```

Ahora nos pide la contraseña, que tambien descargamos del reto, por lo que solo la copio y la pego:

```
$ python3 ende.py -d flag.txt.en 
Please enter the password:aa821c16aa821c16aa821c16aa821c16
picoCTF{4p0110_1n_7h3_h0us3_aa821c16}

```

## Referencias

