
# Descripcion
We have several pages hidden. Can you find the one with the flag?The website is running [here](http://saturn.picoctf.net:62978/).

## Hints
- folders folders folders

## Solucion

Por el nombre del reto, la flag esta escondida en toda la estructura de la pagina web, asi que en este caso en lugar de adiviar las posibles carpetas hago uso de una herramienta de escaneo de sitios web que permite la recursion, para buscar en directorios dentro de directorios. Esta herramienta es `feroxbuster`

comando:

`feroxbuster -u http://saturn.picoctf.net:62978/ -w /usr/share/wordlists/dirb/common.txt `

Analizamos la salida:

```
 |__  |__) |__) | /  `    /  \ \_/ | |  \ |__
|    |___ |  \ |  \ | \__,    \__/ / \ | |__/ |___
by Ben "epi" Risher 🤓                 ver: 2.11.0
───────────────────────────┬──────────────────────
 🎯  Target Url            │ http://saturn.picoctf.net:62978/
 🚀  Threads               │ 50
 📖  Wordlist              │ /usr/share/wordlists/dirb/common.txt
 👌  Status Codes          │ All Status Codes!
 💥  Timeout (secs)        │ 7
 🦡  User-Agent            │ feroxbuster/2.11.0
 💉  Config File           │ /etc/feroxbuster/ferox-config.toml
 🔎  Extract Links         │ true
 🏁  HTTP methods          │ [GET]
 🔃  Recursion Depth       │ 4
───────────────────────────┴──────────────────────
 🏁  Press [ENTER] to use the Scan Management Menu™
──────────────────────────────────────────────────
404      GET        7l       11w      153c Auto-filtering found 404-like response and created new filter; toggle off with --dont-filter
200      GET       65l      162w     1121c http://saturn.picoctf.net:62978/secret/assets/index.css
200      GET      117l      834w     6573c http://saturn.picoctf.net:62978/contact.html
200      GET       28l       55w      674c http://saturn.picoctf.net:62978/about.html
403      GET        7l        9w      153c http://saturn.picoctf.net:62978/secret/assets/
200      GET        0l        0w        0c http://saturn.picoctf.net:62978/secret/hidden/file.css
200      GET       12l       41w      468c http://saturn.picoctf.net:62978/secret/
200      GET      478l     3005w   297974c http://saturn.picoctf.net:62978/secret/assets/DX1KYM.jpg
200      GET       36l       81w     1023c http://saturn.picoctf.net:62978/
200      GET      122l      300w     2087c http://saturn.picoctf.net:62978/secret/hidden/superhidden/login.css
200      GET       73l      150w     2118c http://saturn.picoctf.net:62978/secret/hidden/
200      GET       10l       21w      143c http://saturn.picoctf.net:62978/secret/hidden/superhidden/mycss.css
200      GET       12l       24w      255c http://saturn.picoctf.net:62978/secret/hidden/superhidden/
301      GET        7l       11w      169c http://saturn.picoctf.net:62978/secret/assets => http://saturn.picoctf.net/secret/assets/
200      GET       36l       81w     1023c http://saturn.picoctf.net:62978/index.html
301      GET        7l       11w      169c http://saturn.picoctf.net:62978/secret/hidden => http://saturn.picoctf.net/secret/hidden/
200      GET       12l       41w      468c http://saturn.picoctf.net:62978/secret/index.html
200      GET       73l      150w     2118c http://saturn.picoctf.net:62978/secret/hidden/index.html
200      GET       12l       24w      255c http://saturn.picoctf.net:62978/secret/hidden/superhidden/index.html
301      GET        7l       11w      169c http://saturn.picoctf.net:62978/secret => http://saturn.picoctf.net/secret/
500      GET        7l       13w      177c http://saturn.picoctf.net:62978/secret/hidden/property
500      GET        7l       13w      177c http://saturn.picoctf.net:62978/secret/req
500      GET        7l       13w      177c http://saturn.picoctf.net:62978/secret/hidden/psd
500      GET        7l       13w      177c http://saturn.picoctf.net:62978/secret/reprints
500      GET        7l       13w      177c http://saturn.picoctf.net:62978/secret/hidden/psp
500      GET        7l       13w      177c http://saturn.picoctf.net:62978/secret/assets/resize
500      GET        7l       13w      177c http://saturn.picoctf.net:62978/secret/assets/resolve
500      GET        7l       13w      177c http://saturn.picoctf.net:62978/secret/hidden/pt_BR
500      GET        7l       13w      177c http://saturn.picoctf.net:62978/send_to_friend

```

Analizo el ultimo sitio que dio un codigo de respuesta 200: `http://saturn.picoctf.net:62978/secret/hidden/superhidden/index.html
`
Entramos a la pagina y analizamos:

![](images/secretimage.png)

Ahora analizo el codigo fuente:

```
<!DOCTYPE html>
<html>
  <head>
    <title></title>
    <link rel="stylesheet" href="[mycss.css](view-source:http://saturn.picoctf.net:62978/secret/hidden/superhidden/mycss.css)" />
  </head>

  <body>
    <h1>Finally. You found me. But can you see me</h1>
    <h3 class="flag">picoCTF{succ3ss_@h3n1c@10n_51b260fe}</h3>
  </body>
</html>
```

# Referencias
