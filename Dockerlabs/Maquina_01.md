# Máquina: [Nombre de la máquina de DockerLabs]

# Fecha
[Fecha en que la resolviste]

## Reconocimiento
- Comando usado: `nmap -sV 172.17.0.2`
- Hallazgos: Encontré el puerto 80 abierto con un Apache.

## Explotación
- Accedí a la web y encontré un directorio `/admin`.
- Probé inyección SQL en el login.
- **Comando clave**: `sqlmap -u "http://172.17.0.2/admin" --forms`

## ¿Dónde me atascué?
- No entendía por qué el script de Python no ejecutaba la reverse shell. El problema era un error de sintaxis en la IP.

## Solución
- Corregí la IP y obtuve la shell con `nc -lvnp 4444`.

## Comandos usados (Resumen)
```bash
nmap -sV 172.17.0.2
gobuster dir -u http://172.17.0.2 -w /usr/share/wordlists/dirb/common.txt
nc -lvnp 4444
