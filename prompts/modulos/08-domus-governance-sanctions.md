# Prompt Maestro — DOMUS Governance & Sanctions

Actúa como responsable de gobernanza, cumplimiento, privacidad, seguridad y
arquitectura del dominio de infracciones.

## Principio

**DOMUS no crea sanciones arbitrarias: ejecuta reglas previamente aprobadas,
publicadas y vigentes, manteniendo evidencia, revisión y trazabilidad.**

## Governance

- Biblioteca de reglamento de copropiedad, reglamento interno, deberes,
  protocolos, normas operativas, privacidad, seguridad y circulares.
- Versionado sin sobrescritura silenciosa.
- Estados `DRAFT`, `APPROVED`, `PUBLISHED`, `ACTIVE`, `ARCHIVED`.
- Vigencia desde/hasta y una única versión activa aplicable por tipo/contexto.
- Confirmación de conocimiento separada de consentimiento.
- Políticas de retención, anonimización, exportación y matriz de acceso por módulo.

## Sanctions

- Una infracción siempre referencia regla y versión normativa vigentes.
- La regla define código, conducta, severidad, sanción y vigencia.
- Registrar incidente, unidad, fecha, descripción, reportante y evidencia.
- Notificar propuesta y permitir descargos dentro de plazo configurable.
- Resolver confirmando, modificando justificadamente o anulando.
- Conservar snapshot de regla y monto; cambios futuros no alteran casos anteriores.
- Permitir apelación cuando la política lo contemple.
- Solo una sanción confirmada puede generar cargo en Finance.

## Estados

`REPORTED → UNDER_REVIEW → NOTIFIED → RESPONSE_PERIOD → RESOLVED`.

Resolución: `CONFIRMED`, `CANCELLED`; posteriores: `APPEALED`, `PAID`.

## Entidades

- `GovernanceDocument`
- `DocumentAcknowledgement`
- `GovernancePolicy`
- `SanctionRule`
- `SanctionCase`
- `SanctionEvidence`
- `SanctionResponse`
- `SanctionResolution`

## Criterios de aceptación

- No puede crearse multa sin regla activa aplicable a la fecha del hecho.
- Editar una regla no modifica casos históricos.
- Confirmar o anular exige autoridad, motivo y evento auditable.
- Residentes no consultan sanciones de otras unidades.
