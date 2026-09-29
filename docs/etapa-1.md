# Etapa 1 — Linux, Redes y Programming

**Producto integrador:** servidor operable + CLI de operaciones.
**Hito H1:** CLI funcionando, logs analizados y un servicio detrás de un proxy con TLS.

| Materia | Guía |
|---|---|
| Linux & Sistemas | [01-linux](../01-linux/README.md) |
| Redes | [02-redes](../02-redes/README.md) |
| Programming & Automation | [03-programming](../03-programming/README.md) |

## Semana tipo (~13 h)

| Día | Horas | Materia | Foco |
|---|---|---|---|
| Lunes | 2 h | Linux | Teoría breve + laboratorio |
| Martes | 2 h | Redes | Teoría breve + laboratorio |
| Miércoles | 2 h | Programming | Teoría breve + laboratorio |
| Jueves | 2 h | Linux | Práctica y troubleshooting |
| Viernes | 2 h | Redes | Práctica, capturas y diagnóstico |
| Sábado | 3 h | Programming 1,5 h + integrador 1,5 h | Consolidar y avanzar el producto integrador |
| Domingo | libre | Opcional: repaso y lectura en inglés | |

**Sesión de 2 h:** 20–30 min de teoría · 80–90 min de laboratorio · 10 min de commit con notas.

## Los 4 bloques

Se pasa al siguiente cuando el anterior está sólido, no por calendario.

| Bloque | Linux | Redes | Programming |
|---|---|---|---|
| 1 · Fundamentos | Filesystem, paquetes, permisos, usuarios | TCP/IP, IP, MAC, puertos, captura de paquetes | grep/sed/awk, JSON/YAML, Makefile, Git básico |
| 2 · Construcción · **Checkpoint 1** | Procesos, systemd, cron, logs, SSH, storage | Subnetting, routing, NAT, DHCP, DNS | Python: archivos, JSON/CSV, requests, argparse |
| 3 · Operación · **Checkpoint 2** | Bash: pipes, funciones, arrays, exit codes | HTTP, TLS, reverse proxy, balanceo | APIs, reintentos, logging, configuración |
| 4 · Entrega | Hardening, backups, troubleshooting | Firewall, troubleshooting, diagramas | Tests, empaquetado, idempotencia |
| **Pausa** | Pendientes, descanso activo, ajustes | | |

**El sábado según el bloque:** en los bloques 2 y 3 se usa para el checkpoint; al cierre del bloque 3, para diagrama y ADR; en el bloque 4 pasa a integrador 2,5 h + Programming 0,5 h, y al final se ensaya la demo.

## Producto integrador

Una sola pieza que junta las tres materias:

1. **Servidor Linux** (proyecto de Linux): usuarios, SSH seguro, firewall, tres scripts operativos y runbook.
2. **Servicio detrás de Nginx con TLS** (proyecto de Redes): una app simple con reverse proxy, HTTPS, diagrama y guía de diagnóstico.
3. **CLI de operaciones** (proyecto de Programming): hace health checks del servicio, analiza los logs de Nginx y genera un reporte JSON/CSV.

**Está terminado cuando** otra persona puede levantarlo desde cero siguiendo el README y el runbook.

## Checkpoints

Tarea en tiempo limitado (60–90 min), sin nota. Sirve para saber qué reforzar.

- **Checkpoint 1 (bloque 2):** diagnosticar y arreglar algo roto que vos mismo prepares, por ejemplo un servicio de systemd que no arranca.
- **Checkpoint 2 (bloque 3):** hacer un cambio controlado o resolver una falla simulada (puerto cerrado, DNS mal, certificado vencido) usando solo logs y comandos de diagnóstico.

## Cierre de la etapa

- [ ] Los tres proyectos finales funcionan y están en el repo.
- [ ] El producto integrador es reproducible con README y runbook.
- [ ] Puedo explicar mis decisiones y qué haría distinto.
- [ ] Una persona externa revisó el proyecto como code review.
- [ ] `PROGRESO.md` actualizado.

**Para avanzar a la Etapa 2:** al menos 2 de las 3 materias más el integrador. Regla que agrego: una de las dos no puede faltar nunca, Linux, porque Docker, Kubernetes y cloud dependen de eso. Lo pendiente se cierra en la pausa, sin saltear fundamentos.

## Checklist de competencias (Etapa 1)

- [ ] Explico DNS, TCP, TLS, rutas y firewall al diagnosticar una conexión.
- [ ] Administro Linux, servicios, logs, usuarios, SSH y backups con un runbook.
- [ ] Escribo scripts Bash/Python con logs, errores manejados, configuración y tests básicos.

## Notas prácticas

- **Entorno:** para Linux y Redes conviene una VM completa (VirtualBox, UTM, Multipass) antes que WSL. La captura de paquetes, systemd, firewall y los labs de routing/NAT se comportan más como un servidor real.
- **Dominio y TLS:** un dominio propio cuesta poco, pero si no querés gastar, podés usar un dominio local con `mkcert` para practicar TLS y el reverse proxy igual.
- **Si te atrasás:** no dupliques la sesión siguiente. Mové la sesión al domingo o a la pausa, o reducí el alcance del proyecto.
