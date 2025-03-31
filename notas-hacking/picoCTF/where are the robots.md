
## Descripcion

Can you find the robots? `https://jupiter.challenges.picoctf.org/problem/36474/` ([link](https://jupiter.challenges.picoctf.org/problem/36474/)) or http://jupiter.challenges.picoctf.org:36474

---

# Hints
What part of the website could tell you where the creator doesn't want you to look?

# Solucion

1. Lo primero que debemos de hacer es analizar esta pagina
2. No hay mucho detras, pero en algunos casos existe el archivo `robots.txt` disponible y es accesible
3. Accedo al archivo `robots.txt` por medio de la ruta:
	1. `https://jupiter.challenges.picoctf.org/problem/36474/robots.txt`
Contenido de robots.txt:
```
User-agent: *
Disallow: /477ce.html
```

1. Ahora me doy cuenta que existe un archivo llamado `477ce.html` 
2. Ahora voy a mirarlo:
	1. `https://jupiter.challenges.picoctf.org/problem/36474/477ce.html`
3. Aqui mismo obtenemos la flag.
```
picoCTF{ca1cu1at1ng_Mach1n3s_477ce}
```

# Referencias

