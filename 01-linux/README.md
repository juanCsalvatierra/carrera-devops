# 01 · Linux & Sistemas

**Objetivo:** administrar servidores Linux y automatizar la operación básica.
**Herramientas:** Ubuntu/Debian, Bash, systemd, SSH, journalctl, cron, rsync, ufw.

Guía general de la etapa: [docs/etapa-1.md](../docs/etapa-1.md)

## Bloque 1 · Fundamentos
- [ ] Recorrer el filesystem (`/etc`, `/var`, `/usr`, `/home`, `/proc`) y explicar qué hay en cada uno
- [ ] Instalar, actualizar y remover paquetes con `apt`; inspeccionar con `dpkg`
- [ ] Crear usuarios y grupos; asignar permisos con `chmod`/`chown`; entender `umask`
- [ ] Configurar `sudo` para un usuario sin root
- [ ] Editar archivos con `vim` o `nano` sin mouse

## Bloque 2 · Construcción
- [ ] Inspeccionar procesos (`ps`, `top`) y enviar señales (SIGTERM vs SIGKILL)
- [ ] Escribir una unit de systemd para un script propio: `start`, `enable`, `status`
- [ ] Leer logs con `journalctl` filtrando por servicio, prioridad y fecha
- [ ] Programar una tarea con `cron` y compararla con un systemd timer
- [ ] SSH: generar llaves, deshabilitar login por contraseña, usar `~/.ssh/config`
- [ ] Almacenamiento: `df`, `du`, `lsblk`, montar un loop device, `/etc/fstab`
- [ ] **Checkpoint 1**

## Bloque 3 · Bash
- [ ] Variables, argumentos, condicionales y loops
- [ ] Pipes, redirecciones, funciones y arrays
- [ ] Exit codes y `set -euo pipefail`
- [ ] Script de backup con `rsync`
- [ ] Script de health-check de un servicio
- [ ] Rotación de logs (`logrotate` o script propio)
- [ ] **Checkpoint 2** + diagrama del servidor + ADR corto

## Bloque 4 · Entrega
- [ ] Hardening: `ufw`, SSH sin root ni contraseña, actualizaciones automáticas
- [ ] Probar un restore real de tus backups
- [ ] Diagnosticar un servicio caído con logs, puertos (`ss`) y procesos
- [ ] Escribir el runbook

## Proyecto final: servidor Linux reproducible

| Entregable | Criterio |
|---|---|
| Usuarios y permisos | Documentados, sin uso de root directo |
| SSH seguro | Solo llaves, sin login de root |
| Firewall | `ufw` con solo los puertos necesarios |
| 3 scripts operativos | Backup, health-check y rotación de logs, con manejo de errores |
| Runbook | Cómo operar, diagnosticar y restaurar |
| ADR | Por qué elegiste ese hardening |

**Logrado cuando:** funciona, otra persona lo reproduce con el README y podés explicar tus decisiones.

## Estructura de carpetas

```
01-linux/
├── notas/            # comandos, conceptos, fallas
├── labs/             # 01-permisos/, 02-systemd/, ...
└── proyecto-final/   # scripts, runbook, diagrama, ADR
```

## Recursos
- Manuales: `man`, `man systemd.service`, documentación de Ubuntu Server
- *The Linux Command Line* (William Shotts, gratis online)
- OverTheWire: Bandit, para practicar la terminal
