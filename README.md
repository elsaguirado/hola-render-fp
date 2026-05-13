# Proyecto: Despliegue de Web Estática en Render con Entornos PRE y PRO

Este repositorio contiene una práctica de despliegue continuo utilizando una arquitectura de dos entornos (Preproducción y Producción) para una aplicación web estática simple.

## 📝 Descripción del Proyecto

El objetivo de este proyecto es implementar un flujo de trabajo profesional de desarrollo web, donde se utiliza **GitHub** como control de versiones y **Render** como plataforma de despliegue. Se incluye una fase de validación mediante tests automáticos antes de promocionar los cambios al entorno final de producción.

## 🚀 Tecnologías y Herramientas

* **HTML5**: Estructura básica de la web estática.
* **GitHub**: Repositorio de código y gestión de ramas (`pre` y `main`).
* **Render**: Hosting y despliegue automático (Static Site).
* **Python & Pytest**: Framework para la ejecución de pruebas de validación.
* **Requests**: Librería de Python para realizar peticiones HTTP en los tests.

## 🛠️ Estructura del Repositorio

* `index.html`: Archivo principal de la web.
* `tests/` (opcional): Carpeta que contiene los scripts de validación.
* `README.md`: Documentación del proyecto (este archivo).

## ⚙️ Configuración de Entornos

El proyecto se divide en dos ramas principales que se corresponden con los servicios creados en Render:

1.  **Entorno PRE (Preproducción)**:
    * **Rama**: `pre`
    * **Propósito**: Testing y validación de cambios.
    * **URL**: `https://hola-render-pre-jkuu.onrender.com`

2.  **Entorno PRO (Producción)**:
    * **Rama**: `main`
    * **Propósito**: Entorno final para el usuario final.
    * **URL**: `https://hola-render-pro-k94t.onrender.com`

## ✅ Flujo de Trabajo y Validación

Para asegurar la calidad del despliegue, se sigue este proceso:

1.  Se realizan los cambios en la rama `pre` y se suben al repositorio (`git push origin pre`).
2.  Render detecta el cambio y despliega automáticamente en la URL de PRE.
3.  Se ejecutan los tests de validación con el comando:
    ```bash
    pytest test_deploy.py
    ```
4.  **Tests incluidos**:
    * Verificación de código de estado HTTP 200.
    * Validación de la presencia del texto "Hola mundo desde Render".
    * Comprobación de tiempo de respuesta (< 2 segundos).
    * Verificación de cabecera `Content-Type: text/html`.

5.  Si todos los tests son exitosos, se realiza el merge a la rama `main`:
    ```bash
    git checkout main
    git merge pre
    git push origin main
    ```

## 👥 Autores

* **Elsa Guirado Rodríguez**
* **Samira Benyaala**
* *1º ASIR - IES Francisco Javier de Burgos* (Curso 25-26)

---
*Este proyecto se ha realizado como parte de la formación en colaboración con NTT DATA.*
