# Prompt Maestro — DOMUS Laundry

Actúa como responsable de producto, operaciones y arquitectura del módulo de
lavandería y equipamiento.

## Objetivo

Gestiona solicitud, autorización, preparación, uso real, término, liberación y
mantenimiento de lavadoras y secadoras.

## Requisitos

- Modos por máquina: ficha física, solo autorización o mixto.
- Cada lavadora/secadora es un recurso individual con código y estado.
- Ventanas configurables antes y después del uso; valor inicial sugerido: 20 minutos.
- La reserva y el uso real son eventos diferentes.
- Registrar fichas entregadas, inicio real, fin real y duración.
- Límites configurables por residente, día, semana o período.
- La anulación de un límite requiere permiso y motivo auditado.
- El residente solicita; conserjería autoriza e inicia o confirma operación.
- Reportar fallas y notificar inmediatamente a conserjería y proveedor asignado.
- Un equipo fuera de servicio no acepta nuevas reservas.

## Estados

Máquina: `AVAILABLE`, `RESERVED`, `IN_USE`, `BUFFER`, `OUT_OF_SERVICE`, `MAINTENANCE`.

Uso: `REQUESTED → AUTHORIZED → READY → IN_USE → FINISHED → RELEASED`.

Alternativos: `REJECTED`, `CANCELLED`, `FAILED`.

## Entidades

- `LaundryMachine`
- `LaundryPolicy`
- `LaundryBooking`
- `LaundryUsage`
- `LaundryTokenTransaction`
- `LaundryLimitOverride`

## Integraciones

Residents, Maintenance, Notifications, Finance opcional y Audit.

## Criterios de aceptación

- No existen reservas solapadas considerando buffers.
- Un fallo bloquea la máquina y crea incidente técnico idempotente.
- Duración programada y duración real se conservan por separado.
- Toda excepción de límite identifica actor y motivo.
