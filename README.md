# sideproject-api-banco

> API REST en capas con FastAPI y PostgreSQL que sirve los datos de clientes, cuentas y movimientos de un banco.

**Estado:** 🚧 sin empezar · **Tipo:** API REST · **Módulo del programa:** 06/06 · APIs con FastAPI

## La problemática

Los datos que deja el pipeline en PostgreSQL ya son fiables, pero la app móvil y el equipo de analítica no deberían entrar a la base para consultarlos. Hay que servirlos con una API validada, con reglas de negocio y probada sin base de datos.

## Los datos

| Dónde | Qué es |
|---|---|
| `datos/banco.sql` | Script de PostgreSQL con las tablas `clientes` y `cuentas` (base `banco_python`) |
| `datos/movimientos.csv` | 400 movimientos bancarios limpios, julio a septiembre de 2026 |

Los archivos de `datos/` son **sintéticos**, generados para practicar: no corresponden a personas ni a operaciones reales.

## Qué hay que construir

El enunciado completo, con sus hitos y cómo comprobar cada uno, está en [`RETO.md`](RETO.md). No trae solución: el diseño es tuyo.

- [`docs/REGLAS.md`](docs/REGLAS.md): cómo se trabaja un sideproject y qué debe tener este README al terminar.
- [`docs/RUBRICA.md`](docs/RUBRICA.md): con qué criterios se evalúa.

## Cómo se ejecuta

*Pendiente: se escribe al cerrar el primer hito. Los comandos exactos, desde `git clone`.*

## Decisiones

*Pendiente: tres decisiones técnicas y la alternativa que se descartó en cada una.*

## Qué aprendí

*Pendiente.*

---

Reto del programa de Python e ingeniería de datos: [UNIR_Python_Certification](https://github.com/KevinMondragonDev/UNIR_Python_Certification).
