# 🛡️ TryHackMe - Lo-Fi
![image](https://github.com/user-attachments/assets/977a884c-e3cc-4ead-b1c9-151542478cfd)


## 📅 Fecha
23 Junio 2025

## 🧠 Descripción del reto
> Se proporciona una pagina web. El objetivo es encontrar la flag oculta en el directorio root del servidor.

## 🔍 Categoría
- [ ] Enumeración
- [x] Web
- [ ] OSINT
- [ ] Forensics
- [ ] Otras

## 📁 Herramientas utilizadas
- Navegador Web

## 🧩 Resolución paso a paso
Omitiremos el escaneo con nmap porque ya sabemos que es una pagina web y en la descripcion del room se nos da pistas de hacer un LFI.
![image](https://github.com/user-attachments/assets/82587917-0062-49a8-a29f-22797db7a3a6)
Exporaremos la pagina brevemente y vemos que tenemos varios enlaces que nos permiten seleccionar otros generos
![image](https://github.com/user-attachments/assets/56de6bc4-4be6-4dae-b2b8-632e3c460dda)
Al seleccionar un genero al azar (en mi caso `relax`) vemos como en la URL `?page=relax.php`. Esto nos indica que el servidor indica el nombre de un archivo en la URL para cargar cada pagina. lo cual podemos usar para acceder a mas archivos del sistema
![image](https://github.com/user-attachments/assets/46600d5f-8a9c-4d94-a80e-b2302cbd16d6)
Debemos saber en que ubicacion del sistema, pero no tenemos la posibilidad de ejecutar comandos directamente en el sistema. Probamos un `pwd` pero no tenemos ningun resultado. 
![image](https://github.com/user-attachments/assets/e092fcf8-1b5d-46c4-882d-b90e91327d14)
Intentamos acceder `\etc\passwd`, un archivo que es objetivo de cualquier atacante para enumerar los usuarios del sistema.
![image](https://github.com/user-attachments/assets/4636e59f-7c04-4373-82e3-12dc8fe19056)

Recibimos un disclaimer del sistema lo cual nos inidica que vamos en un buena direccion.
---
Lo siguiente que haremos es intentar retroceder de directorio usando `../`
![image](https://github.com/user-attachments/assets/27453fba-f645-43f2-95e2-c4c30d739d8b)
Repetiremos la operacion hasta obtener un resultado exitoso.
Despues de 3 intentos y usando `../../../` pudimos acceder a `/etc/passwd`
![image](https://github.com/user-attachments/assets/f9da849b-9528-45d0-bd78-33c858497bdd)
Ya nos encontramos en el directorio root, lo ultimo que nos queda hacer es cambiar el nombre del archivo por `flag.txt` y la leemos.
![image](https://github.com/user-attachments/assets/81386a3c-d2c5-4dd5-bd37-f0bef9f36612)

---
🏁 Conclusión
