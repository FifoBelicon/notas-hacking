
## Description

Every file gets a flag.The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye [here](https://artifacts.picoctf.net/c/259/flag.png).

## Hints

None
## Solution

Aplicamos un `strings` a `flag.png`: 

De todo lo que nos muestra existe algo interesante: 

```
7`_QB\\
##ib{
RP0x3
--e^
I|L_
[u]mC
secret/UT
pVgE#
secret/flag.png  <---------
```


Se utiliza la herramienta `binwalk`, es una herramienta forense que analiza archivos binarios en busca de firmas que correspondan a archivos embebidos o estructuras conocidas: como imágenes, archivos comprimidos, ejecutables. 

```
└─$ binwalk -e flag.png                   

DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
41            0x29            Zlib compressed data, compressed
39739         0x9B3B          Zip archive data, at least v1.0 to extract, name: secret/
39804         0x9B7C          Zip archive data, at least v2.0 to extract, compressed size: 2869, uncompressed size: 3024, name: secret/flag.png

WARNING: One or more files failed to extract: either no utility was found or it's unimplemented

```


```
                                                        
└─$ ls
flag.png  _flag.png.extracted
```

```													
└─$ cd _flag.png.extracted/secret
```

```
[~/forensic3/hideme/_flag.png.extracted/secret]
└─$ open flag.png 
```

```
picoCTF{Hidd1ng_An_1mag3_within_@n_1mag3_82101824}

```

