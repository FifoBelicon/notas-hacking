
# Descripcion

This website can be rendered only by **picobrowser**, go and catch the flag! `https://jupiter.challenges.picoctf.org/problem/26704/` ([link](https://jupiter.challenges.picoctf.org/problem/26704/)) or http://jupiter.challenges.picoctf.org:26704

# Hints
You don't need to download a new web browser

# Solucion

Lo primero que tenemos que hacer es analizar la pagina en la que nos encontramos.

-  Observamos un boton que dice flag, pero me dice que no tengo el picobrowser y me dice mi version de mi navegador web
- Capturo la peticion  usando burpsuite para observar de que forma se realiza este movimiento

```
GET /flag HTTP/1.1
Host: jupiter.challenges.picoctf.org:26704
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.120 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://jupiter.challenges.picoctf.org:26704/
Accept-Encoding: gzip, deflate, br
Connection: keep-alive


```

Ahora, pruebo modificando el apartado que dice `User-agent`

```
GET /flag HTTP/1.1
Host: jupiter.challenges.picoctf.org:26704
Accept-Language: en-US,en;q=0.9
Upgrade-Insecure-Requests: 1
User-Agent: picobrowser
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.7
Referer: http://jupiter.challenges.picoctf.org:26704/
Accept-Encoding: gzip, deflate, br
Connection: keep-alive



```

Le envio esta peticion por medio del repeater de burpsuite y obtengo la flag:

```
picoCTF{p1c0_s3cr3t_ag3nt_e9b160d0}
```


## Referencias

