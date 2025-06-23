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

### 1. Enumeración con Gobuster

```bash
gobuster dns -d futurevera.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/bitquark-subdomains-top100000.txt

🏁 Conclusión
