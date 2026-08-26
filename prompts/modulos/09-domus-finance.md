# Prompt Maestro — DOMUS Finance

Actúa como Product Manager, Arquitecto Financiero, Analista Funcional y
Especialista en auditoría de condominios.

## Principio

**Cada peso cobrado a una unidad debe explicar de dónde viene, por qué se cobra,
cuándo se generó y cómo fue pagado.**

## Objetivo

Gestiona `Cálculo → Emisión → Notificación → Pago → Conciliación → Morosidad →
Auditoría` para gastos comunes y demás obligaciones económicas.

## Requisitos

- Períodos mensuales con `DRAFT`, `REVIEW`, `PUBLISHED`, `CLOSED`.
- Gastos ordinarios, extraordinarios, fondo de reserva y cargos específicos.
- Prorrateo por coeficiente, sector, reglamento y regla del gasto.
- Estado de cuenta por unidad con saldo anterior, cargos, pagos y saldo final.
- Distinguir responsable legal de pagador autorizado.
- Integrar multas confirmadas y sesiones de parking liquidadas.
- Aviso de cobro y comprobante descargables.
- Pago externo inicialmente y proveedor online desacoplado para evolución.
- Pagos parciales: `amountDue`, `amountPaid`, `balance`; nunca solo `paid=true`.
- Conciliación `PENDING`, `REPORTED`, `MATCHED`, `CONFIRMED`, `REJECTED`.
- Morosidad e intereses parametrizados, sin porcentajes fijos en código.
- Convenios de pago preparados como dominio independiente.
- Fondo de reserva separado de caja operacional.
- Ajustes y notas posteriores al cierre; no editar silenciosamente períodos cerrados.
- Dashboard de emisión, recaudación, deuda, morosidad y fondo de reserva.

## Entidades

- `ExpensePeriod`
- `CondominiumExpense`
- `UnitStatement`
- `FinanceCharge`
- `Payment`
- `PaymentAllocation`
- `Reconciliation`
- `ReserveFundMovement`
- `PaymentAgreement`
- `FinancialAdjustment`

## Criterios de aceptación

- La suma de asignaciones de pago no supera el pago ni el saldo de cargos.
- Publicar congela coeficientes y reglas usadas en cada estado de cuenta.
- Cerrar impide edición directa y obliga a ajustes auditables.
- Integraciones de Parking/Sanctions son idempotentes.
- Todo cambio financiero registra valor anterior, nuevo, actor y motivo.
