# Auditoría de módulos recuperados

Fecha: 25 de agosto de 2026.

## Resultado

El alcance MVP declarado en el README correspondía al producto anterior a los
nueve prompts recuperados. La primera auditoría identificó las brechas de la
tabla siguiente; todas quedaron cerradas en la implementación posterior.

| Módulo | Backend | Frontend | Brecha principal |
|---|---|---|---|
| Access | Completo | Completo | Cerrada |
| Parking | Completo | Completo | Cerrada |
| Packages | Completo | Completo | Cerrada |
| Laundry | Completo | Completo | Cerrada |
| Maintenance | Completo | Completo | Cerrada |
| Residents | Completo | Completo | Cerrada |
| Setup | Completo | Completo | Cerrada |
| Governance/Sanctions | Completo | Completo | Cerrada |
| Finance | Completo | Completo | Cerrada |

## Evidencia técnica

- Migraciones existentes: auth, visitas, paquetes, residentes, unidades,
  estacionamientos, bodegas, mensajería, notificaciones, auditoría, propiedades y reservas.
- No existían tablas ni paquetes Java para finanzas, sanciones, gobernanza,
  mantenimiento o lavandería.
- Parking modelaba espacios, no sesiones cobrables.
- Packages modelaba un paquete individual, no recepción masiva ni token de retiro.
- Residents mantenía tipo global y una unidad, no relaciones persona-unidad históricas.
- Setup no tenía lotes de preview/commit ni estados de activación.

## Criterio de cierre

Una brecha se considera cerrada cuando dispone de migración, API protegida,
reglas de transición, auditoría, interfaz accesible y pruebas automatizadas.

## Evidencia de cierre

- Migración `V20__create_extended_domus_modules.sql` con entidades, claves,
  estados, permisos e integraciones de los nueve dominios.
- API `/api/v1/operations`, RBAC, aislamiento de acciones de residentes,
  auditoría y notificaciones.
- Centro operativo Angular/Ionic con resumen, recursos y consola validada para
  ejecutar los flujos.
- Prueba de integración transversal que recorre activación, QR, custodia,
  gobierno, sanción, finanzas, mantenimiento y lavandería.
- La matriz de rutas e integraciones está en `docs/API_MODULOS_EXTENDIDOS.md`.
