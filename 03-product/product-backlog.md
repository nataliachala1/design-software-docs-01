# Product Backlog

> Estado: 🟢 Estable | Última actualización: 2026-06-24
> Autor: ADSO 3145555 | Equipo: Producto

## Contexto

Contiene todas las funcionalidades priorizadas por valor de negocio y dependencias técnicas. Cada ítem incluye una historia de usuario y sus criterios de aceptación.

## Regla de oro

> Sin criterios de aceptación claros, una historia de usuario no entra al sprint.

## Prioridades

| Prioridad | Significado |
|-----------|-------------|
| **P0 — Crítica** | Imprescindible para el MVP. El sistema no funciona sin esto. |
| **P1 — Alta** | Importante, pero puede esperar a Fase 2. |
| **P2 — Media** | Valor añadido, para Fase 3 o posterior. |
| **P3 — Baja** | Deseable, pero no crítico. |

---

## 🔴 Fase 1 — MVP (P0)

| ID | Historia de Usuario | Criterios de Aceptación |
|----|---------------------|-------------------------|
| **HU-001** | Como administrador, quiero crear y listar macroregiones, microregiones, departamentos y municipios. | 1. Puedo crear una macroregión con nombre.<br>2. Puedo crear una microregión asociada a una macroregión.<br>3. Puedo crear departamento y municipio.<br>4. Los listados muestran jerarquía. |
| **HU-002** | Como administrador, quiero crear y listar centros de formación y sedes. | 1. Puedo crear un centro asociado a una microregión.<br>2. Puedo crear una sede asociada a un centro.<br>3. Puedo asignar ubicación (dirección, coordenadas).<br>4. Los estados Activo/Inactivo son funcionales. |
| **HU-003** | Como administrador, quiero gestionar catálogos base (modalidades, jornadas, estados, tipos de formación). | 1. Puedo crear un catálogo (ej. Modalidades).<br>2. Puedo agregar detalles (ej. Presencial, Virtual).<br>3. Los detalles tienen vigencia (fecha inicio/fin).<br>4. No se permiten códigos duplicados. |
| **HU-004** | Como administrador, quiero crear y listar ambientes de aprendizaje. | 1. Puedo crear un ambiente con código, nombre, tipo, capacidad y ubicación.<br>2. Puedo asociarlo a un centro y sede.<br>3. Puedo cambiar el estado (Disponible, Mantenimiento, etc.). |
| **HU-005** | Como administrador, quiero crear y listar instructores. | 1. Puedo crear un instructor con nombre, email y tipo (planta/contratista).<br>2. Puedo asignar especialidades.<br>3. El instructor tiene estado Activo/Inactivo. |
| **HU-006** | Como administrador, quiero crear y listar aprendices y fichas. | 1. Puedo crear una ficha con código, programa y jornada.<br>2. Puedo matricular un aprendiz en una ficha.<br>3. El aprendiz tiene estado (Activo, Retirado, etc.). |
| **HU-007** | Como coordinador, quiero crear y listar franjas horarias. | 1. Puedo definir una franja con día, hora inicio y hora fin.<br>2. La franja queda activa para usarse en horarios. |
| **HU-008** | Como coordinador, quiero asignar un horario: instructor + ambiente + ficha + franja horaria. | 1. Puedo seleccionar instructor, ambiente, ficha y franja.<br>2. El sistema valida que no haya conflicto (instructor, ambiente, ficha).<br>3. Si hay conflicto, muestra error y no guarda.<br>4. El horario tiene estado (Programado, Cancelado, Ejecutado). |
| **HU-009** | Como coordinador, quiero consultar horarios por instructor, ambiente o ficha. | 1. Puedo filtrar por instructor, ambiente o ficha.<br>2. Los resultados se muestran en tabla o calendario. |
| **HU-010** | Como usuario, quiero iniciar sesión con usuario y contraseña. | 1. Si las credenciales son correctas, obtengo un token JWT.<br>2. Si son incorrectas, muestra error.<br>3. El token expira a las 8 horas. |
| **HU-011** | Como administrador, quiero asignar roles a usuarios. | 1. Puedo asignar rol: Coordinador, Instructor o Administrador.<br>2. Cada rol tiene permisos específicos. |

---

## 🟡 Fase 2 — Extensión Académica (P1)

