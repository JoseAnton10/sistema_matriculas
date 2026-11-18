# Estrategia Git Flow — Sistema de Matrículas

## 1. Objetivo

Establecer una metodología de control de versiones para el Sistema de Matrículas mediante Git Flow, garantizando organización, trazabilidad, revisión y calidad de los cambios.

## 2. Modelo de ramas

| Rama | Propósito | Origen | Destino de integración |
|---|---|---|---|
| `main` | Versiones estables | — | — |
| `develop` | Integración de funcionalidades | `main` inicialmente | `main` mediante release |
| `feature/*` | Desarrollo de funcionalidades | `develop` | `develop` |
| `release/*` | Preparación de versiones | `develop` | `main` y `develop` |
| `hotfix/*` | Corrección urgente de versiones publicadas | `main` | `main` y `develop` |

### Reglas generales

- No realizar commits directamente en `main` después de establecer la línea base inicial.
- Evitar commits directos en `develop`; integrar mediante Pull Requests.
- Cada rama `feature/*` debe representar una funcionalidad o cambio concreto.
- Cada cambio debe estar asociado a un Issue.
- Los cambios deben superar las verificaciones definidas antes de integrarse.
- Las ramas `release/*` y `hotfix/*` deben integrarse también en `develop` para mantener sincronizado el desarrollo.

## 3. Convención de nombres de ramas

Se utilizarán nombres descriptivos en minúsculas.

Ejemplos:

- `feature/documentacion-inicial`
- `feature/backend-base`
- `feature/autenticacion`
- `feature/gestion-academica`
- `feature/frontend-login`
- `feature/pruebas-automatizadas`
- `release/v1.0.0`
- `hotfix/correccion-login`

## 4. Convención de commits

Se utilizará una convención basada en Conventional Commits.

Formato:

`tipo(alcance): descripcion`

| Tipo | Uso |
|---|---|
| `feat` | Nueva funcionalidad |
| `fix` | Corrección de errores |
| `docs` | Cambios de documentación |
| `test` | Incorporación o modificación de pruebas |
| `refactor` | Reorganización sin modificar comportamiento |
| `chore` | Configuración y mantenimiento |
| `style` | Cambios de formato sin alterar comportamiento |
| `ci` | Configuración de integración continua |

Ejemplos:

- `feat(auth): incorporar autenticacion JWT`
- `feat(cursos): agregar gestion de cursos`
- `fix(login): corregir validacion de credenciales`
- `docs: documentar arquitectura del sistema`
- `test(api): agregar pruebas de autenticacion`
- `chore(repo): configurar archivos ignorados`

Los mensajes deben describir los cambios realizados, no actividades genéricas como "avance" o "cambios".

## 5. Gestión de Issues

Cada tarea deberá registrarse como Issue en GitHub.

### Información mínima

- Título descriptivo.
- Descripción del problema o funcionalidad.
- Responsable asignado.
- Etiquetas correspondientes.
- Criterios de aceptación.
- Evidencia esperada.

### Estados del tablero

| Estado | Significado |
|---|---|
| Backlog | Tarea identificada y pendiente de priorización |
| To Do | Tarea aprobada y lista para iniciar |
| In Progress | Tarea en desarrollo |
| In Review | Cambio enviado a revisión |
| Done | Tarea integrada y con criterios cumplidos |

### Políticas

- Una tarea no pasa a `In Progress` sin responsable.
- Una tarea no pasa a `In Review` sin Pull Request.
- Una tarea no pasa a `Done` hasta cumplir el Definition of Done.
- Los impedimentos deben registrarse en el Issue correspondiente.

## 6. Flujo de desarrollo

### Paso 1. Crear el Issue

Registrar la funcionalidad y definir criterios de aceptación.

### Paso 2. Crear la rama

Actualizar `develop` y crear una rama específica.

Ejemplo:

```bash
git switch develop
git pull origin develop
git switch -c feature/nueva-funcionalidad
```

El comando `git pull` se utiliza cuando el repositorio remoto ya está configurado.

