# Descripcion
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/dcdaf491b35c1d0f5075e9583edbbb7aaea1dffb6ad32bc000e4d87b5200ff7b/fixme3.tar.gz).

# Hints
- Read the comments...darn it!

# Solucion

Este reto es una continuacion del reto `Rust fixme 2` y al igual que el segundo tenemos que corregir el codigo para obtener la flag, asi que primero analizamos el codigo que descargamos:

```
use xor_cryptor::XORCryptor;

fn decrypt(encrypted_buffer: Vec<u8>, borrowed_string: &mut String) {
    // Key for decryption
    let key = String::from("CSUCKS");

    // Editing our borrowed value
    borrowed_string.push_str("PARTY FOUL! Here is your flag: ");

    // Create decryption object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return;
    }
    let xrc = res.unwrap();

    // Did you know you have to do "unsafe operations in Rust?
    // https://doc.rust-lang.org/book/ch19-01-unsafe-rust.html
    // Even though we have these memory safe languages, sometimes we need to do things outside of the rules
    // This is where unsafe rust comes in, something that is important to know about in order to keep things in perspective

    // unsafe {
        // Decrypt the flag operations 
        let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);

        // Creating a pointer 
        let decrypted_ptr = decrypted_buffer.as_ptr();
        let decrypted_len = decrypted_buffer.len();

        // Unsafe operation: calling an unsafe function that dereferences a raw pointer
        let decrypted_slice = std::slice::from_raw_parts(decrypted_ptr, decrypted_len);

        borrowed_string.push_str(&String::from_utf8_lossy(decrypted_slice));
    // }
    println!("{}", borrowed_string);
}

fn main() {
    // Encrypted flag values
    let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "12", "90", "7e", "53", "63", "e1", "01", "35", "7e", "59", "60", "f6", "03", "86", "7f", "56", "41", "29", "30", "6f", "08", "c3", "61", "f9", "35"];

    // Convert the hexadecimal strings to bytes and collect them into a vector
    let encrypted_buffer: Vec<u8> = hex_values.iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    let mut party_foul = String::from("Using memory unsafe languages is a: ");
    decrypt(encrypted_buffer, &mut party_foul);
}

```

Esta usando un puntero crudo (from_raw_parts) para crear un slice cuando no es necesario. Rust ya maneja la memoria de Vec8 . Aparte que no es necesario usar las funciones inseguras.

Codigo corregido:

```
use xor_cryptor::XORCryptor;

fn decrypt(encrypted_buffer: Vec<u8>, borrowed_string: &mut String) {
    // Clave de desencriptación
    let key = String::from("CSUCKS");

    // Modificar la cadena mutable recibida
    borrowed_string.push_str("PARTY FOUL! Here is your flag: ");

    // Crear el objeto de desencriptación
    let xrc = match XORCryptor::new(&key) {
        Ok(val) => val,
        Err(_) => return, // Manejo seguro de errores
    };

    // Desencriptar el buffer
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);

    // Usar el slice de manera segura, sin punteros crudos
    borrowed_string.push_str(&String::from_utf8_lossy(&decrypted_buffer));

    // Imprimir la cadena final
    println!("{}", borrowed_string);
}

fn main() {
    // Valores cifrados en hexadecimal
    let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "12", "90", "7e", "53", "63", "e1", "01", "35", 
                      "7e", "59", "60", "f6", "03", "86", "7f", "56", "41", "29", "30", "6f", "08", "c3", "61", "f9", "35"];

    // Convertir los valores hexadecimales a bytes
    let encrypted_buffer: Vec<u8> = hex_values.iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    // Definir el mensaje inicial mutable
    let mut party_foul = String::from("Using memory unsafe languages is a: ");

    // Llamar a la función de desencriptación
    decrypt(encrypted_buffer, &mut party_foul);
}
```

Ejecutamos `cargo run`

```
Using memory unsafe languages is a: PARTY FOUL! Here is your flag: picoCTF{n0w_y0uv3_f1x3d_1h3m_411}

```

## Referencias
