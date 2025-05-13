
## Description

I've gotten bored of handing out flags as text. Wouldn't it be cool if they were an image instead?You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/16/challenge.zip)

Additional details will be available after launching your challenge instance.

## Hints

1. QR codes are a way of encoding data. While they're most known for storing URLs, they can store other things too.
2. Mobile phones have included native QR code scanners in their cameras since version 8 (Oreo) and iOS 11
3. If you don't have access to a phone, you can also use zbar-tools to convert an image to text

## Solution

Nos conectamos al server con `ssh`

```         
└─$ ssh -p 59757 ctf-player@atlas.picoctf.net
```

Aplicamos un ls, ahi se encuentra flag.png, que es un código de barras. 

El comando `zbarimg` sirve para leer y decodificar códigos de barras y códigos QR contenidos en una imagen. 

```
ctf-player@challenge:~/drop-in$ zbarimg flag.png 
Connection Error (Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory)
Connection Null
QR-Code:picoCTF{p33k_@_b00_7843f77c}
scanned 1 barcode symbols from 1 images in 0 seconds
```

picoCTF{p33k_@_b00_7843f77c}