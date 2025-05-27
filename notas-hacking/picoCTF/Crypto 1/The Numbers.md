
# Descripcion
The [numbers](https://jupiter.challenges.picoctf.org/static/f209a32253affb6f547a585649ba4fda/the_numbers.png)... what do they mean?

# Hints
- The flag is in the format PICOCTF{}

# Solucion

Nos da una imagen. Si verificamos el contenido, veremos una serie de numeros, pero con dos llaves que abren y cierran, asi como el formato de la bandera, pienso que eso puede ser la bandera pero encodeada, no hay numeros mayores a 21, por lo que cada numero se puede tratar de una letra del abecedario. 

Convertimos cada número a su letra correspondiente:

- 16 = P
    
- 9 = I
    
- 3 = C
    
- 15 = O
    
- 3 = C
    
- 20 = T
    
- 6 = F
    
- {
    
- 20 = T
    
- 8 = H
    
- 5 = E
    
- 14 = N
    
- 21 = U
    
- 13 = M
    
- 2 = B
    
- 5 = E
    
- 18 = R
    
- 19 = S
    
- 13 = M
    
- 1 = A
    
- 19 = S
    
- 15 = O
    
- 14 = N
    
- }
    

Entonces, el mensaje es:

`PICOCFT{THENUMBERSMASON}`