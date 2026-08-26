# Recuperacion de modulos definidos en ChatGPT

Fuente sincronizada: conversacion de ChatGPT **Plan de contenido tecnologico**  
Conversacion: `6a8d467c-3b18-83e9-b6e4-4c87e8d307fb`  
Recuperado en Codex: 25 de agosto de 2026

## Resumen ejecutivo

En la conversacion se definieron nueve modulos formales para DOMUS. ChatGPT
confirmo la generacion de los prompts maestros y mostro referencias de descarga,
pero esos documentos no estaban presentes en el repositorio local al momento de
esta recuperacion.

La columna de código local de la tabla siguiente conserva la fotografía inicial
tomada antes de implementar los prompts. Las brechas fueron cerradas después de
la recuperación; el resultado final está documentado en
`docs/AUDITORIA_MODULOS_2026-08-25.md` y `docs/API_MODULOS_EXTENDIDOS.md`.

| Modulo recuperado | Estado en la conversacion | Estado inicial observado en el codigo local |
|---|---|---|
| DOMUS Access | Prompt maestro generado | Parcial: visitas, estados, UI y API basicas |
| DOMUS Parking | Prompt maestro generado | Parcial: CRUD de estacionamientos; falta sesion/reserva/cobro |
| DOMUS Packages | Prompt maestro generado | Parcial: registro y entrega basicos |
| DOMUS Laundry | Prompt maestro generado | No implementado como modulo propio |
| DOMUS Maintenance | Prompt maestro generado | No implementado como modulo propio |
| DOMUS Residents | Prompt maestro generado | Parcial: residentes y vinculacion basica con unidad |
| DOMUS Setup | Prompt maestro generado | Parcial: unidades, propiedades, bodegas y estacionamientos |
| DOMUS Governance & Sanctions | Prompt maestro redactado en el chat | No implementado |
| DOMUS Finance | Prompt maestro generado | No implementado |

## 1. DOMUS Access — Visitas y Control de Acceso

### Alcance recuperado

- Invitacion previa, autorizacion en tiempo real, visita recurrente y contingencia manual.
- QR temporal para invitaciones.
- Lectura del QR de la cedula como ayuda de registro, sin confundir lectura con
  validacion oficial de identidad.
- Registro separado de ingreso, salida fisica y cierre administrativo.
- Finalizacion manual opcional para el residente.
- Historial visible bajo reglas de privacidad y autorizacion del residente.
- Retencion limitada, auditoria y acceso restringido para conserjeria.

### Brecha local

Existe el modulo `visits` en backend y frontend. No se identificaron invitaciones
QR, autorizaciones recurrentes, politicas de retencion ni la separacion completa
entre `entryAt`, `exitAt` y `closedAt` propuesta en el prompt.

## 2. DOMUS Parking — Estacionamientos de Visita

### Alcance recuperado

- Disponibilidad visible para residentes y conserjeria.
- Solicitud del residente o asignacion manual por conserjeria.
- Patente opcional.
- Cobro desde la confirmacion de la reserva, aunque la visita llegue despues.
- Verificacion fisica de llegada y salida por conserjeria.
- Solicitud de termino por residente; liberacion final por conserjeria.
- Tarifa congelada por sesion y calculo de tiempo/monto total.
- Estados: `REQUESTED`, `RESERVED`, `OCCUPIED`, `END_REQUESTED`, `COMPLETED`,
  ademas de cancelacion, expiracion y fuera de servicio.
- Integracion con Access y Finance.

### Brecha local

Existe CRUD de espacios de estacionamiento. No se identificaron entidades de
reserva/sesion, tarifario historico, medicion de tiempo ni liquidacion de cobro.

## 3. DOMUS Packages — Encomiendas y Custodia

### Alcance recuperado

- Recepcion individual y masiva para uno o varios departamentos.
- Fecha, hora y conserje registrados automaticamente.
- Notificacion al residente.
- QR temporal de retiro sin datos personales embebidos.
- Compatibilidad con libro y firma manual.
- Retiro parcial de varias encomiendas.
- Retiro por persona de confianza, puntual o recurrente.
- Cadena de custodia, incidentes, correcciones auditables e historial completo.
- Integracion con Access, Residents y Notifications.

### Brecha local

Existe registro, consulta y entrega basica de paquetes. No se identificaron
recepcion masiva, QR de retiro, firma manual, autorizaciones de terceros ni flujo
formal de incidentes/cadena de custodia.

## 4. DOMUS Laundry — Lavanderia y Equipamiento

### Alcance recuperado

- Solicitud, autorizacion, reserva, uso real, termino y liberacion.
- Modo de fichas fisicas, solo autorizacion o modalidad mixta por maquina.
- Lavadoras y secadoras modeladas individualmente.
- Ventanas configurables antes y despues del uso; referencia inicial de 20 minutos.
- Limites de uso por residente, configurables y anulables con trazabilidad.
- Registro de inicio, duracion y finalizacion real.
- Estados de disponibilidad, reserva, uso, buffer y fuera de servicio.
- Reporte de fallas con aviso inmediato a conserjeria y tecnico externo.
- Integracion con Maintenance, Residents y Notifications.

### Brecha local

No se identifico un modulo Laundry. El modulo generico de reservas de espacios
comunes no cubre maquinas, fichas, buffers operacionales ni fallas tecnicas.

## 5. DOMUS Maintenance — Mantenimiento e Incidentes Tecnicos

