In RSA, a small `e` value can be problematic, but what about `N`? Can you decrypt this? [values](https://mercury.picoctf.net/static/38f30029ab93478310e906d3d084a4c1/values)

# Hints
- Bits are expensive, I used only a little bit over 100 to save money

# Solucion
En este caso, lo que tenemos que hacer es obtener los elementos que conforman N, lo cual es p y q, esto se puede hacer en un ataque de fuerza bruta, ya que  N es pequeño. Descargamos los valores y armamos el siguiente script:


```
─(cyberchef㉿kali)-[~/Downloads/mind]
└─$ cat values       
Decrypt my super sick RSA:
c: 240986837130071017759137533082982207147971245672412893755780400885108149004760496
n: 831416828080417866340504968188990032810316193533653516022175784399720141076262857
e: 65537                                                                                                                      
┌──(cyberchef㉿kali)-[~/Downloads/mind]
└─$ python            
Python 3.13.2 (main, Feb  5 2025, 01:23:35) [GCC 14.2.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> c = 240986837130071017759137533082982207147971245672412893755780400885108149004760496
>>> n = 831416828080417866340504968188990032810316193533653516022175784399720141076262857
>>> e = 65537
>>> p = 1593021310640923782355996681284584012117
>>> q = 521911930824021492581321351826927897005221
>>> p * q == n
True
>>> tn = (p - 1) * (q - 1)
>>> d = pow(e,-1,tn)
>>> m = pow(c,d,n)
>>> m
13016382529449106065927291425342535437996222135352905256639592405461024281868413
>>> bytes.fromhex(hex(m)[2:])
b'picoCTF{sma11_N_n0_g0od_23540368}'


```

# Referencias

