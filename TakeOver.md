# 🛡️ TryHackMe - TakeOver
![image](https://github.com/user-attachments/assets/51a95fca-f064-4942-96e9-ff79b52d53be)

## 📅 Fecha
Junio 2025

## 🧠 Descripción del reto
> Se proporciona el dominio `futurevera.thm`. El objetivo es encontrar subdominios ocultos mediante técnicas de enumeración DNS.

## 🔍 Categoría
- [x] Enumeración
- [ ] Web
- [ ] OSINT
- [ ] Forensics
- [ ] Otras

## 📁 Herramientas utilizadas
- `gobuster`
- Wordlist: `bitquark-subdomains-top100000.txt` (de SecLists)

## 🧩 Resolución paso a paso

### 1. Agregar el dociminio a /etc/hosts
Agregamos el dominio a /etc/hosts asignandole la ip que se nos indica
```bash
nano /etc/hosts
```
```bash
127.0.0.1       localhost
127.0.0.1       vnc.tryhackme.tech
127.0.1.1       tryhackme.lan   tryhackme
10.10.83.207    futurevera.thm

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters

Ahora debemos ser capaces de acceder al dominio 

```
### 2. Scaneo con Nmap
```bash
root@root:~# nmap futurevera.thm
Starting Nmap 7.80 ( https://nmap.org ) at 2025-06-23 18:01 BST
Nmap scan report for futurevera.thm (10.10.83.207)
Host is up (0.0051s latency).
Not shown: 997 closed ports
PORT    STATE SERVICE
22/tcp  open  ssh
80/tcp  open  http
443/tcp open  https
MAC Address: 02:7B:10:06:3F:FD (Unknown)

Nmap done: 1 IP address (1 host up) scanned in 0.43 seconds
```
### 3. Primer subdominio
En la descripcion del room se nos indica que estan reconstruyendo su `support`, por lo tanto es posible que cuenten con un subdominio `support`.
Agregamos el dominio a `\etc\hosts`
```bash
127.0.0.1       localhost
127.0.0.1       vnc.tryhackme.tech
127.0.1.1       tryhackme.lan   tryhackme
10.10.83.207    futurevera.thm support.futurevera.thm

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

### 4. Accedemos al subdominio usando el navegador
![image](https://github.com/user-attachments/assets/05e8e50b-4cc7-4c85-9521-d5009e123067)
### 5.
![image](https://github.com/user-attachments/assets/7aa6769a-f4f3-4baf-9e1f-2a9644c1d426)

```bash
  GNU nano 4.8                       /etc/hosts                       Modified  
127.0.0.1       localhost
127.0.0.1       vnc.tryhackme.tech
127.0.1.1       tryhackme.lan   tryhackme
10.10.177.233   secret**************.support.futurevera.thm futurevera.thm  sup>

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```
![image](https://github.com/user-attachments/assets/7904e12e-317c-4ba5-82ff-7109e03b4659)
https://flag{beea0d6edfcee06a59b83fb50ae81b2f}.s3-website-us-west-3.amazonaws.com/
🏁 Conclusión
