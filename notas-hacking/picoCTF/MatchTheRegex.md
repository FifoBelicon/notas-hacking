
## Descripcion
How about trying to match a regular expression

Additional details will be available after launching your challenge instance.

## Hints
Access the webpage and try to match the regular expression associated with the text field

# Solucion

Lo primero que tengo que hacer es analizar, la pagina. Como solo es un input decidi revisar el codigo fuente de la pagina para analizar el comportamiento de la web y me encontre con el script disponible.

Script:
```
|   |
|---|
|function send_request() {|
||let val = document.getElementById("name").value;|
||// ^p.....F!?|
||fetch(`/flag?input=${val}`)|
||.then(res => res.text())|
||.then(res => {|
||const res_json = JSON.parse(res);|
||alert(res_json.flag)|
||return false;|
||})|
||return false;|
||}|
```

En este caso viene un comentario con una expresion regular, segun la hint del reto, tenemos que hacer que la expresion regular haga un match para devolver la flag. En este caso la expresion regular se conforma de la siguiente manera:

- `^p`: Indica que la expresion debe de comenzar con la letra `p` 
- `.....`: indica 5 caracteres cualquiera
- `F!?`: Termina en F seguido de un ! opcional y un ?

Ahora que ya se como debe de armar la expresion uso burpsuite para probar como se maneja la peticion. Por lo que intercepto por medio del proxy y mando la peticion al repeater. 
La peticion se manda por medio del campo input y escribo `picoCTF` que casualmente concuerda con el regex.

Observo la salida:
![[images/respostMatchRegex.png]]


## Referencias
