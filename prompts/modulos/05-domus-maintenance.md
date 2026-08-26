# Prompt Maestro — DOMUS Maintenance

Actúa como Product Manager, Arquitecto y responsable de operaciones técnicas.

## Objetivo

Centraliza activos, fallas, mantenimiento correctivo/preventivo, técnicos,
proveedores, costos y evidencia del condominio.

## Activos

Lavadoras, secadoras, ascensores, portones, bombas, cámaras, luminarias,
alarmas, citofonía, calderas y cualquier equipo común configurable.

## Requisitos

- Ficha individual con código, tipo, marca, modelo, serie, ubicación y estado.
- Reporte con prioridad, categoría, descripción, evidencia y origen.
- Asignación a proveedor/técnico con acceso limitado a tickets propios.
- Diagnóstico, acciones, repuestos, costos y documentos.
- SLA de reconocimiento, atención y resolución.
- Mantenimiento preventivo recurrente y órdenes generadas por calendario/uso.
- Resolución del técnico y verificación independiente de conserjería/administración.
- Historial técnico inmutable por activo.
- Métricas de recurrencia, indisponibilidad, costo y desempeño de proveedor.

## Estados

`REPORTED → ACKNOWLEDGED → ASSIGNED → IN_PROGRESS → RESOLVED → VERIFIED → CLOSED`.

Alternativos: `CANCELLED`, `BLOCKED`, `REOPENED`.

## Entidades

- `Asset`
- `MaintenanceIncident`
- `WorkOrder`
- `MaintenanceProvider`
- `Technician`
- `MaintenanceEvidence`
- `PartUsage`
- `MaintenancePlan`

## Criterios de aceptación

- Un técnico externo no accede a residentes ni a módulos ajenos.
- Cerrar exige resolución y verificación; reabrir conserva toda la historia.
- Costos y repuestos se agregan mediante movimientos auditables.
- Cada activo muestra su historial completo y próxima mantención.
