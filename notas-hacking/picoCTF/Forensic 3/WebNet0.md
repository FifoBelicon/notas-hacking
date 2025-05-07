# Descripcion
We found this [packet capture](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/capture.pcap) and [key](https://jupiter.challenges.picoctf.org/static/0c84d3636dd088d9fe4efd5d0d869a06/picopico.key). Recover the flag.

# Hints
- Try using a tool like Wireshark.
- How can you decrypt the TLS stream?

# Solucion

Lo primero que tenemos que descargar son los dos archivos, uno es una captura de trafico y de red y otro es una llave RSA. 

Abrimos wireshark y abrimos el archivo del trafico. En este caso, muchos de los paquetes TLS van encriptados por el protocolo `https`. Pero gracias a que tenemos la llave podemos ver el contenido de estos paquetes.

Cargamos la llave RSA en el wireshark y ahora vemos como estos paquetes TLS. Usamos el buscador por strings la palabra `pico` para verificar si la flag se encuentra ahi y en efecto, la flag se encuentra en formato string.

## Referencias

