
# Descripcion
Do you know how to use the web inspector?Start searching [here](http://titan.picoctf.net:54443/) to find the flag

## Hints
- Use the web inspector on other files included by the web page.
- The flag may or may not be encoded

# Solucion

Lo primero que hago es analizar la pagina, comienzo a manipular la pagina web, cada vez que busco en los diferentes indices, encuentro pistar acerca de lo cerca que estoy de la flag. En la pagina `about us` inspecciono el codigo fuente de la pagina:

```
|   |   |
|---|---|
||<!DOCTYPE html>|
||<html lang="en">|
||<head>|
||<meta charset="utf-8"/>|
||<meta content="IE=edge" http-equiv="X-UA-Compatible"/>|
||<meta content="width=device-width, initial-scale=1.0" name="viewport"/>|
||<link href="[style.css](http://titan.picoctf.net:54443/style.css)" rel="stylesheet"/>|
||<link href="[img/favicon.png](http://titan.picoctf.net:54443/img/favicon.png)" rel="shortcut icon" type="image/x-icon"/>|
||<!-- font (google) -->|
||<link href="[https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,400;0,700;1,400&amp;display=swap](https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,400;0,700;1,400&display=swap)" rel="stylesheet"/>|
||<title>|
||About me|
||</title>|
||</head>|
||<body>|
||<header>|
||<nav>|
||<div class="logo-container">|
||<a href="[index.html](http://titan.picoctf.net:54443/index.html)">|
||<img alt="logo" src="[img/binding_dark.gif](http://titan.picoctf.net:54443/img/binding_dark.gif)"/>|
||</a>|
||</div>|
||<div class="navigation-container">|
||<ul>|
||<li>|
||<a href="[index.html](http://titan.picoctf.net:54443/index.html)">|
||Home|
||</a>|
||</li>|
||<li>|
||<a href="[about.html](http://titan.picoctf.net:54443/about.html)">|
||About|
||</a>|
||</li>|
||<li>|
||<a href="[contact.html](http://titan.picoctf.net:54443/contact.html)">|
||Contact|
||</a>|
||</li>|
||</ul>|
||</div>|
||</nav>|
||</header>|
||<section class="about" notify_true="cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMWY4MzI2MTV9">|
||<h1>|
||Try inspecting the page!! You might find it there|
||</h1>|
||<!-- .about-container -->|
||</section>|
||<!-- .about -->|
||<section class="why">|
||<footer>|
||<div class="bottombar">|
||Copyright © 2023 Your_Name. All rights reserved.|
||</div>|
||</footer>|
||</section>|
||</body>|
||</html>|
```

Hay un elemento que me parece sospechoso que es el `notify_true="cGljb0NURnt3ZWJfc3VjYzNzc2Z1bGx5X2QzYzBkZWRfMWY4MzI2MTV9"`

Asi que tomo el valor de la variable e intento decodificar para saber que es lo que contiene:

![](images/flagWebDecode.png)

## Referencias

