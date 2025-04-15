
## Descripcion

If you want to hash with the best, beat this test!`nc saturn.picoctf.net 54164`

### Hints
- You can use a commandline tool or web app to hash text
- Press Ctrl and c on your keyboard to close your connection and return to the command prompt.

# Solucion
En este reto se nos presenta una terminal interactiva en la cual nos pide ingresar el hash md5 de una palabra que es proporcionada por el servidor. 
Para obtener este hash hago uso de una herramienta online como `md5 hash generator`

```
Please md5 hash the text between quotes, excluding the quotes: 'bull fight'
Answer: 
87cc16b261803de4f24debfd23119443
87cc16b261803de4f24debfd23119443
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'angry hornets'
Answer: 
ce49f0297d478454cb6e27c4410caa0f
ce49f0297d478454cb6e27c4410caa0f
Incorrect. Try again?
Answer: 
456fdc871d3f9976046da83bcfdd52ff
456fdc871d3f9976046da83bcfdd52ff
Correct.
Please md5 hash the text between quotes, excluding the quotes: 'local police'
Answer: 
b36e4003adb9138e0c7f0379b9be4d5b
b36e4003adb9138e0c7f0379b9be4d5b
Correct.
picoCTF{4ppl1c4710n_r3c31v3d_bf2ceb02}
                                          

```

# Referencias
- https://www.md5hashgenerator.com/