### Paso 3. Desarrollar

Implementar los cambios correspondientes al Issue.

### Paso 4. Registrar commits

Agregar únicamente los archivos relacionados con el cambio.

Ejemplo:

```bash
git add backend/app/security.py
git commit -m "feat(auth): incorporar funciones de seguridad"
```

Antes del commit, revisar los archivos preparados mediante:

```bash
git diff --cached
```

### Paso 5. Ejecutar pruebas

Verificar que la funcionalidad cumpla sus criterios de aceptación.

Registrar los resultados y las evidencias disponibles.

### Paso 6. Publicar la rama

```bash
git push -u origin feature/nueva-funcionalidad
```

### Paso 7. Crear Pull Request

Crear un Pull Request desde la rama de funcionalidad hacia `develop`.

El PR debe contener:

- Descripción de los cambios.
- Issue relacionado.
- Criterios de aceptación.
- Pruebas ejecutadas.
- Evidencias.
- Riesgos o limitaciones conocidas.

### Paso 8. Revisión humana

Una persona distinta del autor revisará el cambio cuando exista un colaborador disponible.

Si el proyecto se realiza individualmente, se documentará la autoevaluación, pero no se presentará como revisión independiente.

### Paso 9. Integración

Después de aprobar las verificaciones, integrar el PR en `develop`.

### Paso 10. Cierre

Cerrar el Issue cuando se haya comprobado el cumplimiento del Definition of Done.

## 7. Política de Pull Requests

Cada PR debe:

1. Tener un objetivo definido.
2. Estar asociado a un Issue.
3. Contener únicamente cambios relacionados con su objetivo.
4. Presentar resultados de pruebas.
5. Mantener actualizada la documentación afectada.
6. No contener credenciales ni archivos sensibles.
7. Resolver observaciones antes de la integración.

No se deben aprobar cambios que incumplan los criterios de aceptación.

## 8. Definition of Done (DoD)

Una tarea podrá considerarse terminada cuando:

- Se cumplan sus criterios de aceptación.
- Las pruebas correspondientes estén aprobadas.
- Se haya realizado la revisión requerida.
- La documentación esté actualizada.
- Exista trazabilidad entre Issue, rama, commits y Pull Request.
- El código esté integrado en la rama acordada.
- No existan errores bloqueantes conocidos.

Los detalles se especifican en `docs/DEFINITION_OF_DONE.md`.

## 9. Gestión de versiones

Las versiones se identificarán mediante etiquetas como:

- `v1.0.0`
- `v1.0.1`
- `v1.1.0`

Se utilizará una estrategia basada en versionado semántico.

### Release

Una rama `release/*` permitirá preparar una versión estable, ejecutar pruebas y actualizar documentación antes de integrarla en `main`.

### Hotfix

Una rama `hotfix/*` permitirá corregir errores urgentes detectados en una versión publicada.

La corrección deberá integrarse tanto en `main` como en `develop`.

## 10. Línea base

La línea base representa un estado identificado del proyecto que sirve como referencia para controlar cambios posteriores.

La línea base inicial del repositorio corresponde al commit:

`217fe9d` — `chore(repo): configurar archivos ignorados`

Este commit establece únicamente la configuración inicial de Git, no una versión funcional completa.

La línea base del MVP se establecerá posteriormente mediante una versión etiquetada, una vez integrados y verificados sus componentes.

## 11. Incorporación del código existente

El proyecto cuenta con funcionalidades desarrolladas localmente antes de inicializar Git.

Estas funcionalidades se incorporarán progresivamente mediante ramas `feature/*` y commits específicos.

La incorporación por módulos permite organizar la trazabilidad del repositorio, pero no debe presentarse como el historial cronológico original de desarrollo.

## 12. Conclusión

La estrategia Git Flow permite organizar el trabajo del Sistema de Matrículas mediante ramas con responsabilidades definidas, commits descriptivos, revisiones y Pull Requests.

Su aplicación deberá respaldarse con evidencias reales del repositorio, el tablero y las pruebas ejecutadas.