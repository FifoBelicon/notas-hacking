## Descripcion

A developer has added profile picture upload functionality to a website. However, the implementation is flawed, and it presents an opportunity for you. Your mission, should you choose to accept it, is to navigate to the provided web page and locate the file upload area. Your ultimate goal is to find the hidden flag located in the `/root` directory.You can access the web application [here](http://standard-pizzas.picoctf.net:65295/)!


# Hints
- File upload was not sanitized
- Whenever you get a shell on a remote machine, check `sudo -l`

## Solucion
Analizamos esta pagina y solo tenemos un campo para poder subir archivos y dirigirnos a la seccion de dirigirnos a donde se puede subir.
Lo que permite subir es una imagen, por lo que hare un LFI para buscar un RCE inyectando una webshell de php en mi imagen y asi obtener una reverse shell.





