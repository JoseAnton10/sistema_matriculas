# Definition of Done (DoD)
## Sistema de Matrículas

### 1. Objetivo

Establecer criterios verificables de calidad para determinar cuándo una tarea, funcionalidad o corrección del Sistema de Matrículas puede considerarse terminada.

El DoD se aplica a las tareas gestionadas mediante GitHub Issues y Pull Requests.

### 2. Criterios obligatorios

Una tarea se considera terminada cuando cumple todos los criterios aplicables:

- [ ] **Criterios de aceptación cumplidos:** la funcionalidad realiza lo especificado en el Issue.
- [ ] **Código implementado:** los cambios necesarios están completos.
- [ ] **Pruebas aprobadas:** se han ejecutado satisfactoriamente las pruebas correspondientes.
- [ ] **Revisión realizada:** el código ha sido revisado según la política del proyecto.
- [ ] **Documentación actualizada:** los documentos afectados reflejan los cambios.
- [ ] **Issue enlazado:** el trabajo está relacionado con un Issue de GitHub.
- [ ] **Commits identificables:** los commits utilizan la convención definida.
- [ ] **Pull Request registrado:** existe un PR con descripción y evidencias.
- [ ] **Integración completada:** los cambios están incorporados en la rama acordada.
- [ ] **Seguridad verificada:** no se incorporaron credenciales ni archivos sensibles.

Un criterio no aplicable debe justificarse explícitamente en el Pull Request.

### 3. Criterios de aceptación

Cada Issue debe definir condiciones observables y verificables.

**Ejemplo: inicio de sesión**

- El usuario puede ingresar correo y contraseña.
- El backend valida las credenciales.
- Las credenciales incorrectas generan una respuesta de error.
- El usuario autenticado recibe un token JWT.
- El sistema redirige al panel correspondiente a su rol.
- Los endpoints protegidos rechazan solicitudes sin autorización válida.

### 4. Política de pruebas

Las pruebas se clasificarán en:

| Tipo | Propósito | Evidencia |
|---|---|---|
| Unitarias | Verificar funciones individuales | Resultado de ejecución |
| Integración | Comprobar interacción entre componentes | Reporte de pruebas |
| API | Validar endpoints y respuestas HTTP | Resultado automatizado o registro de ejecución |
| Interfaz | Verificar comportamiento del frontend | Resultado de pruebas |
| Manuales | Validar flujos funcionales completos | Registro de ejecución y capturas |

Las pruebas automatizadas se incorporarán progresivamente.

No se marcará una prueba como aprobada si no existe evidencia de su ejecución.

### 5. Revisión humana

Antes de integrar una funcionalidad se revisará:

- Claridad y organización del código.
- Cumplimiento de los criterios de aceptación.
- Manejo de errores.
- Seguridad básica.
- Impacto sobre funcionalidades existentes.
- Documentación y resultados de pruebas.

Cuando exista un colaborador disponible, se solicitará una revisión independiente.

Si el proyecto se desarrolla individualmente, la autoevaluación deberá identificarse como tal y no como aprobación independiente.

### 6. Documentación

Según el alcance de los cambios, se actualizarán:

- `README.md`
- `docs/ARQUITECTURA.md`
- `docs/INVENTARIO.md`
- Documentación de endpoints.
- Instrucciones de instalación.
- Evidencias de pruebas.

### 7. Trazabilidad

Cada funcionalidad debe permitir identificar:

**Issue → Rama → Commit → Pull Request → Revisión → Integración**

Ejemplo de trazabilidad esperada:

| Elemento | Ejemplo |
|---|---|
| Issue | `#12 Implementar inicio de sesión` |
| Rama | `feature/frontend-login` |
| Commit | `feat(login): implementar formulario de acceso` |
| PR | `#18 Integrar inicio de sesión` |
| Destino | `develop` |
| Estado final | Done |

Los números del ejemplo son ilustrativos. En el proyecto se utilizarán los identificadores reales generados por GitHub.

### 8. Políticas del tablero

**Backlog:** tarea identificada, pendiente de priorización.

**To Do:** tarea definida, con criterios de aceptación y lista para iniciar.

**In Progress:** tarea asignada y en desarrollo.

**In Review:** implementación enviada a revisión mediante Pull Request.

**Done:** tarea integrada y con todos los criterios aplicables del DoD cumplidos.

No se permitirá mover una tarea a Done únicamente porque el código compila.

### 9. Evidencias de cumplimiento

Para cada tarea terminada se conservarán, cuando corresponda:

- Enlace al Issue.
- Enlace al Pull Request.
- Commits asociados.
- Resultado de pruebas.
- Registro de revisión.
- Documentación actualizada.
- Evidencia de integración.

### 10. Aplicación al MVP

Para declarar una versión del Sistema de Matrículas como MVP terminado se deberá:

1. Definir el alcance funcional de la versión.
2. Verificar las funcionalidades incluidas.
3. Ejecutar las pruebas correspondientes.
4. Documentar limitaciones conocidas.
5. Integrar los cambios mediante el flujo acordado.
6. Preparar una rama `release/*`.
7. Publicar una versión identificable en `main`.

### 11. Conclusión

El Definition of Done establece un estándar verificable para controlar la calidad de las entregas.

Su aplicación permitirá demostrar que el Sistema de Matrículas utiliza criterios de aceptación, pruebas, revisión, documentación y trazabilidad antes de considerar terminada una funcionalidad.