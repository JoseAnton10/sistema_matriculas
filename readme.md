
# Sistema de Matrículas

Sistema web para la gestión de cursos, clases y matrículas académicas, desarrollado con React, FastAPI y PostgreSQL.

## 1. Descripción

El Sistema de Matrículas permite administrar cursos y clases en modalidades virtual, presencial o mixta, mediante una plataforma web con autenticación y control de acceso basado en roles.

El sistema contempla tres tipos de usuarios:

- **Estudiante:** consulta clases disponibles y gestiona sus matrículas.
- **Docente:** consulta sus clases asignadas y estudiantes matriculados.
- **Administrador:** administra usuarios, cursos, categorías, clases y matrículas.

## 2. Objetivo general

Desarrollar un sistema web que facilite la administración y gestión de matrículas académicas mediante tecnologías modernas, una arquitectura de tres capas y buenas prácticas de ingeniería de software.

## 3. Tecnologías utilizadas

### Backend
- Python
- FastAPI
- SQLAlchemy
- PostgreSQL
- Supabase
- JWT para autenticación
- Uvicorn

### Frontend
- React
- JavaScript
- Vite
- React Router
- HTML y CSS

### Control de versiones
- Git
- GitHub
- Git Flow

## 4. Arquitectura del sistema

Se utiliza una arquitectura cliente-servidor organizada en tres capas:

1. **Presentación:** React gestiona las interfaces de usuario.
2. **Lógica de negocio:** FastAPI procesa las solicitudes, validaciones y autorización.
3. **Datos:** PostgreSQL en Supabase almacena la información del sistema.

Flujo general:

React → API REST FastAPI → PostgreSQL (Supabase)

## 5. Estructura del proyecto

```text
sistema_matriculas/
├── backend/
│   ├── app/
│   │   ├── models/
│   │   ├── schemas/
│   │   ├── database.py
│   │   ├── main.py
│   │   └── security.py
│   └── requirements.txt
├── frontend/
│   ├── public/
│   ├── src/
│   │   ├── assets/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── App.jsx
│   │   └── main.jsx
│   └── package.json
├── docs/
├── .gitignore
└── README.md
```

## 6. Funcionalidades del proyecto

### Backend

- Registro e inicio de sesión de usuarios.
- Autenticación mediante JWT.
- Control de acceso por roles.
- Gestión de cursos y categorías.
- Gestión de clases.
- Registro y consulta de matrículas.
- Consulta de clases asignadas a docentes.
- Administración de usuarios y matrículas.
- Estadísticas administrativas.

### Frontend

- Formulario de inicio de sesión.
- Redirección según el rol.
- Panel de estudiante con clases disponibles.
- Panel de docente con clases asignadas.
- Protección de rutas según el rol.
- Cierre de sesión.

### Funcionalidades pendientes en el frontend

- Conectar el botón de matrícula con la API.
- Visualizar y gestionar las matrículas del estudiante.
- Implementar las herramientas administrativas.

## 7. Instalación y ejecución

### Requisitos

- Python y pip
- Node.js y npm
- Git
- Acceso a una base de datos PostgreSQL

### Backend

Ingresar a la carpeta:

```bash
cd backend
```

Crear un entorno virtual:

```bash
python -m venv venv
```

Activarlo en Git Bash para Windows:

```bash
source venv/Scripts/activate
```

Instalar las dependencias:

```bash
pip install -r requirements.txt
```

Crear el archivo local `backend/.env` con las variables requeridas:

```env
DATABASE_URL=TU_URL_DE_CONEXION
JWT_SECRET=TU_CLAVE_SECRETA
```

Iniciar el servidor:

```bash
python -m uvicorn app.main:app --reload
```

API local:

http://127.0.0.1:8000

Documentación Swagger:

http://127.0.0.1:8000/docs

### Frontend

Desde otra terminal, ingresar a la carpeta:

```bash
cd frontend
```

Instalar dependencias:

```bash
npm install
```

Iniciar la aplicación:

```bash
npm run dev
```

Abrir:

http://localhost:5173

## 8. Estrategia Git Flow

El desarrollo utiliza las siguientes ramas:

| Rama | Propósito |
|---|---|
| main | Versiones estables |
| develop | Integración de funcionalidades |
| feature/* | Desarrollo de funcionalidades |
| release/* | Preparación de versiones |
| hotfix/* | Correcciones urgentes |

Los cambios de funcionalidades se integrarán a `develop` mediante Pull Requests.

### Convención de commits

Se utiliza una convención basada en Conventional Commits.

Ejemplos:

- `feat(auth): implementar autenticacion JWT`
- `fix(api): corregir validacion de usuarios`
- `docs: actualizar documentacion`
- `test(api): agregar pruebas de autenticacion`
- `refactor(models): reorganizar modelos`
- `chore(repo): configurar archivos ignorados`

## 9. Pruebas y calidad

Se incorporarán pruebas automatizadas del backend y frontend.

Los cambios deberán cumplir criterios de aceptación, superar las pruebas correspondientes, contar con documentación actualizada y pasar por revisión antes de su integración.

## 10. Seguridad

- Autenticación mediante tokens JWT.
- Restricción de endpoints según el rol del usuario.
- Variables sensibles almacenadas en archivos `.env` locales.
- Exclusión de credenciales y dependencias mediante `.gitignore`.

Nunca deben publicarse contraseñas, claves privadas ni tokens reales en el repositorio.

## 11. Estado del proyecto

**Estado:** MVP en desarrollo.

La autenticación y los paneles básicos de estudiante y docente funcionan. El backend dispone de operaciones académicas y administrativas que se están integrando progresivamente al frontend.

La versión oficial se establecerá después de completar las pruebas, documentación y revisión de la rama de lanzamiento.


## 12. Gestión del proyecto con Jira

El seguimiento de tareas se realiza mediante Jira.

- **Proyecto:** CAP
- **Plataforma:** Atlassian Jira
- **Tablero:** https://unsaac-team-jiwwnou7.atlassian.net/jira/software/projects/CAP/summary

Las tareas se relacionarán con las ramas Git Flow, los commits y los Pull Requests de GitHub.

Los criterios de aceptación y el Definition of Done se utilizarán para verificar la finalización de cada tarea.
