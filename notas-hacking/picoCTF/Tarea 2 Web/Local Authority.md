
# Descripcion
Can you get the flag?Go to this [website](http://saturn.picoctf.net:64677/) and see what you can discover.

# Hints
- How is the password checked on this website?

# Solucion

Lo primero que hacemos es analizar el comportamiento de la web. En este caso nos encontramos un panel de login. 
Comienzo intentando `admin:admin` 

Obtengo una pantalla de log in fallido, pero si inspecciono el codigo fuente obtengo lo siguiente:

```
  

|   |   |
|---|---|
||<!DOCTYPE html>|
||<html lang="en">|
||<head>|
||<meta charset="UTF-8">|
||<meta name="viewport" content="width=device-width, initial-scale=1.0">|
||<meta http-equiv="X-UA-Compatible" content="ie=edge">|
||<link rel="stylesheet" href="[style.css](http://saturn.picoctf.net:55294/style.css)">|
||<title>Login Page</title>|
||</head>|
||<body>|
||<script src="[secure.js](http://saturn.picoctf.net:55294/secure.js)"></script>|
|||
||<p id='msg'></p>|
|||
||<form hidden action="admin.php" method="post" id="hiddenAdminForm">|
||<input type="text" name="hash" required id="adminFormHash">|
||</form>|
|||
||<script type="text/javascript">|
||function filter(string) {|
||filterPassed = true;|
||for (let i =0; i < string.length; i++){|
||cc = string.charCodeAt(i);|
|||
||if ( (cc >= 48 && cc <= 57) \||
||(cc >= 65 && cc <= 90) \||
||(cc >= 97 && cc <= 122) )|
||{|
||filterPassed = true;|
||}|
||else|
||{|
||return false;|
||}|
||}|
|||
||return true;|
||}|
|||
||window.username = "admin";|
||window.password = "admin";|
|||
||usernameFilterPassed = filter(window.username);|
||passwordFilterPassed = filter(window.password);|
|||
||if ( usernameFilterPassed && passwordFilterPassed ) {|
|||
||loggedIn = checkPassword(window.username, window.password);|
|||
||if(loggedIn)|
||{|
||document.getElementById('msg').innerHTML = "Log In Successful";|
||document.getElementById('adminFormHash').value = "2196812e91c29df34f5e217cfd639881";|
||document.getElementById('hiddenAdminForm').submit();|
||}|
||else|
||{|
||document.getElementById('msg').innerHTML = "Log In Failed";|
||}|
||}|
||else {|
||document.getElementById('msg').innerHTML = "Illegal character in username or password."|
||}|
||</script>|
|||
||</body>|
||</html>|
||

```

Hay un script que se llama `secure.js`, esto es sospechoso, asi hago click para ver su contenido: 

- secure.js
```
  
function checkPassword(username, password)
{
  if( username === 'admin' && password === 'strongPassword098765' )
  {
    return true;
  }
  else
  {
    return false;
  }
}

```

Aqui hace una verificacion del login, el usuario debe de ser igual y la contraseña esta en texto en claro, asi que copio esta contraseña y uso las siguientes credenciales:

`admin:strongPassword098765`

Accedemos:

```
picoCTF{j5_15_7r4n5p4r3n7_b0c2c9cb}
```

## Referencia
