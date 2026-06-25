# Roadmap del producto

> Estado: 🟢 Estable | Última actualización: 2026-06-24
> Autor: ADSO 3145555 | Equipo: Producto

## Contexto

Define las fases de desarrollo, hitos clave y evolución planificada del producto. El enfoque es entregar valor de forma incremental, priorizando las funcionalidades más críticas primero.

## Regla de oro

> Ninguna fase inicia sin que los criterios de aceptación de la fase anterior estén cumplidos.

---

## Fase 1 — MVP
**Duración estimada:** 4–6 semanas

**Objetivo:** Sistema funcional que permita programar horarios con validación automática de conflictos.

| Entregable | Módulos | Criterio de aceptación |
|------------|---------|------------------------|
| Estructura institucional y catálogos | M2, M4 | CRUD de macroregiones, microregiones, centros y sedes. Catálogos de estados, jornadas y modalidades. |
| Gestión de ambientes y actores | M3, M7 | CRUD de ambientes (capacidad, ubicación). CRUD de instructores y aprendices. |
| Motor de horarios | M8, M11 | Asignación de instructor + ambiente + ficha + franja. Validación de cruces sin doble asignación. |
| Autenticación básica | M1 | Login con JWT. Roles: Coordinador, Instructor, Administrador. |
| Interfaz de usuario | Frontend | Vista de horarios por instructor, ambiente y ficha. Formularios de creación. |

**Criterio de éxito:** El sistema bloquea cualquier asignación que solape instructor, ambiente o ficha en el mismo bloque horario.

---

## Fase 2 — Extensión Académica
**Duración estimada:** 3–4 semanas

**Objetivo:** Incorporar gestión académica (programas, competencias, RAPs) y registro de observaciones e incidencias.

| Entregable | Módulos | Criterio de aceptación |
|------------|---------|------------------------|
| Programas y oferta | M5, M6 | CRUD de programas, competencias y RAPs. Relación programa → ficha. |
| Observaciones e incidencias | M12 | Registro de novedades sobre horarios (ej. "Instructor ausente", "Ambiente dañado"). |
| Mejoras en horarios | M8, M11 | Filtros avanzados. Vista de horarios por programa o competencia. |

**Criterio de éxito:** Los coordinadores pueden asociar horarios a competencias y registrar incidencias.

---

## Fase 3 — Proyectos Formativos y Monitoreo
**Duración estimada:** 4–5 semanas

**Objetivo:** Gestionar proyectos formativos con fases, dependencias, entregables y monitoreo de avance.

| Entregable | Módulos | Criterio de aceptación |
|------------|---------|------------------------|
| Proyectos formativos | M9, M13 | Gestión de proyectos: fases, actividades, entregables y dependencias. |
| Coordinación y evaluación | M14 | Asignación de horas para revisión de proyectos. |
| Monitoreo y KPIs | M9 | Tableros de avance, alertas de riesgo y reportes básicos. |

**Criterio de éxito:** Los instructores pueden gestionar proyectos formativos y monitorear el avance de los aprendices.

---

## Fase 4 — Notificaciones, Trazabilidad y Reportes
**Duración estimada:** 2–3 semanas

**Objetivo:** Completar funcionalidades transversales: notificaciones, auditoría y reportes avanzados.

| Entregable | Módulos | Criterio de aceptación |
|------------|---------|------------------------|
| Notificaciones | M15 | Alertas por email y dashboard para cambios de horario e incidencias. |
| Auditoría completa | M1 | Registro inmutable de todas las acciones críticas. |
| Reportes avanzados | M10 | Exportación a PDF/Excel de horarios, ocupación de ambientes y carga de instructores. |

**Criterio de éxito:** El sistema tiene trazabilidad completa y genera reportes operativos.

---

## Hitos clave

| Hito | Fecha estimada | Descripción |
|------|----------------|-------------|
| **Hito 1** | Fin semana 4 | MVP funcional con horarios y validación de conflictos |
| **Hito 2** | Fin semana 8 | Extensión académica completa |
| **Hito 3** | Fin semana 13 | Proyectos formativos y monitoreo operativo |
| **Hito 4** | Fin semana 16 | Sistema completo con notificaciones, auditoría y reportes |

## Dependencias externas

- **Datos de SOFIA Plus:** Necesarios para pruebas de integración (fichas, programas, aprendices).
- **Aprobación de arquitectura:** La definición final de microservicios debe estar aprobada antes del desarrollo.
- **Infraestructura:** Se requiere servidor o entorno Docker para despliegue.

## Referencias

- [vision.md](./vision.md) — Visión del producto
- [product-backlog.md](./product-backlog.md) — Backlog priorizado
- [01-context/scope.md](../01-context/scope.md) — Alcance del proyecto