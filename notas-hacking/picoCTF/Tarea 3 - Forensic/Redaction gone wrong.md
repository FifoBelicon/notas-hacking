## Description

Now you DON’T see me.This [report](https://artifacts.picoctf.net/c/84/Financial_Report_for_ABC_Labs.pdf) has some critical data in it, some of which have been redacted correctly, while some were not. Can you find an important key that was not redacted properly?

## Hint

- How can you be sure of the redaction?
## Solution


Primero descargamos el archivo .pdf, después lo abrimos y observamos que algunbas partes son ocultas. Para poder verlas una opción es control c a todo el contenido del documento, y podria aparecer la flag

```
Financial Report for ABC Labs, Kigali, Rwanda for the year 2021.
Breakdown - Just painted over in MS word.
Cost Benefit Analysis
Credit Debit
This is not the flag, keep looking
Expenses from the
picoCTF{C4n_Y0u_S33_m3_fully}
Redacted document.
```

```
 picoCTF{C4n_Y0u_S33_m3_fully}
 ```
 