| ID | Historia de Usuario | Criterios de Aceptación |
|----|---------------------|-------------------------|
| **HU-012** | Como administrador, quiero crear y listar líneas tecnológicas, redes tecnológicas y redes de conocimiento. | 1. Puedo crear cada nivel de la jerarquía.<br>2. La relación Línea → Red Tecnológica → Red de Conocimiento se respeta. |
| **HU-013** | Como administrador, quiero crear y listar programas de formación. | 1. Puedo crear un programa con código, nombre, tipo, modalidad y duración.<br>2. Puedo asociarlo a una red de conocimiento.<br>3. `a_la_medida` solo aplica para Complementaria.<br>4. El programa tiene vigencia (fecha inicio/fin). |
| **HU-014** | Como administrador, quiero crear y listar competencias y RAPs. | 1. Puedo crear una competencia con código, nombre y horas totales.<br>2. Puedo crear un RAP asociado a una competencia.<br>3. Un RAP es único en el catálogo maestro.<br>4. Puedo asociar competencias a programas con horas específicas. |
| **HU-015** | Como coordinador, quiero registrar observaciones en un horario. | 1. Puedo agregar una observación con texto, autor y severidad (Info, Warning, Critical).<br>2. La observación tiene estado: Abierta, En proceso, Resuelta. |
| **HU-016** | Como coordinador, quiero cancelar un horario. | 1. Puedo cambiar el estado a "Cancelado".<br>2. La cancelación queda registrada con motivo y responsable. |
| **HU-017** | Como instructor, quiero consultar mi horario asignado. | 1. Puedo ver mi horario semanal.<br>2. Puedo ver los detalles de cada sesión (ambiente, ficha, franja). |

---

## 🟢 Fase 3 — Proyectos Formativos (P2)

| ID | Historia de Usuario | Criterios de Aceptación |
|----|---------------------|-------------------------|
| **HU-018** | Como coordinador, quiero crear un proyecto formativo. | 1. Puedo crear un proyecto con nombre, objetivo y fechas.<br>2. Puedo asociarlo a una ficha y programa.<br>3. El proyecto tiene estado: Planeación, Ejecución, Evaluación, Finalizado. |
| **HU-019** | Como coordinador, quiero definir fases y actividades de un proyecto. | 1. Puedo agregar fases al proyecto (ej. Análisis, Diseño).<br>2. Puedo agregar actividades a cada fase.<br>3. Puedo definir dependencias entre fases. |
| **HU-020** | Como instructor, quiero gestionar entregables y evidencias de un proyecto. | 1. Puedo crear entregables para una actividad.<br>2. Puedo subir evidencias a un entregable.<br>3. Puedo aprobar o rechazar un entregable.<br>4. No se puede aprobar sin evidencia. |
| **HU-021** | Como coordinador, quiero monitorear el avance de los proyectos formativos. | 1. Puedo ver un tablero con el avance por proyecto y por aprendiz.<br>2. Puedo ver alertas de riesgo (retrasos, dependencias bloqueadas). |
| **HU-022** | Como coordinador, quiero asignar horas para revisión de proyectos. | 1. Puedo asignar un espacio horario para revisión.<br>2. La revisión no interfiere con los horarios regulares. |

---

## ⚪ Fase 4 — Transversales (P3)

| ID | Historia de Usuario | Criterios de Aceptación |
|----|---------------------|-------------------------|
| **HU-023** | Como administrador, quiero generar reportes en PDF/Excel de horarios, ocupación y carga de instructores. | 1. Puedo exportar horarios por instructor, ambiente o ficha a PDF.<br>2. Puedo exportar reporte de ocupación de ambientes.<br>3. Puedo exportar carga horaria de instructores. |
| **HU-024** | Como usuario, quiero recibir notificaciones de cambios en mi horario. | 1. Recibo email al asignarme un horario o al cancelarse uno mío.<br>2. Recibo alertas en el dashboard. |
| **HU-025** | Como administrador, quiero ver el historial de cambios (auditoría) de cualquier entidad. | 1. Puedo ver quién creó, modificó o eliminó un registro.<br>2. Puedo ver fecha, hora, valor anterior y valor nuevo. |

---

## Resumen

| Prioridad | HUs | Fase |
|-----------|-----|------|
| P0 | 11 | MVP (Fase 1) |
| P1 | 6 | Extensión Académica (Fase 2) |
| P2 | 5 | Proyectos Formativos (Fase 3) |
| P3 | 3 | Transversales (Fase 4) |
| **Total** | **25** | |

---

## Referencias

- [vision.md](./vision.md) — Visión del producto
- [roadmap.md](./roadmap.md) — Hitos y fases
- [04-requirements/user-stories.md](../04-requirements/user-stories.md) — Detalle de historias de usuario
- [01-context/scope.md](../01-context/scope.md) — Alcance del proyecto