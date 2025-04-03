
## Descripcion

We found this [packet capture](https://jupiter.challenges.picoctf.org/static/483e50268fe7e015c49caf51a69063d0/capture.pcap). Recover the flag.

## Hints
- What are streams?
- Try using a tool like Wireshark

# Solucion

Lo primero que hago es abrir WireShark para analizar el trafico de paquetes. Segun la hint busco en los streams una flag. Comienzo a buscar uno por uno en los streams, hasta que el stream numero 6, encuentro la flag:


![[images/flagWireshark.png]]

## Referencias

 