## Descripcion

There is a website running at `https://jupiter.challenges.picoctf.org/problem/33850/` ([link](https://jupiter.challenges.picoctf.org/problem/33850/)) or http://jupiter.challenges.picoctf.org:33850. Do you think you can log us in? Try to see if you can login

> Hints
> 	There doesn't seem to be many ways to interact with this. I wonder if the users are kept in a database?
> 	Try to think about how the website verifies your login.


# Solucion

Lo primero que tenemos que es analizar la pagina que se nos proporciona
- En este caso es una recopilacion de varias celebridades.
- Existe un panel de login para ser admin

Para loggearme intente lo siguiente:
1. Intente con credenciales comunes como admin:admin , admin:admin , admin: admin123, etc...
Ninguna de estas credenciales me funciono.
2. Segun la hint dice que pasaria si hubiera una base de datos con los usuarios, dicho esto proble la injection sql mas famosa
```
' OR 1=1-- -
```
Esta inyeccion estaria terminando el campo de user cerrandolo con la `' ` despues evalua la expresion 1=1 que simpre sera verdadera y despues comenta lo que hay despues en la sentencia de base de datos

Para mi sorpresa intente esta injection y obtuve la flag:

```
picoCTF{s0m3_SQL_f8adf3fb}
```

## Referencias
