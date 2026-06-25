# Requisitos no funcionales

> Estado: 🟢 Estable | Última actualización: 2026-06-24
> Autor: Equipo ADSO 3145555 | Equipo: Arquitectura

## Contexto

Este documento define los requisitos no funcionales del sistema **Horarios SENA**. Cubren atributos de calidad, seguridad, rendimiento, disponibilidad y operación que el sistema debe cumplir independientemente de la funcionalidad.

## Convención de identificadores

| Prefijo | Significado |
|---------|-------------|
| RNF-XXX | Requisito No Funcional |
| **A** | Prioridad Alta |
| **M** | Prioridad Media |
| **B** | Prioridad Baja |

## Resumen por categoría

| Categoría | Total | Alta | Media |
|-----------|-------|------|-------|
| Arquitectura y calidad del código | 4 | 3 | 1 |
| Seguridad | 10 | 10 | 0 |
| Rendimiento y escalabilidad | 4 | 2 | 2 |
| Base de datos | 5 | 4 | 1 |
| Disponibilidad y recuperación | 3 | 1 | 2 |
| Usabilidad y experiencia de usuario | 4 | 3 | 1 |
| Mantenibilidad | 3 | 2 | 1 |
| Pruebas | 5 | 5 | 0 |
| Despliegue y operación | 4 | 3 | 1 |
| **Total** | **42** | **33** | **9** |

---

## Arquitectura y calidad del código

| ID | Requisito | Prioridad | Verificación |
|----|-----------|-----------|--------------|
| RNF-001 | El sistema debe seguir una arquitectura limpia (Clean Architecture) con separación de capas: `domain`, `application`, `infrastructure` y `transport`. | A | Revisión de código y estructura de carpetas. |
| RNF-002 | El sistema debe estar dividido en microservicios independientes, cada uno con su propia base de datos. | A | Revisión de la arquitectura de microservicios. |
| RNF-003 | El código debe cumplir los estándares definidos en `coding-standards.md` (Java 21 + Spring Boot). | A | Revisiones de código automáticas y manuales. |
| RNF-004 | Ningún archivo fuente debe superar las 300 líneas, excepto archivos generados automáticamente. | M | Análisis estático con SonarQube. |

---

## Seguridad

| ID | Requisito | Prioridad | Verificación |
|----|-----------|-----------|--------------|
| RNF-005 | Todas las comunicaciones entre frontend y backend deben usar HTTPS. | A | Verificación de configuración TLS/SSL. |
| RNF-006 | El sistema debe usar JWT para autenticación y autorización. | A | Pruebas de autenticación. |
| RNF-007 | Los roles y permisos deben estar definidos y validados en cada endpoint. | A | Pruebas de autorización por rol. |
| RNF-008 | Las contraseñas deben almacenarse con BCrypt. | A | Revisión de implementación de hash. |
| RNF-009 | Los campos de PII (nombre, email, documento) deben estar cifrados en reposo mediante PostgreSQL pgcrypto o a nivel de aplicación. | A | Verificación de cifrado en base de datos. |
| RNF-010 | Los errores internos del servidor no deben exponer stack traces al cliente. | A | Pruebas de respuesta en errores 500. |
| RNF-011 | Todas las acciones críticas (crear, modificar, eliminar) deben registrarse en la tabla `audit_log`. | A | Verificación de logs de auditoría. |
| RNF-012 | El sistema debe prevenir inyección SQL usando JPA/Hibernate con parámetros bind. | A | Revisión de código y pruebas de seguridad. |
| RNF-013 | El CORS debe configurarse de forma restrictiva, permitiendo solo orígenes autorizados. | A | Verificación de configuración de CORS. |
| RNF-014 | Los tokens JWT deben expirar después de 8 horas. | A | Pruebas de expiración de tokens. |

---

## Rendimiento y escalabilidad

| ID | Requisito | Prioridad | Verificación |
|----|-----------|-----------|--------------|
| RNF-015 | El tiempo de respuesta de las APIs debe ser inferior a 2 segundos bajo carga normal. | A | Pruebas de carga con JMeter. |
| RNF-016 | La validación de conflictos de horario debe ejecutarse en menos de 500 ms. | A | Pruebas de rendimiento del motor de horarios. |
| RNF-017 | El sistema debe soportar al menos 1.000 usuarios concurrentes en operación normal. | M | Pruebas de escalabilidad. |
| RNF-018 | El sistema debe diseñarse para escalar horizontalmente con múltiples instancias de microservicios. | M | Revisión de arquitectura y configuración. |

---

## Base de datos

