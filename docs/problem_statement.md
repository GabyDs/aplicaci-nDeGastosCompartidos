# Planificación de Aplicación de Gestión de Gastos Compartidos

## 1. Visión General
El objetivo de esta aplicación es gestionar las finanzas compartidas entre dos usuarios (Persona A y Persona B), permitiendo el registro de deudas mutuas, gastos compartidos y gastos personales, centralizando el cálculo de saldos netos para simplificar la liquidación de cuentas.

## 2. Definición del Problema
Actualmente, el seguimiento de quién debe a quién en una relación de convivencia o sociedad suele ser confuso debido a la mezcla de diferentes tipos de flujos monetarios. Se requiere una herramienta que automatice el cálculo del "neto" sin perder el detalle histórico de cada transacción.

## 3. Requerimientos Funcionales

### 3.1. Tipos de Gastos
La aplicación debe clasificar cada entrada en una de las siguientes tres categorías:
1. **Gastos Divisibles (50/50):** Pagados por un usuario, pero donde el 50% del monto debe ser cubierto por el otro.
2. **Deudas Directas:** Gastos donde un usuario le debe el 100% del monto al otro (ej. préstamos directos o pagos por cuenta del otro).
3. **Gastos Personales:** Gastos registrados por cada usuario para su propio control financiero, los cuales **no** afectan el balance compartido.

### 3.2. Lógica de Cálculo (Flujo de Caja)
* **Detalle por Usuario:** Mostrar una lista de deudas pendientes de A hacia B y viceversa.
* **Cálculo del Neto:** La aplicación debe realizar la compensación de deudas (*netting*) para determinar quién debe pagar a quién al final del periodo.
  * *Fórmula del Neto:*
  $$\text{Saldo}_A = \sum (\text{Divisibles de B} \times 0.5) + \sum (\text{Directos de B a A})$$
  $$\text{Neto} = \text{Saldo}_A - \text{Saldo}_B$$

### 3.3. Interfaz y Experiencia de Usuario
* **Pestaña de Resumen:** Visualización del estado neto actual.
* **Pestaña de Flujo de Caja:** Historial detallado de deudas divisibles y directas.
* **Pestaña de Gastos Particulares:** Sección independiente para el control personal.
* **Sincronización:** Actualización de datos al abrir la aplicación (modelo cliente-servidor).

## 4. Stack Tecnológico Propuesto
* **Backend:** Python con Django + Django REST Framework.
* **Base de Datos:** PostgreSQL (o SQLite para prototipado inicial).
* **Frontend Móvil:** Python con Flet (basado en Flutter) o KivyMD.
* **Arquitectura:** API REST.

## 5. Alcance Inicial (MVP)
* Moneda única: Pesos.
* Sin soporte para imágenes/tickets (versión 1.0).
* Cuenta compartida única para dos usuarios específicos.
