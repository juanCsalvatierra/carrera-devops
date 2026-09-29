# 03 · Programming & Automation

**Objetivo:** construir herramientas pequeñas, confiables y reutilizables.
**Herramientas:** Python, Bash, `requests`, `argparse`, `logging`, `pytest`, `jq`, `yq`, Make.

Guía general de la etapa: [docs/etapa-1.md](../docs/etapa-1.md)

Esta materia tiene menos horas semanales que las otras dos (Programming va el miércoles y parte del sábado). Mantené los labs chicos.

## Bloque 1 · Fundamentos
- [ ] `grep`, `sed` y `awk` sobre un log real
- [ ] `jq` y `yq` para leer y transformar JSON/YAML
- [ ] Convenciones de scripts: shebang, `set -euo pipefail`, `shellcheck`
- [ ] Un `Makefile` con targets (`test`, `lint`, `run`)
- [ ] Git básico: rama, commit, merge, resolver un conflicto, PR y `.gitignore`

## Bloque 2 · Construcción
- [ ] Python: entorno virtual (`venv`) y manejo de dependencias
- [ ] Leer y escribir archivos, JSON y CSV
- [ ] Consumir una API con `requests` y guardar los resultados
- [ ] CLI con `argparse` (subcomandos y `--help`)
- [ ] Ejecutar comandos del sistema con `subprocess`
- [ ] **Checkpoint 1**

## Bloque 3 · Operación
- [ ] Autenticación contra una API con token desde variable de entorno
- [ ] Reintentos con backoff y manejo de excepciones
- [ ] `logging` en lugar de `print`
- [ ] Configuración por entorno (variables de entorno o archivo)
- [ ] Analizar logs y emitir alertas simples
- [ ] **Checkpoint 2** + diagrama de la CLI + ADR corto

## Bloque 4 · Entrega
- [ ] Tests con `pytest` (casos felices y de error)
- [ ] Códigos de salida coherentes
- [ ] Empaquetado liviano con `pyproject.toml`
- [ ] Hacer el script idempotente: correrlo dos veces da el mismo resultado
- [ ] README con ejemplos de uso

## Proyecto final: CLI de operaciones

Idea de diseño, ajustala a lo que necesites:

```
ops check    # health checks / inventario de servicios
ops logs     # análisis de logs (por ejemplo, los de Nginx)
ops report   # reporte en JSON o CSV
```

| Entregable | Criterio |
|---|---|
| CLI con `--help` | Subcomandos claros y documentados |
| Configuración | Por entorno, sin secretos en el código |
| Logging y errores | Fallas manejadas y códigos de salida correctos |
| Tests | `pytest` corre y pasa |
| Reporte | Salida en JSON/CSV |

**Logrado cuando:** funciona, otra persona lo instala y lo usa con el README, y podés explicar tus decisiones.

## Estructura de carpetas

```
03-programming/
├── notas/            # snippets, errores frecuentes
├── labs/             # 01-awk-logs/, 02-api-requests/, ...
└── proyecto-final/   # la CLI, tests, README
```

## Recursos
- Tutorial oficial de Python y documentación de `argparse`, `logging` y `pytest`
- *Automate the Boring Stuff with Python* (Al Sweigart, gratis online)
- *Pro Git* (gratis online) para el bloque de Git
- Manual de `jq` y `shellcheck`
