
## Description

The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?Download the suspicious file [here](https://artifacts.picoctf.net/c_titan/96/flag2of2-final.pdf).

## Hints

- This problem can be solved by just opening the file in different ways

## Solution
Abrimos el pdf, con el comando `open`

```
└─$ open flag2of2-final.pdf 

```

Al momento de ver el pdf, nos dan la mitad de la flag

```
1n_pn9_&_pdf_90974127}
```

Con el comando `convert` permite manipular imágenes desde diferente formatos, en este caso se convierte un archivo PD en una imágen PNG.  

```
└─$ convert flag2of2-final.pdf flag2of2-final.png 
convert: profile 'icc': 'RGB ': RGB color space not permitted on grayscale PNG `flag2of2-final.png' @ warning/png.c/MagickPNGWarningHandler/1525.

```

```

└─$ ls
flag2of2-final.pdf  flag2of2-final.png

```


```
└─$ open flag2of2-final.png 

```

La segunda parte de la flag:
```
picoCTF{f1u3n7_1n_pn9_&_pdf_724b1287}
```

```
```