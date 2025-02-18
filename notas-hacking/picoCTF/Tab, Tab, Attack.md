## Descripcion
Using tabcomplete in the Terminal will add years to your life, esp. when dealing with long rambling directory structures and filenames: [Addadshashanammu.zip](https://mercury.picoctf.net/static/72712e82413e78cc8aa8d553ffea42b0/Addadshashanammu.zip)

## Hints
After `unzip`ing, this problem can be solved with 11 button-presses...(mostly Tab)..

## Solucion

Siguiendo la pista que nos da el archivo, descargamos el archivo y aplicamos el comando `unzip`
- `unzip Addadshashanammu `
Al descomprimirlo tenemos bastantes directorios con nombres bastantes largos, por lo que hacemos `cd [tab]` para autocompletar el nombre del directorio hasta encontrarnos con un archivo llamado `fang-of-haynekhtnamet`
Le aplicamos un cat para analizarlo profundamente:
 ```
  HH/lib64/ld-linux-x86-64.so.2GNUGNU� �"!�@����a	~���= 
                                                              Y h "libc.so.6puts__cxa_finalize__libc_start_mainGLIBC_2.2.5_ITM_deregisterTMCloneTable__gmon_star � � � � � � H�H��CloneTableu�i	1�
 H��t��H���5�
 �%�
 @�%�
 h������%�
H�=�����^H��H���PTL��H�
 �DH�=�
 UH��
 H9�H��tH�Z
]��f.�]�@f.�H�=i
 H�5b
 UH)�H��H��H��H��?H�H��tH�!
 H��t
     ]��f�]�@f.��=
 u/H�=�	 UH��t
����H�����    H� ]����fDUH��]�f���UH��H�=�������]�f.�DAWAVI��AUATL�%F UH�-F SA��8#TT 1tt$D���o�NH��t 1��L��L��D��A��H��H9�u�H�[]A\A]A^A_Ðf.���H�H��*ZAP!* picoCT�� ��0)@�p!_t4k3(;�                                                                                                                             ����+zRx
 ```
 Este archivo es ilegible, por lo que le damos los permisos de ejecucion con el comando:
 - `chmod +x fang-of-haynekhtnamet `
 Y ejecutamos el archivo con el comando:
 - `./fang-of-haynekhtnamet`
 ```
 *ZAP!* picoCTF{l3v3l_up!_t4k3_4_r35t!_6f332f10}

 ```