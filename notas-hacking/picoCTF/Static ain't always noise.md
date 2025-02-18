## Descripcion
Can you look at the data in this binary: [static](https://mercury.picoctf.net/static/7495259e963bd5b67d0fb8b616652618/static)? This [BASH script](https://mercury.picoctf.net/static/7495259e963bd5b67d0fb8b616652618/ltdis.sh) might help!

## Hints
None

## Solucion
Lo primero que debemos de hacer es descargar los dos archivos y analizarlos por separado para entender lo que hacen.
- `cat static`
```
HH/lib64/ld-linux-x86-64.so.2GNUGNU��A+�kpl%h��B0m�'= 
                                                       Y h "libc.so.6puts__cxa_finalize__libc_start_mainGLIBC_2.2.5_ITM_deregisterTMCloneTable__gmon_start___ITM � � � � � � H�H��bleu�i	1�
 H��t��H���5�
 �%�
 @�%�
 h������%�
H�=�����^H��H���PTL��H�
 �DH�=�
 UH��
 H9�H��tH�Z
]��f.�]�@f.�H�=�
 H�5�
 UH)�H��H��H��H��?H�H��tH�!
 H��t
     ]��f�]�@f.��=I
 u/H�=�	 UH��t
����H����!    H�=�	 �
 ]����fDUH��]�f���UH��H�=�������]�f.�DAWAVI��AUATL�%F UH�-F SA��I��L)�H�H���W���H��t 1��L��L��D��A��H��H9�u�H�[]A\A]A^A_Ðf.���H�H��Oh hai! Wait what? A flag? Ye8#TT 1tt$D���o�Nere somewhere!8����������
�� � @ @ �0@)p  p�V``�^�y�                                                                                                                   ����+zRx

```

Veemos que este archivo contiene una serie de caracteres encodeados y no podemos leerlo. 
Ahora analizamos el siguiente archivo
- `cat ltdis.sh`
```
#!/bin/bash



echo "Attempting disassembly of $1 ..."


#This usage of "objdump" disassembles all (-D) of the first file given by 
#invoker, but only prints out the ".text" section (-j .text) (only section
#that matters in almost any compiled program...

objdump -Dj .text $1 > $1.ltdis.x86_64.txt


#Check that $1.ltdis.x86_64.txt is non-empty
#Continue if it is, otherwise print error and eject

if [ -s "$1.ltdis.x86_64.txt" ]
then
	echo "Disassembly successful! Available at: $1.ltdis.x86_64.txt"

	echo "Ripping strings from binary with file offsets..."
	strings -a -t x $1 > $1.ltdis.strings.txt
	echo "Any strings found in $1 have been written to $1.ltdis.strings.txt with file offset"



else
	echo "Disassembly failed!"
	echo "Usage: ltdis.sh <program-file>"
	echo "Bye!"
fi



```

Por como inicia este script, observamos que es un archivo que ejecuta instrucciones en linux. Una vez que analizamos el archivo y veamos que no sea malicioso le otorgarmos permisos de ejecucion para ejecutar este script
- `chmod +x ltdis.sh`
Ahora ejecutamos el archivo 
- `./ltdish.sh`
 ```
Attempting disassembly of  ...
objdump: 'a.out': No such file
objdump: section '.text' mentioned in a -j option, but not found in any input file
Disassembly failed!
Usage: ltdis.sh <program-file>
Bye!


 ```
 Observamos que es un programa para 'descifrar' archivos, el mismo script nos da la forma de usarlo, por lo que aplicamos esta forma de usarlo:
 - `./ltdish.sh static`
- Este comando nos devuelve el archivo 'descifrado', lo que queda es analizar el archivo generado 
	- `cat static.ltdis.strings.txt`
	- `picoCTF{d15a5m_t34s3r_f6c48608}`

## Referencias
