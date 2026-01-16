# Roadmap de Desarrollo: App de Gastos Compartidos

## Fase 1: Análisis y Definición (MVP)

- [x] **Definir el Problema y Alcance:** Documentar el flujo de caja, tipos de gastos y moneda única.
- [x] **Documentación Inicial:** Crear el archivo `problem_statement.md` para el repositorio.
- [x] **Definir Stack Tecnológico:** Python (Django + Flet) y PostgreSQL.
- [x] **Diseñar Arquitectura de Sistema:** Crear diagrama de bloques (Frontend, API, Backend, DB).

## Fase 2: Diseño Técnico (Blueprint)

- [ ] **Diseñar Diagrama Entidad-Relación (DER):** Definir tablas, campos y relaciones de base de datos <-- Próximo Paso.
    - [ ] Incluir tabla de Vinculaciones y estados de Confirmación.
- [ ] **Definir Lógica de Handshake:** Estados del gasto (Pendiente, Confirmado, Rechazado).
- [ ] **Definir Contrato de la API:** Mapear los endpoints (rutas) y el formato JSON de intercambio de datos.
- [ ] **Diseño de Interfaz (Mockups):** Esbozar las pantallas de Dashboard, Flujo de Caja y Gastos Personales.

## Fase 3: Desarrollo del Backend (Django)

- [ ] **Configuración de Entorno:** Setup de Django, Django REST Framework (DRF) y conexión a base de datos.
- [ ] **Implementar Modelos:** Crear las clases en `models.py` basadas en el DER.
- [ ] **Desarrollar Motor de Validaciones:** Lógica para que B acepte deudas de A.
- [ ] **Desarrollar Lógica de Negocio:** Programar el algoritmo que calcula el saldo neto de deudas (Solo suma gastos "Confirmados").
    - Los cálculos son asíncronos, basados en los estado del *handshake*.
- [ ] **Crear Endpoints (API):** Implementar vistas y serializers para el consumo de datos desde la app.
- [ ] **Seguridad y Autenticación:** Configurar el sistema de Tokens/JWT para el acceso de los usuarios.

## Fase 4: Desarrollo del Frontend (App Móvil)

- [ ] **Estructura Base:** Configurar el proyecto en Flet.
- [ ] **Desarrollo de UI:** Construir los formularios de registro de gastos y las pestañas de visualización.
- [ ] **Módulo de Notificaciones/Pendientes:** Avisar a B que tiene gastos por confirmar.
- [ ] **Gestión de Estado:** Implementar el almacenamiento local y la lógica para actualizar datos al abrir la app.
- [ ] **Integración de API:** Conectar los botones y listas de la app con el backend de Django.

## Fase 5: QA, Pruebas y Despliegue

- [ ] **Pruebas de Consistencia:** Validar que los cálculos de deudas directas y divisibles sean exactos.
- [ ] **Despliegue de Backend:** Subir el servidor Django a servidor local y a futuro en la nube.
- [ ] **Compilación de App:** Generar el ejecutable/binario para su uso en dispositivos móviles.