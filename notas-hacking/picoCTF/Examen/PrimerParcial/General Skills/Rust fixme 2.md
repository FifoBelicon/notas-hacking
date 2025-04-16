
## Descripcion
The Rust saga continues? I ask you, can I borrow that, pleeeeeaaaasseeeee?Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz).

# Hints
- https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html

# Solucion

Este reto es una continuacion del reto `Rust fixme 1` y al igual que el primero tenemos que corregir el codigo para obtener la flag, asi que primero analizamos el codigo que descargamos:

```
use xor_cryptor::XORCryptor;

fn decrypt(encrypted_buffer:Vec<u8>, borrowed_string: &String){ // How do we pass values to a function that we want t>

    // Key for decryption
    let key = String::from("CSUCKS");

    // Editing our borrowed value
    borrowed_string.push_str("PARTY FOUL! Here is your flag: ");

    // Create decrpytion object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return; // How do we return in rust?
    }
    let xrc = res.unwrap();

    // Decrypt flag and print it out
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    borrowed_string.push_str(&String::from_utf8_lossy(&decrypted_buffer));
    println!("{}", borrowed_string);
}


fn main() {
    // Encrypted flag values
    let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61", "25",>

    // Convert the hexadecimal strings to bytes and collect them into a vector
    let encrypted_buffer: Vec<u8> = hex_values.iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    let party_foul = String::from("Using memory unsafe languages is a: "); // Is this variable changeable?
    decrypt(encrypted_buffer, &party_foul); // Is this the correct way to pass a value to a function so that it can b>
}

```

Igual aqui hay erroes que los comentarios en el codigo nos da pistas:
- el parametro `borrowed_string` es una referencia inmutable (`$String`) , entonces no se puede modificar dentro de la funcion
	- Se debe usar `mut String`
- La variable `party_foul` no esta declarada como mut, no se puede modifcar

Codigo corregido: 

```
use xor_cryptor::XORCryptor;

fn decrypt(encrypted_buffer: Vec<u8>, borrowed_string: &mut String) {
    // Key for decryption
    let key = String::from("CSUCKS");

    // Modificar el string pasado como referencia mutable
    borrowed_string.push_str("PARTY FOUL! Here is your flag: ");

    // Crear el objeto de desencriptado
    let xrc = match XORCryptor::new(&key) {
        Ok(val) => val,
        Err(_) => return, // Manejo seguro de errores
    };

    // Desencriptar el buffer y agregarlo al string mutable
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    borrowed_string.push_str(&String::from_utf8_lossy(&decrypted_buffer));

    // Imprimir el resultado
    println!("{}", borrowed_string);
}

fn main() {
    // Valores encriptados en hexadecimal
    let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61", "25",
                       "7f", "5a", "60", "50", "11", "38", "1f", "3a", "60", "e9", "62", "20", "0c", "e6", "50", "d3", "35"];

    // Convertir los valores hexadecimales a bytes
    let encrypted_buffer: Vec<u8> = hex_values.iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    // Declarar `party_foul` como mutable
    let mut party_foul = String::from("Using memory unsafe languages is a: ");
    
    // Pasar la referencia mutable a la función
    decrypt(encrypted_buffer, &mut party_foul);
}
```

Ahora corremos el codigo con `cargo run`:

```
Using memory unsafe languages is a: PARTY FOUL! Here is your flag: picoCTF{4r3_y0u_h4v1n5_fun_y31?}

```

# Referencias
- https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html
