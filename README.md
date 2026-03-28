# Ingeniería Devops

## 🌳 Estrategia de Ramas: GitFlow
Para este proyecto hemos decidido implementar **GitFlow** como nuestra estrategia de ramificación. 

**Justificación:**
Elegi GitFlow porque nos proporciona una estructura robusta y predecible, ideal para el trabajo colaborativo. Separa claramente el código en producción (`main`) del código en desarrollo (`develop`). Además, el uso de ramas efímeras (`feature`, `hotfix`) nos permite trabajar en nuevas funcionalidades y resolver errores críticos en producción de manera aislada sin interferir en el trabajo de otros desarrolladores.

## 📝 Convenciones del Proyecto

### Naming de Ramas (Branch Naming)
Todas las ramas deben crearse a partir de `develop` (excepto los hotfixes) y seguir esta convención de nombres en minúsculas y separados por guiones:
* `feature/nombre-de-la-funcionalidad`: Para nuevos desarrollos.
* `hotfix/nombre-del-error`: Para errores críticos en producción (salen de `main` y se fusionan en `main` y `develop`).


### Flujos de Merge y Estrategia de Revisión
1. **Desarrollo:** Todo el trabajo se realiza en ramas `feature/*` o `hotfix/*`. Nunca se hace commit directo a `main` o `develop`.
2. **Pull Requests (PR):** Para integrar código, se debe abrir un PR hacia `develop` (o hacia `main` si es un hotfix).
3. **Revisión:** Todo PR debe ser revisado y aprobado por al menos 1 desarrollador distinto al autor antes de ser fusionado.


> ⚠️ **Aviso de Versión:** Este proyecto se encuentra actualmente en la versión estable v1.0.1.