### Alcance recuperado

- Inventario de activos: lavanderia, ascensores, portones, bombas, camaras,
  luminarias, alarmas, citofonia y otros equipos comunes.
- Incidentes correctivos y planes preventivos.
- Asignacion a proveedores o tecnicos externos con acceso limitado.
- Prioridad, SLA, diagnostico, evidencia, repuestos, costos y verificacion de cierre.
- Historial tecnico por activo y analisis de recurrencias.
- Estados desde reporte hasta cierre verificado.
- Integracion transversal con Laundry, Access, Parking y Packages.

### Brecha local

No se identificaron entidades, migraciones, API ni pantallas especificas de
mantenimiento o activos tecnicos.

## 6. DOMUS Residents — Residentes y Ficha de Unidad

### Alcance recuperado

- Propietario residente, propietario no residente y arrendatario.
- Relacion persona-unidad mediante membresia, evitando un rol global rigido.
- Una persona puede relacionarse con varias unidades de distinta forma.
- Alta y baja de arrendatarios solicitada por propietario y verificada en conserjeria.
- Estados pendientes, activos e inactivos sin borrar el historial.
- RUT, contacto de emergencia, estacionamientos, bodegas y visitas frecuentes.
- Ficha oficial de unidad e historial de ocupacion.
- Permisos diferenciados, privacidad y auditoria.

### Brecha local

Existe CRUD de residentes y vinculacion basica con unidades. Falta comprobar o
implementar el modelo completo de membresias historicas, solicitudes verificadas,
propietario no residente, asignaciones por ocupante y trazabilidad de ocupacion.

## 7. DOMUS Setup — Configuracion Inicial y Marcha Blanca

### Alcance recuperado

- Creacion de condominios, torres, sectores, bloques y pisos variables.
- Generacion masiva de departamentos con excepciones por piso.
- Vista previa obligatoria antes de crear lotes.
- Estados de ocupacion inicial: sin configurar, propietario pendiente, vacante,
  propietario residente y arrendatario residente.
- Configuracion de estacionamientos, bodegas, lavanderia y activos iniciales.
- Importacion CSV/XLSX con validacion, errores y preview.
- Checklist de implementacion y estados `SETUP`, `PILOT`, `ACTIVE`.
- Auditoria de lotes y posibilidad de revertir/corregir antes de activacion.

### Brecha local

Existen unidades, propiedades, estacionamientos y bodegas. No se identifico un
asistente de marcha blanca, generacion masiva con preview, importacion CSV/XLSX ni
maquina de estados de activacion del condominio.

## 8. DOMUS Governance & Sanctions — Gobierno, Normativa y Multas

### Alcance recuperado

- Biblioteca descargable de reglamentos, deberes, protocolos y politicas.
- Versionado documental sin sobrescritura silenciosa.
- Vigencia, publicacion, archivo y confirmacion de conocimiento.
- Separacion entre conocimiento del documento y consentimiento de datos.
- Politicas de privacidad, seguridad, retencion y matriz de acceso por modulo.
- Toda sancion debe referenciar una regla previamente aprobada y vigente.
- Evidencias, notificacion, periodo de descargos, resolucion, multa y apelacion.
- Snapshot de la regla y del monto aplicable al momento de la infraccion.
- Integracion con Parking, Laundry, Access y Finance.

### Brecha local

No se identificaron modulos de governance, documentos normativos, reglas,
infracciones, descargos o sanciones. La auditoria generica existente sirve como
base transversal, pero no reemplaza este dominio.

## 9. DOMUS Finance — Gastos Comunes y Obligaciones Economicas

### Alcance recuperado

- Ciclo completo: calculo, emision, notificacion, pago, conciliacion, morosidad y auditoria.
- Periodos mensuales y estados `DRAFT`, `REVIEW`, `PUBLISHED`, `CLOSED`.
- Prorrateo por coeficiente, sector, reglamento y gasto especifico.
- Gastos ordinarios, extraordinarios, fondo de reserva, multas, intereses y otros cargos.
- Distincion entre responsable legal y pagador autorizado.
- Aviso de cobro y comprobante descargables.
- Pagos externos, pagos online futuros, abonos y conciliacion.
- Morosidad, intereses parametrizados y convenios de pago preparados para evolucion futura.
- Integracion automatica con Parking y Sanctions.
- Estados de cuenta, transparencia financiera, reportes e indicadores.
- Auditoria reforzada y ajustes trazables despues del cierre mensual.

### Brecha local

No se identificaron migraciones, entidades, API ni pantallas del dominio financiero.

## Orden sugerido para incorporacion

1. Consolidar Residents y Setup, porque definen unidades, ocupantes y configuracion base.
2. Completar Access, Parking y Packages sobre los modulos ya existentes.
3. Implementar Governance & Sanctions antes de emitir multas reales.
4. Implementar Finance despues de estabilizar coeficientes, unidades y sanciones.
5. Implementar Maintenance y luego Laundry, reutilizando activos e incidentes tecnicos.

## Nota sobre los documentos originales

La conversacion conserva referencias internas de descarga de los prompts maestros.
El contenido de varias referencias no estaba disponible como archivo local ni como
adjunto recuperable mediante la lectura de historial. Este documento preserva el
inventario, las decisiones funcionales y el estado real observado; no pretende
hacerse pasar por una copia byte a byte de aquellos adjuntos.
