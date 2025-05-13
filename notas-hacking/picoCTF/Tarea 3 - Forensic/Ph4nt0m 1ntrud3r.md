## Description

A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag.To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder!Find the PCAP file here [Network Traffic PCAP file](https://challenge-files.picoctf.net/c_verbal_sleep/a681faccaaa199ce75c3abeef9525f813b6451644a8d8d27cc097e4b1ccb741a/myNetworkTraffic.pcap) and try to get the flag.

## Hint

-  Filter your packets to narrow down your search.
-  Attacks were done in timely manner.
-  Time is essential

## Solution

Abrimos el archivo `.pcap` en wireshark.

Se verifica por el tiempo Buscamos todos los paquetes de tcp que tengan el tamaño 12

```
Asi bucamos en wireshark -> tcp.len==12 
```

Tomamos todos el texto ASCII de los paquetes TSP, formamos la siguiente cadena. Se tomo otro que sea de tamaño 4, por que faltaba una parte.

```
cGljb0NURg==ezF0X3c0cw==bnRfdGg0dA==XzM0c3lfdA==YmhfNHJfZA==MTA2NTM4NA==
```

Al utilizar cyber chef

```
 picoCTF{1t_w4snt_th4t_34sy_tbh_4r_d1065384}
 ```
 