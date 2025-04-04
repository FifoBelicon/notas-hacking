
# Descripcion

The flag is somewhere on this web application not necessarily on the website. Find it.Check [this](http://saturn.picoctf.net:52411/) out.

## Hints
- None

# Solucion

Lo primero que hago es analizar la pagina y ver su funcionamiento, ahora que no vi algo sospechoso en la pagina, asi que analizo el codigo fuente. Por el nombre del reto busco la flag relacionandose con las fuentes de la pagina. Pero no encontre nada.

Procedo a buscar en el robots de la pagina y econtre esto:

```
User-agent *
Disallow: /cgi-bin/
Think you have seen your flag or want to keep looking.

ZmxhZzEudHh0;anMvbXlmaW
anMvbXlmaWxlLnR4dA==
svssshjweuiwl;oiho.bsvdaslejg
Disallow: /wp-admin/
```

Este texto parece sospechoso, asi que lo meto en `cyberchef` para analizarlo. Encuentro que este texto esta en base64 y obtengo el siguiente resultado:

```
/js/myfile.txt
```

Me dirijo a esta ruta a ver que hay:

```
picoCTF{Who_D03sN7_L1k5_90B0T5_032f1c2b}
```

## Referencias
