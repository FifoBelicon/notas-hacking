Our flag printing service has started glitching!

Additional details will be available after launching your challenge instance.

## Solucion
Para solucionar este reto es necesario iniciar una instancia. 
![[Pasted image 20250212234627.png]]
Una vez que se inicia esta instancia es posible conectarnos a la direccion.  
Usamos el siguiente comando para conectarnos por medio de netcat (nc)
- `nc saturn.picoctf.net 64533`
Ahora que nos conectamos, tendremos que analizar la salida que da.
![[Pasted image 20250212235453.png]]
Si observamos vemos que intenta concatenar caracteres (chr) que tienen un codigo en hexadecimal. Estos valores en hexadecimal corresponden al codigo ASCII por lo que estos corresponden a caracteres. Nuestra tarea es completar la bandera por medio de los caracteres que esta tratando de mostrar.
Hacemos uso de una tabla ASCII con una equivalencia a valor Hex como esta:
![[Pasted image 20250212235905.png]]
Con esto podemos saber a que letra corresponde cada valor hexadecimal
- chr(0x62) = b
- chr(0x64) = d
- chr(0x61) = a
- chr(0x36) = 6 
- chr(0x38) = 8 
- chr(0x66) = f
- chr(0x37) = 7
- chr(0x35) = 5
Ahora completamos la bandera:
```
picoCTF{gl17ch_m3_n07_bda68f75}
```
## Referencias
- https://ss64.com/ascii.html
