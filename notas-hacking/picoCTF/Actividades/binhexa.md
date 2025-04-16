## Descripcion

How well can you perfom basic binary operations?

Additional details will be available after launching your challenge instance.

## Hints
None

# Solucion

Este reto pone a prueba las operaciones que hacemos con los numeros binarios y todas aquellas que se pueden realizar con estos numeros, operaciones como la multiplicacion, AND, OR, corrimiento de bits a la izquierda (<<) y a la derecha (>>).

El reto nos proporciona conectarnos al servidor y comenzar las preguntas, en la cual nos da un numero 1 y un numero 2 estos dos en binario, los cuales tenemos que responder para encontrar la flag, para estos, realice un script en python para responder todas las preguntas y obtener la flag:

Para estas operaciones realice el siguiente script de python:

```
bin1 = "10111110"
bin2 = "00111111"

num1 = int(bin1, 2)
num2 = int(bin2, 2)

and_resultado = num1 & num2
print(f"AND: {bin(and_resultado)[2:].zfill(8)")

or_resultado = num1 | num2
print(f"OR= {bin(or_resultado)[2:].zfill(8)}")


dezplazamiento_izq = num1 << 1
print(f"(<<1): {bin(dezplazamiento_izq)[2:]}")

dezplazamienti_der = num2 >> 1
print(f"(>>1): {bin(dezplazamiento_der)[2:].zfill(8)}")

```

```
Welcome to the Binary Challenge!"
Your task is to perform the unique operations in the given order and find the final result in hexadecimal that yields the flag.

Binary Number 1: 10111110
Binary Number 2: 00111111


Question 1/6:
Operation 1: '*'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10111011000010
Correct!

Question 2/6:
Operation 2: '&'
Perform the operation on Binary Number 1&2.
Enter the binary result: 00111110
Correct!

Question 3/6:
Operation 3: '|'
Perform the operation on Binary Number 1&2.
Enter the binary result: 10111111
Correct!

Question 4/6:
Operation 4: '+'
Perform the operation on Binary Number 1&2.
Enter the binary result: 11111101
Correct!

Question 5/6:
Operation 5: '<<'
Perform a left shift of Binary Number 1 by 1 bits.
Enter the binary result: 101111100
Correct!

Question 6/6:
Operation 6: '>>'
Perform a right shift of Binary Number 2 by 1 bits .
Enter the binary result: 00011111
Correct!

```

Por ultimo solo uso un transformador de binario a hexadecimal e ingreso el valor que se me pide:

```
Enter the results of the last operation in hexadecimal: 1F

Correct answer!
The flag is: picoCTF{b1tw^3se_0p3eR@tI0n_su33essFuL_1367e2c6}

```

## Referencias

- https://es.planetcalc.com/911/
- https://es.convertbinary.com/binario-a-hexadecimal/