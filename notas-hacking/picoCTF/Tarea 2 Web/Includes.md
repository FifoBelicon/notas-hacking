# Descripcion

Can you get the flag?

Additional details will be available after launching your challenge instance.

# Hints
- Is there more code than what the inspector initially shows?

## Solucion

Una vez que comence la instancia accedo a la pagina web. Lo primero que tenemos que hacer es explorar la pagina e identificar posibles vectores. Tiene un boton para decir `hello`. Pero leyendo la pista del reto busco el codigo fuente de la pagina (`ctrl + u` )

```

|   |   |
|---|---|
||<!DOCTYPE html>|
||<html lang="en">|
||<head>|
||<meta charset="UTF-8">|
||<meta name="viewport" content="width=device-width, initial-scale=1.0">|
||<meta http-equiv="X-UA-Compatible" content="ie=edge">|
||<link rel="stylesheet" href="[style.css](http://saturn.picoctf.net:50105/style.css)">|
||<title>On Includes</title>|
||</head>|
||<body>|
||<script src="[script.js](http://saturn.picoctf.net:50105/script.js)"></script>|
|||
||<h1>On Includes</h1>|
||<p>Many programming languages and other computer files have a directive,|
||often called include (sometimes copy or import), that causes the|
||contents of a second file to be inserted into the original file. These|
||included files are called copybooks or header files. They are often used|
||to define the physical layout of program data, pieces of procedural code|
||and/or forward declarations while promoting encapsulation and the reuse|
||of code.</p>|
||<br>|
||<p> Source: Wikipedia on Include directive </p>|
||<button type="button" onclick="greetings();">Say hello</button>|
||</body>|
||</html>|

```

En este caso podemos observar que tiene codigos que son accesibles: `href="[style.css]` y  `script src="[script.js]`. Procedemos a analizar para ver si hay algo sospechoso.

- style.css
```
body {
  background-color: lightblue;
}

/*  picoCTF{1nclu51v17y_1of2_  */
```

Observamos que viene la flag, pero parece que esta incompleta, asi que seguimos buscando.

- script.js
```
function greetings()
{
  alert("This code is in a separate file!");
}

//  f7w_2of2_df589022}
```

Asumo que esta es la segunda y ultima parte de la llave, ya que tiene la llave que cierra `}`.

Flag: 

```
picoCTF{1nclu51v17y_1of2_f7w_2of2_df589022}
```

## Referencias
