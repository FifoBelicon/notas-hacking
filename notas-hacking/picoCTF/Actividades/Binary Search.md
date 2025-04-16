
## Descripcion
Want to play a game? As you use more of the shell, you might be interested in how they work! Binary search is a classic algorithm used to quickly find an item in a sorted list. Can you find the flag? You'll have 1000 possibilities and only 10 guesses.Cyber security often has a huge amount of data to look through - from logs, vulnerability reports, and forensics. Practicing the fundamentals manually might help you in the future when you have to write your own tools!You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_atlas/6/challenge.zip)

Additional details will be available after launching your challenge instance.

### Hints
- Have you ever played hot or cold? Binary search is a bit like that.
- You have a very limited number of guesses. Try larger jumps between numbers!
- The program will randomly choose a new number each time you connect. You can always try again, but you should start your binary search over from the beginning - try around 500. Can you think of why?

# Solucion
 En  este reto simulamos una busqueda binaria, en la cual es un algoritmo de busqueda, en la cual funciona en dividir un rango de numeros por la mitad para asi encontrar subrangos y encontrar su posicion. En este caso, el reto trata de adivinar un numero entre el 0 y el 1000 en 10 intentos. 
 1. Aplicaremos el algoritmo de busqueda binaria basado en la formula matematica: 
	 1. $$ \frac{min + max}{2} = x $$
 2. Aplicando esta formula, lo primero que hice fue descartar la mitad de los numeros, en este caso aplique el numero 500 y depende de la respuesta del servidor, en este caso si sale `higher` se que el numero que busco es mayor que 501, y si sale `lower` se que el numero es menor al 500.
	 1. Observo la salida:
	 2. Enter your guess: 500
			Higher! Try again.
1. Ahora se que mi numero es mayor al 500, y mi rango de numeros es ahora entre el 501 al 1000.
2. Para saber ahora cual es la otra mitad en este rango aplicamos nuevamente la formula con los valores obtenidos:
	1. $$ \frac{501 + 1000}{2} = 751 $$
- Escribo el numero 751 para intentar. 
```
Enter your guess: 751
Lower! Try again.

```
- Ahora se que mi numero es menor que 751.
	- Ahora mi rango se hace mas pequeño, por que mi numero es mayor que 500 y menor que 751.
- Para resolver este reto consiste en aplicar esta formula hasta dar con el numero exacto. En mi caso use los 10 intentos para descifrar mi numero correcto, usando esta formula matematica:

```
Welcome to the Binary Search Game!
I'm thinking of a number between 1 and 1000.
Enter your guess: 500
Higher! Try again.
Enter your guess: 751
Lower! Try again.
Enter your guess: 625
Higher! Try again.
Enter your guess: 688
Lower! Try again.
Enter your guess: 657
Higher! Try again.
Enter your guess: 673
Higher! Try again.
Enter your guess: 681
Lower! Try again.
Enter your guess: 677
Higher! Try again.
Enter your guess: 679
Lower! Try again.
Enter your guess: 678
Congratulations! You guessed the correct number: 678
Here's your flag: picoCTF{g00d_gu355_de9570b0}
Connection to atlas.picoctf.net closed.

```

### Referencias
- https://es.khanacademy.org/computing/computer-science/algorithms/binary-search/a/binary-search
