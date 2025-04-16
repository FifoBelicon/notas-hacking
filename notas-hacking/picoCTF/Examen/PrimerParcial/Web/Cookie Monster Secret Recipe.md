## Descripcion
Cookie Monster has hidden his top-secret cookie recipe somewhere on his website. As an aspiring cookie detective, your mission is to uncover this delectable secret. Can you outsmart Cookie Monster and find the hidden recipe?You can access the Cookie Monster [here](http://verbal-sleep.picoctf.net:49480/) and good luck

## Hints
- Sometimes, the most important information is hidden in plain sight. Have you checked all parts of the webpage?
- Cookies aren't just for eating - they're also used in web technologies!
- Web browsers often have tools that can help you inspect various aspects of a webpage, including things you can't see directly.

# Solucion

Analizamos la pagina y lo primero que encontramos es un panel de login. Asi que me loggeo con credenciales comunes como `admin:admin`, vemos que nos da acceso y nos muestra esto: 
```
# Access Denied

Cookie Monster says: 'Me no need password. Me just need cookies!'

Hint: Have you checked your cookies lately?
```

Capturo la peticion con burpsuite y accedo de nuevo con el repeater, para ver la respuesta:

```
HTTP/1.1 200 OK
Date: Wed, 16 Apr 2025 03:01:01 GMT
Server: Apache/2.4.54 (Debian)
X-Powered-By: PHP/7.4.33
Set-Cookie: secret_recipe=cGljb0NURntjMDBrMWVfbTBuc3Rlcl9sMHZlc19jMDBraWVzX0FDOEZDRDc1fQ%3D%3D; expires=Wed, 16-Apr-2025 04:01:01 GMT; Max-Age=3600; path=/
Vary: Accept-Encoding
Content-Length: 167
Keep-Alive: timeout=5, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=UTF-8

<h1>Access Denied</h1><p>Cookie Monster says: 'Me no need password. Me just need cookies!'</p><p>Hint: Have you checked your cookies lately?</p><a href='/'>Go back</a>
```

Vemos que hay una variable que dice `secret_recipe` en donde copio su valor y burpsuite tiene un decodificador de base 64, y este me da la flag:

```
picoCTF{c00k1e_m0nster_l0ves_c00kies_AC8FCD75}
```

## Referencias
