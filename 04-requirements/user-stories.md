# Historias de usuario

> Estado: 🟢 Estable | Última actualización: 2026-06-24
> Autor: Equipo ADSO 3145555 | Equipo: Producto

## Contexto

Este documento contiene las historias de usuario del sistema **Horarios SENA**, organizadas por módulo funcional y prioridad. Cada historia incluye su descripción, criterios de aceptación y relación con los requisitos funcionales.

## Convención de prioridades

| Prioridad | Significado |
|-----------|-------------|
| **P0** | Crítica — bloquea la operación del sistema |
| **P1** | Alta — necesaria para el flujo principal |
| **P2** | Media — amplía la funcionalidad base |
| **P3** | Baja — mejoras y funcionalidades adicionales |

## Resumen por módulo

| Módulo | Historias | Prioridad mínima |
|--------|-----------|------------------|
| Módulo 1 — Seguridad y Acceso | HU-034 a HU-037 | P0 |
| Módulo 2 — Estructura Institucional | HU-001 a HU-005 | P0 |
| Módulo 3 — Infraestructura / Ambientes | HU-006 a HU-009 | P0 |
| Módulo 4 — Catálogos Base | HU-010 a HU-012 | P0 |
| Módulo 5 — Programas de Formación | HU-013 a HU-016 | P1 |
| Módulo 7 — Actores | HU-017 a HU-020 | P0 |
| Módulo 8/11 — Horarios y Motor de Asignación | HU-021 a HU-025 | P0 |
| Módulo 9 — Proyectos Formativos | HU-029 a HU-033 | P2 |
| Módulo 12 — Observaciones e Incidencias | HU-026 a HU-028 | P1 |
| Módulo 15 — Notificaciones y Trazabilidad | HU-038 a HU-040 | P3 |

---

## Módulo 1 — Seguridad y Acceso

| ID | Historia de Usuario | Prioridad | RF Relacionado |
|----|---------------------|-----------|----------------|
| HU-034 | Como usuario, quiero iniciar sesión con usuario y contraseña para acceder al sistema. | P0 | RF-055 |
| HU-035 | Como administrador, quiero asignar roles (Coordinador, Instructor, Administrador) a los usuarios. | P0 | RF-056 |
| HU-036 | Como administrador, quiero gestionar permisos por rol para controlar el acceso a funcionalidades. | P0 | RF-057 |
| HU-037 | Como administrador, quiero ver el historial de auditoría de todas las acciones críticas. | P0 | RF-058 |

---

## Módulo 2 — Estructura Institucional

| ID | Historia de Usuario | Prioridad | RF Relacionado |
|----|---------------------|-----------|----------------|
| HU-001 | Como administrador, quiero crear y listar macroregiones para organizar la estructura territorial del SENA. | P0 | RF-001 |
| HU-002 | Como administrador, quiero crear y listar microregiones asociadas a una macroregión. | P0 | RF-002 |
| HU-003 | Como administrador, quiero crear y listar departamentos y municipios para detallar la ubicación. | P0 | RF-003, RF-004 |
| HU-004 | Como administrador, quiero crear y listar centros de formación asociados a una microregión. | P0 | RF-006 |
| HU-005 | Como administrador, quiero crear y listar unidades institucionales asociadas a un centro de formación y una ubicación. | P0 | RF-007 |

**Criterios de aceptación comunes:**
- Los campos obligatorios deben validarse antes de guardar.
- No se permiten códigos duplicados.
- El estado (Activo/Inactivo) controla la disponibilidad en otros módulos.

---

## Módulo 3 — Infraestructura / Ambientes

| ID | Historia de Usuario | Prioridad | RF Relacionado |
|----|---------------------|-----------|----------------|
| HU-006 | Como administrador, quiero crear y listar ambientes de aprendizaje con código, nombre, tipo, capacidad y ubicación. | P0 | RF-008, RF-009 |
| HU-007 | Como administrador, quiero gestionar el inventario de recursos asociados a un ambiente, incluyendo equipos y mobiliario. | P0 | RF-010 |
| HU-008 | Como administrador, quiero cambiar el estado de un ambiente entre Disponible, Mantenimiento y Fuera de servicio. | P0 | RF-011 |
| HU-009 | Como coordinador, quiero consultar los ambientes disponibles para asignar horarios. | P0 | RF-012 |

**Criterios de aceptación comunes:**
- Un ambiente en estado Mantenimiento no puede asignarse a horarios.
- El inventario debe mostrar la cantidad y el estado de cada recurso.

---

## Módulo 4 — Catálogos Base

| ID | Historia de Usuario | Prioridad | RF Relacionado |
|----|---------------------|-----------|----------------|
| HU-010 | Como administrador, quiero crear y listar catálogos (Modalidades, Jornadas, Estados) para estandarizar la información del sistema. | P0 | RF-013 |
| HU-011 | Como administrador, quiero agregar detalles a los catálogos, como Presencial o Virtual. | P0 | RF-014 |
| HU-012 | Como administrador, quiero gestionar parámetros globales como la capacidad máxima y las horas máximas permitidas. | P0 | RF-016 |

**Criterios de aceptación comunes:**
- Los códigos de catálogo deben ser únicos.
- Los cambios en catálogos y parámetros deben quedar registrados en auditoría.

---

## Módulo 5 — Programas de Formación

