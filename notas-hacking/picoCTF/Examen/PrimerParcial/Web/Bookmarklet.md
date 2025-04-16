
## Descripcion
Why search for the flag when I can make a bookmarklet to print it for me?Browse [here](http://titan.picoctf.net:58040/), and find the flag!

# Hints
- A bookmarklet is a bookmark that runs JavaScript instead of loading a webpage.
- What happens when you click a bookmarklet?
- Web browsers have other ways to run JavaScript too.

# Solucion

Lo primero que hacemos es un hacer un analisis del sitio web. Lo unico que muestra es un codigo js que es la funcion para desencriptar la flag.
Lo que tenemos que hacer es una forma de lograr cargar codigo de javascript. Siguiendo las hints, lo primero que hago es crear un nuevo bookmark, ingreso como nombre `flag` en el campo de nombre y agrego en una linea el codigo de javascript que la pagina web me manda:
`javascript:(function() { var encryptedFlag = "àÒÆÞ¦È¬ëÙ£ÖÓÚåÛÑ¢ÕÓÉÕËÆÒÇÚËí"; var key = "picoctf"; var decryptedFlag = ""; for (var i = 0; i < encryptedFlag.length; i++) { decryptedFlag += String.fromCharCode((encryptedFlag.charCodeAt(i) - key.charCodeAt(i % key.length) + 256) % 256); } alert(decryptedFlag); })();
`

Esto lo agregamos en el campo de url. Ahora si hacemos click en este bookmark vemos que nos da un pop up con la flag. Esto ya que una forma de ejecutar codigos de js es por medio de los bookmarks

```
picoCTF{p@g3_turn3r_cebccdfe}
```