# Inventario del Sistema de Matrículas

## 1. Objetivo

Identificar y organizar los principales componentes del Sistema de Matrículas para facilitar su documentación, mantenimiento, control de versiones y seguimiento del desarrollo mediante Git Flow.

## 2. Tecnologías utilizadas

| Componente | Tecnología | Función |
|---|---|---|
| Frontend | React + Vite | Interfaz de usuario |
| Backend | Python + FastAPI | API REST |
| Base de datos | PostgreSQL / Supabase | Almacenamiento persistente |
| ORM | SQLAlchemy | Interacción con la base de datos |
| Autenticación | JWT | Autenticación de usuarios |
| Control de versiones | Git | Seguimiento de cambios |
| Repositorio remoto | GitHub (previsto) | Colaboración y Pull Requests |

## 3. Inventario del backend

Directorio principal: `backend/`

| Archivo o directorio | Responsabilidad |
|---|---|
| `app/main.py` | Configuración de FastAPI y puntos de entrada de la API |
| `app/database.py` | Configuración de conexión a PostgreSQL |
| `app/security.py` | Funciones relacionadas con autenticación y seguridad |
| `app/models/usuario.py` | Modelo de usuarios |
| `app/models/curso.py` | Modelo de cursos |
| `app/models/clase.py` | Modelo de clases |
| `app/models/categoria.py` | Modelo de categorías |
| `app/models/matricula.py` | Modelo de matrículas |
| `app/models/__init__.py` | Inicialización del paquete de modelos |
| `app/schemas/` | Esquemas de datos y validaciones |
| `requirements.txt` | Dependencias de Python |
| `app/requirements.txt` | Archivo adicional de dependencias observado; pendiente de revisar |

### Archivos que no deben publicarse

- `.env`: contiene variables de configuración y posibles credenciales.
- `venv/`: entorno virtual local de Python.
- `__pycache__/`: archivos temporales generados por Python.

Estos elementos deben mantenerse excluidos mediante `.gitignore`.

## 4. Inventario del frontend

Directorio principal: `frontend/`

| Archivo o directorio | Responsabilidad |
|---|---|
| `src/App.jsx` | Configuración principal de la aplicación y rutas |
| `src/main.jsx` | Punto de entrada de React |
| `src/pages/Login.jsx` | Formulario de autenticación |
| `src/pages/Panel.jsx` | Panel de usuario según su rol |
| `src/services/api.js` | Comunicación con la API de FastAPI |
| `src/index.css` | Estilos generales |
| `src/App.css` | Estilos de la aplicación |
| `src/components/` | Directorio para componentes reutilizables |
| `src/assets/` | Recursos gráficos y estáticos |
| `public/` | Archivos públicos |
| `package.json` | Dependencias y scripts del proyecto |
| `package-lock.json` | Versiones resueltas de dependencias |
| `vite.config.js` | Configuración de Vite |
| `eslint.config.js` | Configuración de ESLint |
| `index.html` | Documento HTML principal |



### Archivos que no deben publicarse

- `node_modules/`: dependencias instaladas localmente.
- `dist/`: archivos generados durante la compilación.
- Archivos `.env` con datos sensibles.

## 5. Inventario de funcionalidades

| Código | Funcionalidad | Estado conocido |
|---|---|---|
| FUN-01 | Registro de usuarios mediante API | Implementado |
| FUN-02 | Inicio de sesión con JWT | Implementado |
| FUN-03 | Control de acceso por roles | Implementado |
| FUN-04 | Gestión de cursos mediante API | Implementado |
| FUN-05 | Gestión de categorías mediante API | Implementado |
| FUN-06 | Gestión de clases mediante API | Implementado |
| FUN-07 | Gestión de matrículas mediante API | Implementado |
| FUN-08 | Consulta de clases del docente en React | Funcional |
| FUN-09 | Consulta de clases disponibles en React | Funcional |
| FUN-10 | Registro de matrículas desde React | Pendiente |
| FUN-11 | Panel administrativo completo en React | Pendiente |
| FUN-12 | Pruebas automatizadas documentadas | Pendiente de incorporar |

Los estados corresponden al avance observado durante el desarrollo. La revisión formal de pruebas se realizará durante la preparación de la versión.

## 6. Inventario de roles

| Rol | Responsabilidades |
|---|---|
| Estudiante | Consultar clases y gestionar matrículas |
| Docente | Consultar sus clases y estudiantes matriculados |
| Administrador | Gestionar usuarios, cursos, categorías, clases y matrículas |

Algunas funciones ya existen en la API, pero todavía no están conectadas a sus correspondientes interfaces React.

## 7. Plan de incorporación mediante Git Flow

Para registrar ordenadamente el código existente, se utilizarán ramas de funcionalidad:

| Rama | Componentes previstos |
|---|---|
| `feature/documentacion-inicial` | README y documentos técnicos |
| `feature/backend-base` | Configuración FastAPI y conexión a base de datos |
| `feature/modelos-database` | Modelos SQLAlchemy y esquemas |
| `feature/autenticacion` | Autenticación JWT y endpoints de usuarios |
| `feature/gestion-academica` | Cursos, categorías y clases |
| `feature/matriculas` | Endpoints de matrículas |
| `feature/frontend-base` | Configuración React, Vite y servicios generales |
| `feature/frontend-login` | Formulario de inicio de sesión y navegación |
| `feature/paneles` | Paneles según roles |
| `feature/pruebas-automatizadas` | Pruebas automatizadas y evidencias |

La incorporación se realizará respetando las dependencias entre componentes.

Cada rama deberá asociarse a un Issue y contar con commits identificables. La integración en `develop` se realizará mediante Pull Requests.

## 8. Elementos de calidad y trazabilidad

Para cada cambio se buscará conservar:

- Identificador del Issue.
- Responsable.
- Rama de implementación.
- Commits relacionados.
- Criterios de aceptación.
- Resultados de pruebas.
- Documentación actualizada.
- Pull Request de integración.
- Evidencia de revisión humana.

## 9. Observaciones técnicas

1. Se observan dos archivos `requirements.txt` dentro del backend. Se debe verificar cuál contiene las dependencias oficiales.
2. Existe un entorno virtual `venv/` en la raíz del proyecto y otro dentro del backend. Ninguno debe incorporarse a Git.
3. El frontend contiene su propio `.gitignore`, además del archivo `.gitignore` de la raíz.
4. Antes de cada commit se verificará que no se estén incorporando credenciales, dependencias o archivos temporales.
5. Como parte del código ya está desarrollado localmente, su incorporación progresiva al repositorio no representa necesariamente el orden histórico de implementación.

## 10. Conclusión

Este inventario establece una referencia inicial de los componentes, funcionalidades y recursos del Sistema de Matrículas.

Servirá para organizar el trabajo por ramas, mantener la trazabilidad de los cambios y respaldar la presentación del proyecto mediante documentación y evidencias verificables.