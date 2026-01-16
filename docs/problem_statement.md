# Planificación de Aplicación de Gestión de Gastos Compartidos (v2.0)

## 1. Visión General
Plataforma de gestión financiera para usuarios independientes que permite llevar un control de gastos personales y establecer vínculos con otros usuarios para gestionar deudas mutuas y gastos compartidos mediante un sistema de validación bilateral (Handshake).

## 2. Definición del Problema
Actualmente, el seguimiento de quién debe a quién en una relación de convivencia o sociedad suele ser confuso debido a la mezcla de diferentes tipos de flujos monetarios. Se requiere una herramienta que automatice el cálculo del "neto" sin perder el detalle histórico de cada transacción.

## 3. Requerimientos Funcionales

### 3.1. Gestión de Usuarios y Vínculos
* **Cuentas Independientes:** Cada usuario gestiona su propio perfil.
* **Vinculación:** Para compartir gastos, el Usuario A debe solicitar una conexión al Usuario B (vía ID/DNI). Una vez aceptada, se habilita el módulo compartido.

### 3.2. Tipos de Gastos
La aplicación debe clasificar cada entrada en una de las siguientes tres categorías:

1. **Gastos Divisibles (50/50):** El creador registra el gasto; el contraparte debe **aceptar** para que se sume al balance.
2. **Deudas Directas (Pares):** Registro de deuda de A hacia B; requiere **confirmación** del deudor.
3. **Gastos Personales:** Gastos registrados por cada usuario para su propio control financiero, los cuales **no** afectan el balance compartido.

### 3.3. Estados de la Transacción (Handshake)
Para garantizar que ambos estén de acuerdo, cada registro tendrá los siguientes estados:
* **Pendiente:** Registrado por una parte, esperando aprobación. No afecta el neto.
* **Confirmado:** Aceptado por ambas partes. Suma al neto oficial.
* **Liquidación Pendiente:** Una parte marca la deuda como pagada; la otra debe confirmar la recepción del dinero.
* **Saldado:** Transacción finalizada y archivada.

### 3.2. Lógica de Cálculo (Flujo de Caja)
El "Neto" se mostrará en una sección de "Flujo de Caja" y solo tomará en cuenta los gastos en estado **Confirmado**.

### 3.3. Interfaz y Experiencia de Usuario

* **Pestaña de Resumen:** Visualización del estado neto actual.
* **Pestaña de Flujo de Caja:** Historial detallado de deudas divisibles y directas.
* **Pestaña de Gastos Personales:** Sección independiente para el control personal.
* **Sincronización:** Actualización de datos al abrir la aplicación (modelo cliente-servidor).

## 4. Stack Tecnológico Propuesto
* **Backend:** Python con Django + Django REST Framework.
* **Base de Datos:** PostgreSQL.
* **Frontend Móvil:** Python con Flet (basado en Flutter).
* **Arquitectura:** API REST.

## 5. Alcance Inicial (MVP)
* Moneda única: Pesos.
* Sin soporte para imágenes/tickets (versión 1.0).