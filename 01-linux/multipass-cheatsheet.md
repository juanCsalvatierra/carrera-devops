# Cheatsheet de Multipass

Guardar en: `~/carrera-devops/01-linux/multipass-cheatsheet.md`

## Ciclo de vida

| Comando | Qué hace |
|---|---|
| `multipass launch 24.04 --name lab` | Crear y arrancar una VM |
| `multipass launch 24.04 -n lab -c 2 -m 2G -d 20G` | Igual, con CPUs, memoria y disco (forma corta) |
| `multipass list` | Ver todas las VMs, estado e IP |
| `multipass info lab` | Detalle: IP, recursos, disco usado, montajes |
| `multipass start lab` | Encender |
| `multipass stop lab` | Apagar (limpio) |
| `multipass restart lab` | Reiniciar |
| `multipass suspend lab` | Pausar guardando el estado |
| `multipass delete lab` | Marcar para borrar (recuperable) |
| `multipass recover lab` | Recuperar una VM borrada |
| `multipass purge` | Eliminar definitivamente las VMs borradas |
| `multipass delete lab --purge` | Borrar y purgar de una vez |

## Acceso

| Comando | Qué hace |
|---|---|
| `multipass shell lab` | Abrir una shell dentro de la VM |
| `multipass exec lab -- ls /etc` | Ejecutar un comando sin entrar |
| `multipass exec lab -- sudo apt update` | Ejecutar con sudo |

El `--` separa los argumentos de Multipass de los del comando.

## Snapshots

La VM tiene que estar detenida.

| Comando | Qué hace |
|---|---|
| `multipass snapshot lab --name limpia` | Crear snapshot |
| `multipass list --snapshots` | Ver snapshots |
| `multipass info lab --snapshots` | Detalle de snapshots de una VM |
| `multipass restore lab.limpia` | Volver a ese estado |
| `multipass delete lab.limpia` | Borrar un snapshot |

## Archivos entre Mac y VM

| Comando | Qué hace |
|---|---|
| `multipass transfer archivo.txt lab:/home/ubuntu/` | Mac → VM |
| `multipass transfer lab:/home/ubuntu/archivo.txt .` | VM → Mac |
| `multipass mount ~/carrera-devops lab:/home/ubuntu/repo` | Montar carpeta compartida |
| `multipass umount lab` | Desmontar |

Si `mount` falla, puede ser por el acceso de macOS a carpetas (el daemon corre como root). `transfer` suele ser más simple.

## Imágenes y utilidades

| Comando | Qué hace |
|---|---|
| `multipass find` | Ver imágenes disponibles |
| `multipass version` | Versión del cliente y del daemon |
| `multipass get local.driver` | Ver el driver de virtualización |
| `multipass help` | Ayuda general |
| `multipass help launch` | Ayuda de un comando |

## Flujo típico del laboratorio

```bash
multipass stop lab
multipass snapshot lab --name antes-de-ssh
multipass start lab
multipass shell lab
# ... practicar, romper cosas ...
exit
multipass stop lab
multipass restore lab.antes-de-ssh   # si algo salió mal
multipass start lab
```

**Regla práctica:** snapshot antes de tocar SSH, firewall o permisos de sistema.

## Troubleshooting (problemas que ya viste)

| Síntoma | Causa | Solución |
|---|---|---|
| `Remote "release" is unknown or unreachable` | Fallo temporal de red o daemon | Reintentar, `multipass find`, revisar VPN/proxy |
| `failed to download from '...img'` | La descarga interna de Multipass falla | Bajar la imagen con `curl -LO` y lanzar con `file:///ruta/absoluta` |
| `Custom image ... $HOME ... does not exist` | `$HOME` no se expande dentro de `file://` | Usar la ruta absoluta escrita completa (tres barras: `file:///Users/...`) |
| `Failed to copy ... to /var/root/...` | El daemon (root) no puede leer `~/Downloads` | Copiar la imagen a `/tmp` y lanzar desde ahí |
| `instance lab already exists` | Intento fallido dejó una instancia a medias | `multipass delete lab --purge` y reintentar |
