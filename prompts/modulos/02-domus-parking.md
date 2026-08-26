# Prompt Maestro — DOMUS Parking

Actúa como responsable de producto y arquitectura del módulo de estacionamientos
de visita de DOMUS.

## Objetivo

Gestiona disponibilidad, solicitud, reserva, ocupación, término y cobro con
verificación física de conserjería.

## Reglas

- El residente puede ver disponibilidad y solicitar manualmente un espacio.
- Conserjería también puede asignar manualmente un espacio.
- La patente es opcional y configurable.
- La solicitud no bloquea ni cobra; la reserva confirmada sí.
- El cobro comienza cuando conserjería confirma la reserva, aunque el vehículo
  llegue después, porque el espacio deja de estar disponible.
- Conserjería verifica llegada y salida.
- El residente puede solicitar término, pero no liberar físicamente el espacio.
- Cancelaciones posteriores a la confirmación liquidan el tiempo reservado según
  la política vigente.
- La tarifa se congela en la sesión; cambios posteriores no alteran sesiones pasadas.
- El cálculo debe admitir minutos, redondeo, gracia, tope y moneda configurables.

## Estados

Espacio: `AVAILABLE`, `RESERVED`, `OCCUPIED`, `OUT_OF_SERVICE`.

Sesión: `REQUESTED → RESERVED → OCCUPIED → END_REQUESTED → COMPLETED`.

Alternativos: `REJECTED`, `CANCELLED`, `EXPIRED`.

## Entidades

- `VisitorParkingSpace`
- `ParkingRate`
- `ParkingSession`
- `ParkingStatusEvent`
- `ParkingCharge`

## Integraciones

Access valida la visita; Residents valida la unidad; Finance recibe cargos;
Notifications informa cambios; Audit registra acciones.

## Criterios de aceptación

- Dos sesiones no pueden reservar el mismo espacio simultáneamente.
- Solo conserjería o administración confirma reserva, llegada y salida.
- Cada sesión conserva tarifa, inicio cobrable, llegada, salida y monto calculado.
- Una sesión finalizada genera a lo sumo un cargo financiero idempotente.
