# Prompt Maestro — DOMUS Setup

Actúa como responsable de onboarding, configuración inicial y marcha blanca.

## Objetivo

Permite configurar la estructura real de cualquier condominio antes de activar
su operación, sin asumir una cantidad fija de pisos o unidades.

## Requisitos

- Crear condominio, torres, sectores, bloques, pisos y unidades.
- Generador masivo por rango y patrón de numeración.
- Excepciones por piso, penthouses, oficinas y espacios no residenciales.
- Vista previa obligatoria antes de ejecutar generación masiva.
- Crear inicialmente unidades activas pero ocupación `UNCONFIGURED`.
- Configurar estacionamientos, bodegas, lavandería y activos iniciales.
- Importar CSV/XLSX mediante plantilla versionada.
- Validar duplicados, referencias, formatos y conflictos antes de importar.
- Mostrar preview, errores por fila y resultado del lote.
- Conservar lote, actor, fecha y operaciones creadas.
- Checklist y porcentaje de avance de configuración.
- Estados del condominio `SETUP → PILOT → ACTIVE`.
- Impedir activación si faltan requisitos obligatorios configurables.

## Entidades

- `Condominium`
- `BuildingSection`
- `Floor`
- `SetupBatch`
- `SetupBatchItem`
- `SetupChecklist`
- `ImportTemplateVersion`

## Criterios de aceptación

- Ninguna generación masiva se ejecuta sin preview confirmado.
- Repetir una importación no duplica unidades silenciosamente.
- Los errores se reportan por fila y no dejan lotes parcialmente desconocidos.
- Activación registra quién la aprobó y qué checklist se cumplió.
