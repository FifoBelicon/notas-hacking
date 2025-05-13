## Description

RED, RED, RED, REDDownload the image: [red.png](https://challenge-files.picoctf.net/c_verbal_sleep/831307718b34193b288dde31e557484876fb84978b5818e2627e453a54aa9ba6/red.png)

## Hint

1. The picture seems pure, but is it though?
2. Red?Ged?Bed?Aed?
3. Check whatever Facebook is called now.

## Solution

Se utiliza la herramienta `zsteg` para buscar archivos ocultos mediante estenografía en los bits menos significativos

Se utiliza zsteg, `--lsb` para kliminar los bits menos significativos, `--channel rgbs` nalaiza los canales rojo, verde, azul y alfa.

```
└─$ zsteg --lsb --channel rgba red.png
```

- Nos lanza esta siguiente cadena de texto:

```
cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==
```

```
picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}
```