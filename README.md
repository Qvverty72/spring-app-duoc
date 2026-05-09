# Spring Boot App - Pipeline CI/CD & Contenedores

Este proyecto consiste en un microservicio desarrollado en Java con Spring Boot, diseñado para demostrar la implementación de un ciclo de vida de desarrollo moderno utilizando Docker, GitHub Actions y prácticas de DevSecOps.

## 🚀 Tecnologías Utilizadas
* **Lenguaje:** Java 21
* **Framework:** Spring Boot
* **Contenedores:** Docker & Docker Compose
* **CI/CD:** GitHub Actions
* **Seguridad:** Snyk (Escaneo de dependencias)
* **Pruebas:** JUnit 5

---

## 🛠️ 1. Contenerización (IE1)

El microservicio ha sido contenerizado utilizando un **Dockerfile** optimizado de múltiples etapas (*multi-stage build*). Esto garantiza una imagen ligera para producción, separando el entorno de compilación del de ejecución.

**Características del Dockerfile:**
- **Build Stage:** Utiliza Maven y JDK 21 para compilar el código.
- **Run Stage:** Utiliza JRE 21 para ejecutar el artefacto `.jar`.

---

## ⛓️ 2. Pipeline de CI/CD (IE1, IE2, IE3, IE4)

Se implementó un flujo de trabajo automatizado en **GitHub Actions** (`.github/workflows/main.yml`) que se activa en cada `push` a la rama principal.

### Etapas del Pipeline:
1. **Pruebas Unitarias (IE2):** Ejecución de tests automatizados con JUnit mediante el comando `mvn test`. Si un test falla, el pipeline se detiene inmediatamente.
2. **Escaneo de Seguridad (IE3):** Integración con **Snyk** para detectar vulnerabilidades en dependencias y malas prácticas en el código.
3. **Build de Imagen (IE1):** Construcción automática de la imagen Docker etiquetada con el hash del commit para garantizar la trazabilidad.
4. **Despliegue Simulado (IE4):** Orquestación mediante **Docker Compose** en el runner de GitHub para validar que el microservicio y sus dependencias levantan correctamente.

---

## 🛡️ 3. Seguridad y Calidad (IE3)

Para garantizar la calidad y seguridad del software, el pipeline incluye:
- **Bloqueo por Fallo:** El pipeline está configurado para fallar si los tests unitarios no pasan.
- **Alertas de Snyk:** El análisis de seguridad genera reportes (SARIF/JSON) que se suben como artefactos. Se ha configurado el pipeline para alertar sobre vulnerabilidades críticas.
- **Trazabilidad:** Cada imagen construida está vinculada a un commit específico de GitHub, permitiendo saber exactamente qué código está corriendo en cada contenedor.

---

## 🏗️ 4. Orquestación (IE5)

La estrategia de orquestación se basa en **Docker Compose**, lo que permite definir y correr aplicaciones multi-contenedor.

Para levantar el entorno localmente, ejecute:
```bash
docker-compose up -d


