# Prompt Maestro — DOMUS Access

Actúa como Product Manager, Arquitecto de Software, Analista Funcional,
Diseñador UX y Especialista en Seguridad y Privacidad de DOMUS.

## Objetivo

Diseña e implementa un motor de autorización y trazabilidad de accesos para
condominios. No debe ser solamente un libro de visitas digital.

Principio: **autorizar lo necesario, registrar lo comprobable y conservar solo
lo justificable**.

## Actores

- Residente: invita, autoriza, rechaza, revoca y consulta visitas propias.
- Conserje: valida invitaciones, solicita autorización y registra hechos físicos.
- Administración: configura políticas y consulta información autorizada.
- Visitante: utiliza invitación o solicita ingreso sin crear un perfil permanente.

## Requisitos

- Invitación anticipada única, recurrente o por período.
- Autorización en tiempo real cuando la visita llega sin invitación.
- Autorización manual de contingencia registrada por conserjería.
- QR temporal, revocable y de propósito único, sin datos personales embebidos.
- La lectura del QR de una cédula ayuda a completar datos, pero no debe afirmarse
  que constituye validación oficial si no existe un servicio autorizado.
- Identificación mínima y configurable; no almacenar fotografías o documentos
  completos por defecto.
- Separar `entryAt`, `exitAt` y `closedAt`.
- Finalizar visita es opcional para el residente.
- Un cierre automático nunca debe inventar una hora de salida.
- Historial personal configurable y acceso a listados de una unidad sujeto a
  autorización, rol, finalidad y auditoría.
- Retención y anonimización configurables.

## Estados

`DRAFT → PENDING → AUTHORIZED → CHECKED_IN → EXIT_REPORTED → CLOSED`

Estados alternativos: `REJECTED`, `REVOKED`, `EXPIRED`, `AUTO_CLOSED`.

## Entidades mínimas

- `VisitInvitation`
- `VisitAuthorization`
- `VisitSession`
- `VisitorIdentitySnapshot`
- `AccessPolicy`
- `VisitAuditEvent`

## Integraciones

Residents, Parking, Packages, Notifications, Governance y Audit.

## Criterios de aceptación

- No puede registrarse ingreso sin autorización válida o contingencia auditada.
- Un residente solo ve visitas de unidades donde mantiene membresía vigente.
- El conserje ve operación activa y no historiales ilimitados.
- QR vencido, revocado o reutilizado es rechazado.
- Toda transición registra actor, fecha, motivo y origen.
