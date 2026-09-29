# carrera-devops

Repo de práctica: notas, laboratorios y proyectos de DevOps, organizados por materia.

## Estructura

```
carrera-devops/
├── README.md
├── PROGRESO.md
├── docs/
│   └── adr/              # decisiones técnicas (ver template.md)
├── 01-linux/
├── 02-redes/
└── 03-programming/
```

Cada materia tiene el mismo esquema:

| Carpeta | Para qué |
|---|---|
| `notas/` | Comandos, conceptos y fallas que me encontré |
| `labs/` | Ejercicios reproducibles, uno por carpeta o archivo |
| `proyecto-final/` | Proyecto integrador con README, diagrama, ADRs y runbook |

Las materias nuevas se agregan con el mismo formato (`04-docker`, `05-cicd`, etc.).

## Cómo trabajo acá

- Rama por tema (`linux/permisos`) y PR hacia `main`.
- Commits con prefijo de materia: `linux: permisos y usuarios, lab 2`.
- Cada lab debe poder repetirse desde cero con lo que está escrito.
- Las decisiones técnicas importantes van como ADR en `docs/adr/`.

## ADRs

| ADR | Título | Estado |
|---|---|---|
| [0001](docs/adr/0001-estructura-del-repo.md) | Estructura del repo de práctica | Aceptada |
