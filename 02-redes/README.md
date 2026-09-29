# 02 · Redes

**Objetivo:** explicar y diagnosticar el camino de una petición de cliente a servidor.
**Herramientas:** `ip`, `ss`, `ping`, `traceroute`, `dig`, `curl`, Wireshark, Nginx, `ufw`.

Guía general de la etapa: [docs/etapa-1.md](../docs/etapa-1.md)

## Bloque 1 · Fundamentos
- [ ] Explicar el modelo TCP/IP y qué pasa en cada capa
- [ ] Ver tu interfaz, IP, MAC y rutas con `ip a` e `ip route`
- [ ] Listar puertos y conexiones con `ss -tulpn`
- [ ] Capturar con Wireshark: un `ping`, un `curl` a HTTP y un handshake TCP (SYN, SYN-ACK, ACK)
- [ ] Diferenciar TCP y UDP con una captura de cada uno

## Bloque 2 · Construcción
- [ ] Subnetting a mano: 10 ejercicios de CIDR (rango, máscara, hosts)
- [ ] Lab con `ip netns`: dos subredes conectadas por un router en tu máquina
- [ ] Leer tablas de rutas y entender NAT y DHCP
- [ ] DNS con `dig`: registros A, CNAME, MX, TTL y resolución paso a paso
- [ ] **Checkpoint 1**

## Bloque 3 · Operación
- [ ] HTTP con `curl -v`: métodos, headers, códigos de estado
- [ ] TLS: `openssl s_client`, leer la cadena de certificados
- [ ] Poner una app detrás de Nginx como reverse proxy
- [ ] Activar HTTPS (Let's Encrypt o `mkcert` para un dominio local)
- [ ] Balanceo básico con dos backends en un `upstream`
- [ ] **Checkpoint 2** + diagrama de red + ADR corto

## Bloque 4 · Entrega
- [ ] Reglas de firewall con `ufw` (y mirar qué genera por debajo)
- [ ] Reproducir y diagnosticar 4 fallas: DNS, ruta, puerto cerrado y certificado
- [ ] Diagrama de red final en diagrams.net
- [ ] Guía de diagnóstico: "si pasa X, revisá Y con este comando"

## Proyecto final: red de aplicación

| Entregable | Criterio |
|---|---|
| Diagrama | Muestra el camino de una petición de punta a punta |
| Dominio | Real o local resolviendo a tu servidor |
| Reverse proxy | Nginx delante de la app |
| TLS | HTTPS válido (o CA local si es dominio local) |
| Firewall | Solo puertos necesarios abiertos |
| Guía de diagnóstico | Cubre DNS, ruta, puerto y TLS |

**Logrado cuando:** funciona, otra persona lo reproduce y podés explicar qué pasa en cada salto de una petición.

## Estructura de carpetas

```
02-redes/
├── notas/            # comandos, capturas, conceptos
├── labs/             # 01-captura/, 02-netns/, 03-nginx/, ...
└── proyecto-final/   # diagrama, configs, guía de diagnóstico
```

## Recursos
- Documentación de Wireshark, Nginx y Let's Encrypt
- *Computer Networking: A Top-Down Approach* (Kurose y Ross), como referencia
- Zines de Julia Evans sobre redes y Linux
