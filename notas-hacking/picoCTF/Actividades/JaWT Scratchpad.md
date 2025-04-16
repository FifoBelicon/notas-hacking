
## Descripcion
Check the admin scratchpad! `https://jupiter.challenges.picoctf.org/problem/61864/` or http://jupiter.challenges.picoctf.org:61864

## Hints
- What is that cookie?
- Have you heard of JWT?

# Solucion

Primero analizamos la pagina, en este caso nos pide ingresar nuestro nombre. 
Lo ingresamos y nos da la bienvenida. Nos dice que el usuario admin y que tiene algo especial.

Ahi mismo en la pagina hay un enlace al reposito de `johntheripper` que es una herramienta de fuerza bruta, por lo que pienso que la usare mas adelante.

Siguiendo la hint, analizo las cookiesm, y me encuentro con una cookie llamada jwt con un valor de:
`eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoicGVkcm8ifQ.ECbGFWO43PRfcg4jREB3u78SX_2atDQmgH1OWC5JObI`

Segun JWT, esto esta en formato JSON, por lo que la informacion de mi inicio de secion esta codificada en base 64, algo asi:

```
"typ":"JWT","alg":"HS256"}{"user":"pedro"}
```
 La ultima parte de esta cookie, evita que haya modificaciones directa a las cookies, pero podemos hacer pasar la cookie como admin.

La cookie dice utiliza el algoritmo HS256 con john podemos descifrarla y obtener la contraseña que se utilizo. 

Guardo mi cookie en un txt y sigo corro el siguiente comando:

`john cookie.txt --format=HMAC-SHA256 --wordlist=/usr/share/wordlists/rockyou.txt

Y obtuve esta salida:
```
Using default input encoding: UTF-8
Loaded 1 password hash (HMAC-SHA256 [password is key, SHA256 128/128 SSE2 4x])
Will run 4 OpenMP threads
Press 'q' or Ctrl-C to abort, almost any other key for status
ilovepico        (?)     
1g 0:00:00:04 DONE (2025-03-26 22:13) 0.2136g/s 1580Kp/s 1580Kc/s 1580KC/s iloverob4live345..ilovemymother@
Use the "--show" option to display all of the cracked passwords reliably
Session completed. 

```


Veo que la contraseña que usaron para firmar fue `ilovepico`

Con esto, podemos firmar una cookie y hacerla pasar como administrador.

Uso la pagina https://jwt.io/ para agregar a mi cookie la contraseña y copio la cookie generada: 
`eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ1c2VyIjoicGVkcm8ifQ.ECbGFWO43PRfcg4jREB3u78SX_2atDQmgH1OWC5JObI`

- Nota, se tiene que modificar el usuario a admin y agregar en el secreto la contraseña `ilovepico`

- Darle guardar y actualizar

Flag:

```
picoCTF{jawt_was_just_what_you_thought_1ca14548}
```

# Referencias
https://jwt.io/
