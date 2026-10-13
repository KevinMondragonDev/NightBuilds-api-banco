# 🚀 Sideproject — API del banco

**Repositorio:** `sideproject-api-banco` · **Tipo:** API REST · **Tiempo:** 8–10 h · **Después de:** lecciones 1 a 4 de esta sección

> Reglas, README y lista de cierre: [`SIDEPROJECTS.md`](docs/REGLAS.md). **No hay solución: el diseño es tuyo.**

## El caso

Los datos que tu pipeline deja en PostgreSQL ya son fiables. Ahora la app móvil del banco y el equipo de analítica los quieren consultar sin entrar a la base. Vas a servirlos con una API.

Un Data Engineer no solo mueve datos: a menudo también los sirve. Aquí construyes la API sobre datos preparados por un pipeline.

## Qué practicas

| Lección | Dónde aparece |
|---|---|
| Primera API | Rutas, parámetros, códigos de estado, `/docs` |
| Modelos y validación | Modelos de entrada y de salida distintos |
| Capas y PostgreSQL | Router → servicio → repositorio, con `Depends` |
| Tests y errores | Manejadores de errores y tests sin base de datos |

## Hitos

**Hito 1 — Contrato primero.** En un `API.md`, antes del código: la tabla de endpoints con verbo, ruta, parámetros, respuesta y códigos posibles.
*Comprueba:* cada endpoint responde a una pregunta de un usuario real.

**Hito 2 — Lectura.** Con repositorio en memoria: `GET /clientes/{id}`, `GET /cuentas/{id}`, `GET /cuentas/{id}/movimientos` (filtros por fecha y tipo, paginación) y `GET /cuentas/{id}/resumen`.
*Comprueba:* en `/docs`, un caso válido y uno inválido de cada uno.

**Hito 3 — PostgreSQL.** Repositorio real con `psycopg`, conexión por variables de entorno e inyectada con `Depends`.
*Comprueba:* cambiar de memoria a PostgreSQL no toca routers ni servicios.

**Hito 4 — Escritura con reglas.** `POST /movimientos` y `POST /transferencias` (una sola transacción). Errores de negocio con su código: 404, 409, 422.
*Comprueba:* una transferencia que falla a la mitad no mueve dinero.

**Hito 5 — Tests.** Un test por código de estado de cada endpoint, con el repositorio en memoria inyectado.
*Comprueba:* `pytest` pasa con PostgreSQL apagado.

**Hito 6 — Lista para otros.** `docker compose up` levanta la API y PostgreSQL con datos de ejemplo.
*Comprueba:* en una máquina limpia, un comando y `/docs` funciona.

## Preguntas para defenderlo

- ¿Qué capa tocarías para cambiar PostgreSQL por DynamoDB? ¿Y para cambiar una regla de negocio?
- ¿Por qué el modelo de salida no es el mismo que el de entrada?
- Dos transferencias simultáneas de la misma cuenta: ¿qué puede salir mal?
- Si ya has hecho APIs con otro framework (Spring Boot, Express, Django), compara: ¿qué te resultó más simple y qué echaste de menos?

## Súbelo de nivel

- Autenticación con una clave en la cabecera (`Depends` + `Header`).
- `GET /cuentas/{id}/resumen` leyendo de DynamoDB sobre **Floci**, alimentado por tu pipeline de eventos.
