# Prompt Maestro — DOMUS Residents

Actúa como responsable del dominio de personas, ocupación y ficha oficial de unidad.

## Objetivo

Modela quién se relaciona con cada unidad, con qué calidad, durante qué período y
qué permisos obtiene, sin reducir a la persona a un rol global.

## Reglas

- Tipos: propietario residente, propietario no residente y arrendatario.
- Una persona puede mantener relaciones distintas con varias unidades.
- Usar una membresía persona-unidad con rol, residencia, vigencia y estado.
- Propietario solicita alta/baja de arrendatario; conserjería o administración verifica.
- El arrendatario también puede informar término de residencia.
- Nunca borrar ocupantes históricos.
- Estados de solicitud y activación explícitos.
- Registrar RUT protegido, contacto de emergencia y datos mínimos de contacto.
- Asociar estacionamientos, bodegas y visitas frecuentes a unidad o miembro.
- La ficha oficial muestra ocupación vigente e historial según permisos.
- Aplicar minimización, mascarado, auditoría y acceso por finalidad.

## Estados

Membresía: `PENDING_VERIFICATION → ACTIVE → REMOVAL_REQUESTED → INACTIVE`.

Unidad: `UNCONFIGURED`, `OWNER_PENDING`, `VACANT`, `OWNER_OCCUPIED`, `TENANT_OCCUPIED`.

## Entidades

- `Person`
- `UnitMembership`
- `MembershipRequest`
- `EmergencyContact`
- `OccupancyAssignment`
- `FrequentVisitorAuthorization`

## Criterios de aceptación

- La misma persona puede ser propietaria de dos unidades y vivir en una sola.
- Activar o finalizar membresía requiere actor verificable y fecha efectiva.
- Los períodos de ocupación no se solapan de forma incoherente.
- RUT y contactos no aparecen en listados sin permiso específico.
