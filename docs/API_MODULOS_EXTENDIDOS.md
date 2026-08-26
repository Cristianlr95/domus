# API de módulos extendidos

Base: `/api/v1/operations`. Todas las rutas requieren JWT y permisos RBAC.
Las mutaciones registran auditoría. Los listados aceptan `limit` (1–500) y
`offset`.

| Dominio | Operaciones principales |
|---|---|
| Residents | crear membresía y verificar su estado |
| Setup | crear condominio, completar checklist, preview y commit idempotente |
| Access | crear invitación, validar QR y registrar entrada/salida/cierre |
| Parking | crear tarifa, sesión y transiciones con liquidación automática |
| Packages | recepción masiva, autorización tokenizada, entrega y custodia |
| Governance | documento versionado, publicación y acuse de recibo |
| Sanctions | reglas, casos, descargos, resolución y cargo financiero |
| Finance | períodos, cargos, pagos, imputaciones, ajustes, fondo y convenios |
| Maintenance | activos, planes, incidentes, atención y verificación |
| Laundry | máquinas, límites, buffers, usos y escalamiento de fallas |

La especificación exacta y ejecutable está disponible mediante OpenAPI en
`/swagger-ui.html` al iniciar el backend. El frontend expone las operaciones en
`/operations` para los roles autorizados.

## Integraciones críticas

- El token de una invitación se almacena únicamente como SHA-256 y se verifica
  en `POST /access/token/events` respetando vigencia y estado.
- Parking aplica minutos de gracia, bloque de redondeo y tarifa congelada al
  confirmar la sesión.
- Parking y sanciones generan cargos idempotentes. Si no existe un período
  financiero editable, el cargo queda pendiente y se procesa al crear el
  siguiente período.
- La recepción de paquetes notifica al residente y los incidentes notifican a
  administración/conserjería.
- Una falla de lavandería crea un incidente sobre el activo asociado.