| ID | Requisito | Prioridad | Verificación |
|----|-----------|-----------|--------------|
| RNF-019 | El sistema debe usar PostgreSQL 16 o superior. | A | Verificación de versión en los entornos de desarrollo y producción. |
| RNF-020 | Cada microservicio debe tener su propio esquema de base de datos. | A | Verificación de separación de datos. |
| RNF-021 | Deben crearse los índices necesarios para las consultas más frecuentes, como `schedule.instructor_id` y `schedule.start_time`. | A | Revisión de scripts de migración en Flyway. |
| RNF-022 | Las migraciones de base de datos deben gestionarse con Flyway y ser idempotentes. | A | Verificación de ejecución de migraciones. |
| RNF-023 | Se deben realizar backups diarios de la base de datos (RPO: 24 horas). | M | Verificación de política de backups. |

---

## Disponibilidad y recuperación

| ID | Requisito | Prioridad | Verificación |
|----|-----------|-----------|--------------|
| RNF-024 | El sistema debe exponer un endpoint de healthcheck en `/actuator/health` que verifique la conexión a la base de datos y otros servicios dependientes. | A | Pruebas de healthcheck en Docker Compose. |
| RNF-025 | El tiempo máximo de inactividad planificada (RTO) debe ser inferior a 4 horas. | M | Plan de recuperación documentado. |
| RNF-026 | El sistema debe poder restaurarse desde el último backup disponible (RPO: 24 horas). | M | Pruebas de restauración. |

---

## Usabilidad y experiencia de usuario

| ID | Requisito | Prioridad | Verificación |
|----|-----------|-----------|--------------|
| RNF-027 | La interfaz de usuario debe estar en español. | A | Revisión de textos y etiquetas en el frontend. |
| RNF-028 | La interfaz debe ser responsiva y funcionar correctamente en dispositivos móviles, tablets y escritorio. | A | Pruebas en diferentes tamaños de pantalla. |
| RNF-029 | Los mensajes de error deben ser claros y comprensibles para el usuario, sin exponer información técnica. | A | Pruebas de validación de formularios. |
| RNF-030 | La aplicación debe cargarse en menos de 3 segundos bajo condiciones normales. | M | Pruebas de rendimiento del frontend. |

---

## Mantenibilidad

| ID | Requisito | Prioridad | Verificación |
|----|-----------|-----------|--------------|
| RNF-031 | La API debe estar documentada con OpenAPI (Swagger) usando SpringDoc y ser accesible en `/swagger-ui.html`. | A | Verificación de acceso al endpoint. |
| RNF-032 | Los comentarios en el código deben estar escritos en inglés cuando sean necesarios. | M | Revisión de código. |
| RNF-033 | El repositorio de documentación debe mantenerse actualizado según la estructura definida en `CONTRIBUTING.md`. | A | Revisión de PRs. |

---

## Pruebas

| ID | Requisito | Prioridad | Verificación |
|----|-----------|-----------|--------------|
| RNF-034 | El sistema debe incluir pruebas unitarias para la capa de dominio y de servicios (JUnit 5 + Mockito). | A | Ejecución de `mvn test`. |
| RNF-035 | El sistema debe incluir pruebas de integración con Testcontainers para la capa de repositorios. | A | Ejecución de pruebas de integración. |
| RNF-036 | La cobertura de código debe ser al menos del 80% en las capas de servicio y dominio, medida con JaCoCo. | A | Verificación de informes de JaCoCo. |
| RNF-037 | Se deben ejecutar pruebas de aceptación para los flujos críticos, como la creación de un horario con conflicto. | A | Pruebas automáticas y manuales. |
| RNF-038 | El sistema debe superar las pruebas de seguridad OWASP Top 10 antes de cada despliegue. | A | Reporte de AppSec. |

---

## Despliegue y operación

| ID | Requisito | Prioridad | Verificación |
|----|-----------|-----------|--------------|
| RNF-039 | El sistema debe desplegarse usando Docker Compose con al menos tres servicios: backend, frontend y base de datos. | A | Ejecución de `docker compose up`. |
| RNF-040 | Las variables de entorno deben configurarse en un archivo `.env`, con un archivo `.env.example` como referencia. | A | Verificación de archivos de configuración. |
| RNF-041 | El sistema debe generar logs estructurados con SLF4J + Logback, usando los niveles DEBUG, INFO, WARN y ERROR. | A | Verificación de logs en entorno de desarrollo. |
| RNF-042 | El sistema debe incluir un plan de despliegue y rollback documentado en `deployment-plan.md` y `rollback-plan.md`. | M | Revisión de los documentos referenciados. |

---

## Referencias

- [functional.md](./functional.md) — Requisitos funcionales
- [user-stories.md](./user-stories.md) — Historias de usuario
- [traceability-matrix.md](./traceability-matrix.md) — Matriz de trazabilidad
- [05-architecture/](../05-architecture/) — Arquitectura del sistema
- [10-devops/](../10-devops/) — Despliegue y operación