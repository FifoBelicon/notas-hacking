
# Descripcion

How about some hide and seek?Download this file [here](https://artifacts.picoctf.net/c_titan/130/unknown.zip).

## Hints

- How can you view the information about the picture?
- If something isn't in the expected form, maybe it deserves attention?

## Solution

Descomprimimos el archivo .zip

```
└─$ unzip unknown.zip       
Archive:  unknown.zip
  inflating: ukn_reality.jpg         
                              
```

Utilizamos el comando `exiftool` , que nos sirve para observar, escribir, y editar metadatos en archivo multimedia, principalmente imágenes y video.

Lo aplicamos al archivo jpg

```
└─$ exiftool ukn_reality.jpg 
ExifTool Version Number         : 13.10
File Name                       : ukn_reality.jpg
Directory                       : .
File Size                       : 2.3 MB
File Modification Date/Time     : 2024:02:15 16:40:14-06:00
File Access Date/Time           : 2024:02:15 16:40:14-06:00
File Inode Change Date/Time     : 2025:05:12 13:55:51-06:00
File Permissions                : -rw-r--r--
File Type                       : JPEG
File Type Extension             : jpg
MIME Type                       : image/jpeg
JFIF Version                    : 1.01
Resolution Unit                 : inches
X Resolution                    : 72
Y Resolution                    : 72
XMP Toolkit                     : Image::ExifTool 11.88
Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fZGVjYTA2ZmJ9Cg==
Image Width                     : 4308
Image Height                    : 2875
Encoding Process                : Baseline DCT, Huffman coding
Bits Per Sample                 : 8
Color Components                : 3
Y Cb Cr Sub Sampling            : YCbCr4:2:0 (2 2)
Image Size                      : 4308x2875
Megapixels                      : 12.4

```

```
Attribution URL                 : cGljb0NURntNRTc0RDQ3QV9ISUREM05fZGVjYTA2ZmJ9Cg==
```

Observamsos en atribution URL, se ve una cadena de caracteres URL en base64, donde posiblemente sea la bandera

```
picoCTF{ME74D47A_HIDD3N_6a9f5ac4}
```

