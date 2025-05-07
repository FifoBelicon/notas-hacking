
# Descripcion

I've hidden a flag in this file. Can you find it? [Forensics is fun.pptm](https://mercury.picoctf.net/static/9a7436948cc502e9cacf5bc84d2cccb5/Forensics%20is%20fun.pptm)

# Hints
None


# Solucion

Lo primero que hacemos en este reto es descargar el achivo que se nos proporciona. 
Este archivo es de powerpoint, por lo que me dirijo a abrirlo, pero me doy cuenta que este se cierra inmediatamente sin poder ver su contenido.

Con la herramienta `exiftool` veo los metadatos de este archivo, y no encuentro informacion relevante. 

Una forma de lograr de ver el contenido de este archivo es desempaquetandolo, obteniendo multiples carpetas, las que contienen todos los archivos que conforman este powerpoint. 

- `unzip Forensics is fun.pptm`

Esto nos genera las siguientes carpetas:
- `_rels`
- `docProps`
- `ppt`

Me pongo a analizar las carpetas en busca de la flag.

En la carpeta `ppt` tiene un subdirectorio llamado `slideMasters`
 que contiene un fichero llamado `hidden`  y me parece sospechoso.

El contenido de este archivo es el siguiente:
- `Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q`

Esto lo paso al cyberchef y veo que no me regresa ningun resultado.

Modifique esta cadena eliminando los espacios y ahora cyberchef me detecta que esta en base64. Una vez que lo decodificamos obtenemos lo siguiente:

```
picoCTF{D1d_u_kn0w_ppts_r_z1p5}
```

# Referencias

