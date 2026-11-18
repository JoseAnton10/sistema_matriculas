# Arquitectura del Sistema de Matrículas

## 1. Introducción

El Sistema de Matrículas es una aplicación web para gestionar usuarios, cursos, clases y matrículas académicas.

Se utiliza una **arquitectura cliente-servidor organizada en tres capas**, que permite separar la interfaz de usuario, las operaciones del sistema y la persistencia de datos.

## 2. Arquitectura general

El sistema está organizado en tres capas:

**Capa 1: Presentación — React + Vite**

Responsable de mostrar las interfaces y permitir que los usuarios interactúen con el sistema.

Componentes principales:

- `Login.jsx`: inicio de sesión.
- `Panel.jsx`: paneles según el rol del usuario.
- `api.js`: comunicación con la API REST.
- `App.jsx`: configuración de rutas.

**Capa 2: Lógica de negocio — FastAPI**

Responsable de procesar solicitudes HTTP, autenticación, autorización y operaciones académicas.

Componentes principales:

- `main.py`: aplicación FastAPI y configuración de rutas.
- `security.py`: funcionalidades de seguridad y autenticación.
- `schemas/`: esquemas de validación y transferencia de datos.
- `models/`: modelos de datos utilizados por la aplicación.
- `database.py`: configuración de conexión con la base de datos.

**Capa 3: Datos — PostgreSQL en Supabase**

Responsable del almacenamiento persistente de la información.

Entidades principales:

- Usuarios
- Roles
- Categorías
- Cursos
- Clases
- Matrículas

## 3. Comunicación entre capas

El flujo general es:

**Usuario → React → API REST FastAPI → PostgreSQL (Supabase)**

La respuesta regresa por el camino inverso hasta mostrarse en la interfaz.

La comunicación entre React y FastAPI se realiza mediante solicitudes HTTP y respuestas JSON.

## 4. Flujo de autenticación

1. El usuario introduce su correo y contraseña.
2. React envía los datos a `POST /usuarios/login`.
3. FastAPI verifica las credenciales.
4. Si son correctas, el backend devuelve un token JWT y los datos del usuario.
5. El frontend guarda los datos de sesión y redirige al panel correspondiente.
6. Las solicitudes protegidas incluyen el token JWT en la cabecera `Authorization`.
7. El backend valida los permisos del usuario antes de permitir operaciones protegidas.

**Consideración de seguridad:** la protección de rutas del frontend mejora la navegación, pero la autorización efectiva debe realizarse siempre en el backend.

## 5. Flujo de consulta de clases

1. El estudiante inicia sesión.
2. React consulta `GET /clases`.
3. FastAPI procesa la solicitud.
4. Se recuperan las clases disponibles desde PostgreSQL.
5. La API devuelve los resultados en formato JSON.
6. React muestra modalidad, fechas, precio y cupos.

## 6. Organización del código

### Backend

```text
backend/
├── app/
│   ├── models/
│   ├── schemas/
│   ├── database.py
│   ├── main.py
│   └── security.py
└── requirements.txt
```

### Frontend

```text
frontend/
├── public/
├── src/
│   ├── assets/
│   ├── components/
│   ├── pages/
│   │   ├── Login.jsx
│   │   └── Panel.jsx
│   ├── services/
│   │   └── api.js
│   ├── App.jsx
│   ├── index.css
│   └── main.jsx
├── package.json
└── vite.config.js
```

## 7. Justificación de la arquitectura

La arquitectura de tres capas se eligió porque:

- Permite desarrollar el frontend y backend por separado.
- Facilita el mantenimiento y la organización del código.
- Centraliza las validaciones y reglas de negocio en el servidor.
- Permite utilizar la misma API desde diferentes clientes.
- Facilita la incorporación de pruebas automatizadas.

## 8. Comparación con otras arquitecturas

| Arquitectura | Descripción | Aplicación en el proyecto |
|---|---|---|
| Dos capas | Cliente y servidor de datos o servicios | No es la clasificación principal |
| Tres capas | Presentación, lógica de negocio y datos | Arquitectura utilizada |
| MVC | Separa modelo, vista y controlador | Referencia para organizar responsabilidades |
| Microservicios | Servicios independientes y desplegables por separado | No implementada |
| Orientada a mensajes | Comunicación mediante intercambio de mensajes | No implementada |
| Publicación/Suscripción | Comunicación basada en publicación y recepción de eventos | No implementada |

## 9. Limitaciones y mejoras pendientes

- Implementar la funcionalidad de matrícula desde React.
- Completar los paneles administrativos.
- Incorporar pruebas automatizadas.
- Evaluar una separación más detallada de servicios y responsabilidades del backend.
- Revisar el almacenamiento de tokens y las medidas de seguridad del frontend.

## 10. Conclusión

El Sistema de Matrículas utiliza una arquitectura cliente-servidor de tres capas, con React para la presentación, FastAPI para el procesamiento de solicitudes y PostgreSQL en Supabase para el almacenamiento.

Esta organización proporciona una base para continuar el desarrollo, incorporar pruebas y mejorar progresivamente la mantenibilidad del sistema.