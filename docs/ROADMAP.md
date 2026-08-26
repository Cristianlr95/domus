# Roadmap de producto y desarrollo

El alcance MVP anterior está implementado, pero el alcance ampliado recuperado
de ChatGPT incorpora nueve módulos y requiere el siguiente orden de trabajo.

## Fase 1 — Fundaciones

- [x] Membresías históricas de residentes y ocupación por unidad.
- [x] Condominio, sectores y estados de marcha blanca.
- [x] Lotes de configuración con preview y commit idempotente.
- [x] Permisos y auditoría para los nuevos dominios.

## Fase 2 — Operación existente

- [x] Access: invitaciones, autorizaciones y eventos de entrada/salida/cierre.
- [x] Parking: sesiones, tarifas congeladas, ocupación y liquidación.
- [x] Packages: recepción masiva, tokens, autorizaciones y custodia.

## Fase 3 — Gobierno y finanzas

- [x] Governance: documentos versionados, publicación y conocimiento.
- [x] Sanctions: reglas vigentes, expedientes, descargos y resolución.
- [x] Finance: períodos, estados de cuenta, cargos, pagos y conciliación.

## Fase 4 — Activos y lavandería

- [x] Maintenance: activos, incidentes, asignación y verificación.
- [x] Laundry: máquinas, buffers, usos, fichas y reporte de fallas.

## Fase 5 — Cierre productivo

- [x] Pruebas unitarias e integración de todos los flujos.
- [x] Pruebas frontend y E2E de caminos críticos.
- [x] Paginación de listados de alto volumen.

## Mejoras productivas fuera del alcance recuperado

- Recuperación de contraseña mediante proveedor de correo.
- Cookies `HttpOnly` para refresh tokens web.
- Observabilidad, alertas y ambientes `staging`/`production`.
- Mapas y push si se confirma alcance móvil.

Ninguna casilla debe marcarse únicamente porque exista una tabla: el criterio de
cierre exige API, reglas, permisos, auditoría, interfaz y pruebas.
