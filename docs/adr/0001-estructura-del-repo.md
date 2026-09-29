# ADR-0001: Estructura del repo de práctica

- **Estado:** Aceptada
- **Fecha:** 2026-09-29
- **Reemplaza a:** ninguno

## Contexto

Necesito un lugar único donde guardar notas, laboratorios y proyectos de todas las materias, que sea fácil de navegar y que pueda escalar de 3 materias a 12 sin reorganizarlo. Además quiero que lo que hago sea reproducible y que las decisiones técnicas queden registradas.

## Decisión

- Un solo repo (`carrera-devops`) con una carpeta numerada por materia.
- Cada materia con el mismo esquema: `notas/`, `labs/` y `proyecto-final/`.
- Decisiones técnicas registradas como ADRs numerados en `docs/adr/`, con una plantilla común.
- Trabajo con ramas y PRs hacia `main`, y un commit al cerrar cada sesión.
- Un `PROGRESO.md` corto con qué sé hacer, en qué estoy y qué me falta por materia.

## Alternativas consideradas

- **Un repo por materia:** descartada. Más overhead de gestión y se pierde la visión de conjunto.
- **Estructura libre sin esquema fijo:** descartada. Termino dudando dónde guardar cada cosa y el repo se desordena.
- **Notas fuera del repo (Notion, etc.):** descartada. Prefiero tener notas y código juntos y versionados.

## Consecuencias

**Ganamos:** navegación predecible, todo versionado y proyectos reproducibles.

**Aceptamos:** algo de disciplina para mantener el esquema y escribir ADRs solo cuando la decisión lo merece.
