# Log Book 11

## Task 1

### What part of the certificate indicates this is a CA’s certificate?
![](imgs/week11/task1-1.png)

### What part of the certificate indicates this is a self-signed certificate?
The Issuer is the same as the Subject.

![](imgs/week11/task1-2.png)

### In the RSA algorithm, we have a public exponent e, a private exponent d, a modulus n, and two secret numbers p and q, such that n = pq. Please identify the values for these elements in your certificate and key files.

- Public exponent, e:

![](imgs/week11/task1-3.png)

- Private exponent, d:

![](imgs/week11/task1-5.png)

- Modulus, n:
  
![](imgs/week11/task1-4.png)

- To find the private key, we need to find the two secret numbers p and q, such that n=p*q:
  - p:
    ![](imgs/week11/task1-6.png)
  - q:
    ![](imgs/week11/task1-7.png) 

## Task 2
We generated the certificate signing request (CSR).

![](imgs/week11/task2.png)

## Task 3
We generated the certificate.

![](imgs/week11/task3-1.png)

Print of the decoded content of the
certificate:

![](imgs/week11/task3-2.png)

## Task 4
![](imgs/week11/task4-1.png)
![](imgs/week11/task4-2.png)

## Task 5
ServerName was changed to ```fe.up.pt```. ```10.9.0.80 fe.up.pt``` was added to ```/etc/hosts```.
![](imgs/week11/task5.png)

## Task 6
When the CA is compromised, we can sign certificates ourselves and impersonate other websites. In this case, we're impersonating ```fe.up.pt```.

![](imgs/week11/task6-1.png)

![](imgs/week11/task6-2.png)

---

## CTF 11
### Challenge 1

No primeiro desafio o objetivo é decifrar uma mensagem RSA sendo nos dado indiretamente o valor de p e q e o e é padrão.

Primeiramente, descobrimos p e q. A estratégia utilizada foi o teste de primalidade de Miller-Rabin que diz se um número tem uma boa probabilidade de ser primo, uma vez que com número com tantos digitos verificar com 100% de certeza levaria algum tempo.

<img src="imgs/week11/ctf1img1.png">

Com estes dois números, consegui-mos facilmente calcular o (p-1)(q-1) e por consequente o d.
´
O resultado foi o seguinte: 

<img src="imgs/week11/ctf1img2.png">
