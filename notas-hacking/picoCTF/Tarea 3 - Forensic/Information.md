## Description

Files can always be changed in a secret way. Can you find the flag? [cat.jpg](https://mercury.picoctf.net/static/b4d62f6e431dc8e563309ea8c33a06b3/cat.jpg)

## Hint

- Look at the details of the file Make sure to submit the flag as picoCTF{XXXXX}
## Solution

Utilizamos el comando hexeditor` para ver y editar archivos en foramto hexadecimal.

A lado de la derecha observamos lo siguiente, el inicio de la bandera:

```
  <cc:license rdf:resource='cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9'/>
 </rdf:Description>

 <rdf:Description rdf:about=''
  xmlns:dc='http://purl.org/dc/elements/1.1/'>
  <dc:rights>
   <rdf:Alt>
    <rdf:li xml:lang='x-default'>PicoCTF</rdf:li>
   </rdf:Alt>
  </dc:rights>
 </rdf:Description>
</rdf:RDF>
</x:xmpmeta>
```

Posiblemente ahí se encuentre la bandera, pero en formato hexadecimal

`resource='cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9`

Utilizamos el cyber chef

 ```
 picoCTF{the_m3tadata_1s_modified}
 ```
 