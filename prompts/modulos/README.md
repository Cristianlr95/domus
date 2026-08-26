# Prompts maestros recuperados de DOMUS

Estos documentos reconstruyen los prompts definidos en la conversación de
ChatGPT **Plan de contenido tecnológico**. Conservan las decisiones funcionales
recuperadas del historial y las convierten en especificaciones versionables del
proyecto.

## Módulos

1. [DOMUS Access](01-domus-access.md)
2. [DOMUS Parking](02-domus-parking.md)
3. [DOMUS Packages](03-domus-packages.md)
4. [DOMUS Laundry](04-domus-laundry.md)
5. [DOMUS Maintenance](05-domus-maintenance.md)
6. [DOMUS Residents](06-domus-residents.md)
7. [DOMUS Setup](07-domus-setup.md)
8. [DOMUS Governance & Sanctions](08-domus-governance-sanctions.md)
9. [DOMUS Finance](09-domus-finance.md)

## Regla común

Cada implementación debe incluir backend, migraciones, permisos, auditoría,
frontend, validaciones y pruebas. Ningún estado sensible puede alterarse sin
trazabilidad y ninguna integración debe acoplar dominios mediante acceso directo
a sus tablas.
