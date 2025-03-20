# Descripcion

Kishor Balan tipped us off that the following code may need inspection: `https://jupiter.challenges.picoctf.org/problem/9670/` ([link](https://jupiter.challenges.picoctf.org/problem/9670/)) or http://jupiter.challenges.picoctf.org:9670

## Hints
- How do you inspect web code on a browser?
- There's 3 parts

## Solucion

1. Lo primero que debemos de hacer es analizar la pagina.
2. En esta pagina al explorar un poco, si hacemos click en el apartado `how`, podemos observar que dice este sitio web con html, js y css
3. Usamos `ctrl + u ` y tenemos este codigo fuente.

```
|   |   |
|---|---|
||<!doctype html>|
||<html>|
||<head>|
||<title>My First Website :)</title>|
||<link href="[https://fonts.googleapis.com/css?family=Open+Sans\|Roboto](https://fonts.googleapis.com/css?family=Open+Sans\|Roboto)" rel="stylesheet">|
||<link rel="stylesheet" type="text/css" href="[mycss.css](https://jupiter.challenges.picoctf.org/problem/9670/mycss.css)">|
||<script type="application/javascript" src="[myjs.js](https://jupiter.challenges.picoctf.org/problem/9670/myjs.js)"></script>|
||</head>|
|||
||<body>|
||<div class="container">|
||<header>|
||<h1>Inspect Me</h1>|
||</header>|
|||
||<button class="tablink" onclick="openTab('tabintro', this, '#222')" id="defaultOpen">What</button>|
||<button class="tablink" onclick="openTab('tababout', this, '#222')">How</button>|
|||
||<div id="tabintro" class="tabcontent">|
||<h3>What</h3>|
||<p>I made a website</p>|
||</div>|
|||
||<div id="tababout" class="tabcontent">|
||<h3>How</h3>|
||<p>I used these to make this site: <br/>|
||HTML <br/>|
||CSS <br/>|
||JS (JavaScript)|
||</p>|
||<!-- Html is neat. Anyways have 1/3 of the flag: picoCTF{tru3_d3 -->|
||</div>|
|||
||</div>|
|||
||</body>|
||</html>|
|||

```

1. Al analizar este html, obtenemos la primera parte de la flag:
	```1. Anyways have 1/3 of the flag: picoCTF{tru3_d3``` 

2. Ahora, tenemos dos referencias a codigos, uno que es `mycss.css` y `myjs.js` analizamos cada uno.

mycss.css:
```
div.container {
    width: 100%;
}

header {
    background-color: black;
    padding: 1em;
    color: white;
    clear: left;
    text-align: center;
}

body {
    font-family: Roboto;
}

h1 {
    color: white;
}

p {
    font-family: "Open Sans";
}

.tablink {
    background-color: #555;
    color: white;
    float: left;
    border: none;
    outline: none;
    cursor: pointer;
    padding: 14px 16px;
    font-size: 17px;
    width: 50%;
}

.tablink:hover {
    background-color: #777;
}

.tabcontent {
    color: #111;
    display: none;
    padding: 50px;
    text-align: center;
}

#tabintro { background-color: #ccc; }
#tababout { background-color: #ccc; }

/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */
```

Aqui esta la segunda parte de la flag:
- `/* You need CSS to make pretty pages. Here's part 2/3 of the flag: t3ct1ve_0r_ju5t */`

myjs.js
```
/* Javascript sure is neat. Anyways part 3/3 of the flag: _lucky?2e7b23e3} */
```

Aqui esta la tercera parte y formamos la flag:

```
picoCTF{tru3_d3t3ct1ve_0r_ju5t_lucky?2e7b23e3}
```

## Referencias

