# Descripcion
Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag.The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden.The website is running [picoCTF News](http://verbal-sleep.picoctf.net:51506/).

# Hints
- Explore backend development with us
- The head was dumped.

# Solucion

Lo primero que hacemos es un analisis al sito web. Es una web en donde encontramos diferente informacion. Investigando en la web encontramos una seccion de API en donde nos explica el funcionamiento de estas API. 

Encontramos la que dice heapdump, que se parece mucho al nokbre del reto.

Podemos ver como se ejecuta y la pagina nos da la opcion de descargar la respuesta.

Si le hacemos un cat a ese archivo nos desglosa mucho contenido, asi que usare un grep para ver si en la respuesta esta la flag:

- `grep -r "picoCTF" heapdump-1744774358698.heapsnapshot`
Encontramos la flag:

```
picoCTF{Pat!3nt_15_Th3_K3y_f1179e46}

```