| ID | Historia de Usuario | Prioridad | RF Relacionado |
|----|---------------------|-----------|----------------|
| HU-013 | Como administrador, quiero crear y listar líneas tecnológicas, redes tecnológicas y redes de conocimiento. | P1 | RF-019, RF-020, RF-021 |
| HU-014 | Como administrador, quiero crear y listar programas de formación con código, nombre, tipo, modalidad y duración. | P1 | RF-022 |
| HU-015 | Como administrador, quiero crear y listar competencias y RAPs asociados a un programa. | P1 | RF-023, RF-024, RF-025 |
| HU-016 | Como coordinador, quiero consultar las competencias de un programa para asignar horarios correctamente. | P1 | RF-026, RF-027 |

**Criterios de aceptación comunes:**
- Un programa de tipo Titulado no puede marcarse como `a_la_medida`.
- Los RAPs deben ser únicos en el catálogo maestro.
- La jerarquía Línea → Red Tecnológica → Red de Conocimiento → Programa debe respetarse.

---

## Módulo 7 — Actores

| ID | Historia de Usuario | Prioridad | RF Relacionado |
|----|---------------------|-----------|----------------|
| HU-017 | Como administrador, quiero crear y listar instructores con nombre, email, tipo (planta/contratista) y especialidades. | P0 | RF-028 |
| HU-018 | Como administrador, quiero crear y listar aprendices y fichas. | P0 | RF-029, RF-030 |
| HU-019 | Como administrador, quiero matricular aprendices en fichas. | P0 | RF-031 |
| HU-020 | Como coordinador, quiero consultar instructores disponibles filtrando por especialidad. | P0 | RF-034 |

**Criterios de aceptación comunes:**
- Un instructor en estado INACTIVO no puede asignarse a horarios.
- Un aprendiz debe estar matriculado en una ficha para aparecer en los horarios.

---

## Módulo 8 y 11 — Horarios y Motor de Asignación

| ID | Historia de Usuario | Prioridad | RF Relacionado |
|----|---------------------|-----------|----------------|
| HU-021 | Como coordinador, quiero definir franjas horarias indicando día, hora de inicio y hora de fin. | P0 | RF-035 |
| HU-022 | Como coordinador, quiero asignar un horario combinando instructor, ambiente, ficha y franja horaria. | P0 | RF-036 |
| HU-023 | Como coordinador, quiero que el sistema impida asignar el mismo instructor, ambiente o ficha en franjas solapadas. | P0 | RF-037, RF-038, RF-039 |
| HU-024 | Como coordinador, quiero consultar horarios filtrando por instructor, ambiente o ficha. | P0 | RF-042 |
| HU-025 | Como coordinador, quiero cancelar un horario registrando el motivo de la cancelación. | P1 | RF-041 |

**Criterios de aceptación comunes:**
- El sistema valida conflictos en tiempo real y muestra un mensaje de error descriptivo.
- Las sesiones de clase ya ejecutadas no pueden modificarse.

---

## Módulo 12 — Observaciones e Incidencias

| ID | Historia de Usuario | Prioridad | RF Relacionado |
|----|---------------------|-----------|----------------|
| HU-026 | Como coordinador, quiero registrar observaciones sobre un horario con severidad (Info, Warning, Critical). | P1 | RF-044 |
| HU-027 | Como coordinador, quiero actualizar el estado de una observación entre Abierta, En proceso y Resuelta. | P1 | RF-045 |
| HU-028 | Como coordinador, quiero listar observaciones filtrando por horario o instructor. | P1 | RF-046 |

---

## Módulo 9 — Proyectos Formativos

| ID | Historia de Usuario | Prioridad | RF Relacionado |
|----|---------------------|-----------|----------------|
| HU-029 | Como coordinador, quiero crear un proyecto formativo con nombre, objetivo, fechas y ficha asociada. | P2 | RF-047 |
| HU-030 | Como coordinador, quiero gestionar fases, actividades y entregables de un proyecto. | P2 | RF-048, RF-049, RF-050 |
| HU-031 | Como coordinador, quiero definir dependencias entre fases para que se respete el orden de ejecución. | P2 | RF-051 |
| HU-032 | Como instructor, quiero aprobar o rechazar entregables con comentarios. | P2 | RF-054 |
| HU-033 | Como coordinador, quiero ver el avance del proyecto expresado como porcentaje de fases completadas. | P2 | RF-053 |

---

## Módulo 15 — Notificaciones y Trazabilidad

| ID | Historia de Usuario | Prioridad | RF Relacionado |
|----|---------------------|-----------|----------------|
| HU-038 | Como instructor, quiero recibir una notificación por email cuando se me asigne un horario. | P3 | RF-061 |
| HU-039 | Como instructor, quiero recibir una notificación por email cuando se cancele un horario asignado a mí. | P3 | RF-062 |
| HU-040 | Como administrador, quiero generar reportes en PDF o Excel sobre horarios, ocupación y carga de instructores. | P3 | RF-064 |

---

## Referencias

- [functional.md](./functional.md) — Requisitos funcionales
- [non-functional.md](./non-functional.md) — Requisitos no funcionales
- [traceability-matrix.md](./traceability-matrix.md) — Matriz de trazabilidad
- [03-product/product-backlog.md](../03-product/product-backlog.md) — Backlog de producto