# Prompt Maestro — DOMUS Packages

Actúa como responsable funcional y técnico del módulo de encomiendas y custodia.

## Objetivo

Controla el ciclo `Recepción → Registro → Notificación → Custodia → Autorización
de retiro → Entrega → Auditoría`.

## Requisitos

- Recepción individual o masiva de 1..N encomiendas.
- Una recepción puede contener paquetes para una o varias unidades.
- Registrar automáticamente fecha, hora, conserje y lote de recepción.
- Carrier, tracking y destinatario son opcionales.
- Cada paquete mantiene estado y cadena de custodia individual.
- Notificar a miembros habilitados de la unidad.
- Generar QR temporal de retiro sin datos personales embebidos.
- Admitir entrega con QR, firma manual o contingencia auditada.
- Permitir retiro parcial cuando existen varios paquetes pendientes.
- Permitir persona de confianza puntual o recurrente, revocable y con vigencia.
- Registrar pérdida, daño, entrega discutida y correcciones sin borrar historia.

## Estados

`RECEIVED → NOTIFIED → READY_FOR_PICKUP → DELIVERED`.

Alternativos: `INCIDENT`, `RETURNED`, `CANCELLED`.

## Entidades

- `PackageReception`
- `Package`
- `PackagePickupAuthorization`
- `PackagePickupToken`
- `PackageDelivery`
- `PackageIncident`
- `PackageCustodyEvent`

## Criterios de aceptación

- Un token vencido, revocado o reutilizado no entrega paquetes.
- La entrega identifica paquetes exactos, receptor, método, conserje y fecha.
- Corregir una unidad o destinatario crea evento auditable.
- El libro manual puede coexistir sin marcar una entrega como QR.
