# Descripcion
We made a lot of substitutions to encrypt this. Can you decrypt it? Connect with `nc jupiter.challenges.picoctf.org 43522`.

# Hints
- Flag is not in the usual flag format

# Solucion

Una vez que nos conectamos vemos la siguiente salida:
```
┌──(cyberchef㉿kali)-[~/Downloads/caesar]
└─$ nc jupiter.challenges.picoctf.org 43522         
-------------------------------------------------------------------------------
skpfhjdo rchc no zkmh uejf - uhcbmcpsz_no_s_kqch_ejxvwj_kfuxjmphju
-------------------------------------------------------------------------------
jecacz uzkwkhkqndsr yjhjxjikq gjo drc drnhw okp ku uzkwkh ljqekqndsr yjhjxjikq, j ejpw kgpch gcee ypkgp np kmh wnodhnsd np rno kgp wjz, jpw odnee hcxcxvchcw jxkpf mo kgnpf dk rno fekkxz jpw dhjfns wcjdr, grnsr rjllcpcw drnhdccp zcjho jfk, jpw grnsr n orjee wcoshnvc np ndo lhklch lejsc. ukh drc lhcocpd n gnee kpez ojz drjd drno ejpwkgpchukh ok gc mocw dk sjee rnx, jedrkmfr rc rjhwez olcpd j wjz ku rno enuc kp rno kgp codjdcgjo j odhjpfc dzlc, zcd kpc lhcddz uhcbmcpdez dk vc xcd gndr, j dzlc jvtcsd jpw qnsnkmo jpw jd drc ojxc dnxc ocpocecoo. vmd rc gjo kpc ku drkoc ocpocecoo lchokpo grk jhc qchz gcee sjljvec ku ekkynpf judch drcnh gkhewez juujnho, jpw, jlljhcpdez, judch pkdrnpf ceoc. uzkwkh ljqekqndsr, ukh npodjpsc, vcfjp gndr pcad dk pkdrnpf; rno codjdc gjo ku drc oxjeecod; rc hjp dk wnpc jd kdrch xcp'o djveco, jpw ujodcpcw kp drcx jo j dkjwz, zcd jd rno wcjdr nd jllcjhcw drjd rc rjw j rmpwhcw drkmojpw hkmveco np rjhw sjor. jd drc ojxc dnxc, rc gjo jee rno enuc kpc ku drc xkod ocpocecoo, ujpdjodnsje uceekgo np drc grkec wnodhnsd. n hclcjd, nd gjo pkd odmlnwndzdrc xjtkhndz ku drcoc ujpdjodnsje uceekgo jhc orhcgw jpw npdceenfcpd cpkmfrvmd tmod ocpocecoopcoo, jpw j lcsmenjh pjdnkpje ukhx ku nd.


```

La pista dice que se hacen sustituciones. Existen bastantes tipos de cifrados por sustucion, use una herramienta online para obtener el mensaje automaticamente:

- https://www.guballa.de/substitution-solver
 Ingreso el texto cifrado y selecciono romper el cifrado y obtengo la siguiente salida:

```
-------------------------------------------------------------------------------
congrats here is your flag - frequency_is_c_over_lambda_ogfmaunraf
-------------------------------------------------------------------------------
alexey fyodorovitch karamajov was the third son of fyodor pavlovitch karamajov, a land owner well known in our district in his own day, and still remembered among us owing to his gloomy and tragic death, which happened thirteen years ago, and which i shall describe in its proper place. for the present i will only say that this landownerfor so we used to call him, although he hardly spent a day of his life on his own estatewas a strange ty

```

Esta es la flag:
`frequency_is_c_over_lambda_ogfmaunraf`

