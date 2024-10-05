# Playwright || Cucumber || JavaScript

## Saucedemo Automation Project

Este repositorio contiene las automatizaciones de pruebas para [saucedemo.com](https://www.saucedemo.com), incluyendo pruebas de regresión, end-to-end (E2E) y accesibilidad utilizando Playwright, Cucumber, y Axe.

## Requisitos previos

Antes de clonar y ejecutar el proyecto, asegúrate de tener las siguientes herramientas instaladas en tu máquina local:

- **Node.js** (versión recomendada: 16.x o superior)
- **npm** (que viene con Node.js)
- **Jenkins** (si planeas ejecutar las pruebas localmente con CI)
- **Git** (para clonar el repositorio)
- **Docker** (opcional, si deseas ejecutar los contenedores)

## Instalación

Sigue estos pasos para clonar el repositorio y configurar el proyecto:

1. Clona el repositorio en tu máquina local:
   ```bash
   git clone https://github.com/tu-usuario/tu-repositorio.git

2. Navega al directorio del proyecto:
   ```bash
   cd tu-repositorio
   
3. Instala las dependencias del proyecto utilizando npm:
   ```bash
   npm install

## Configuración

### Playwright

  Playwright está configurado para ejecutar pruebas en navegadores web principales. Para asegurarte de que Playwright está completamente configurado, ejecuta el siguiente comando para      instalar los navegadores requeridos:
  ```bash
  npx playwright install
  ```

## Monocart y Reportes Nativos de Playwright

El proyecto está configurado para generar reportes visuales utilizando Monocart y los reportes nativos de Playwright. No es necesario realizar configuraciones adicionales, ya que estos están integrados dentro del código del proyecto.

Para ejecutar y generar los reportes:

1. Ejecuta las pruebas:
   ```bash
   npx playwright test
   ```
2. Los reportes se generarán en la carpeta test-results para los reportes nativos de Playwright y monocart-reports para los reportes de Monocart.

## Axe para Pruebas de Accesibilidad
Este proyecto utiliza la librería Axe para validar la accesibilidad de las páginas. Las pruebas de accesibilidad ya están configuradas en los casos de prueba.

Para ejecutar las pruebas de accesibilidad:

```bash
npx playwright test --grep @accessibility
```

Los resultados de las pruebas se incluirán en el reporte generado por Playwright.

## Ejecución de Pruebas

Ejecución Local
Puedes ejecutar todas las pruebas locales con el siguiente comando:
```bash
npx playwright test
```

Para ejecutar pruebas específicas (por ejemplo, solo las pruebas de accesibilidad o de un módulo en particular):
```bash
npx playwright test --grep @tag
```

Las etiquetas (@tag) pueden encontrarse dentro de cada archivo de prueba.

## Ejecución en Docker

Si prefieres ejecutar las pruebas en un contenedor Docker, asegúrate de tener Docker instalado y luego usa el siguiente comando:

1. Construye la imagen Docker:

```bash
docker build -t saucedemo-automation .
```

2. Ejecuta el contenedor:
```bash
docker run -it saucedemo-automation
```
## Ejecución con GitHub Actions

El proyecto incluye un archivo .github/workflows/playwright.yml que define un workflow para ejecutar las pruebas automatizadas en GitHub Actions.

Para activar el workflow, solo necesitas hacer push de tu código a GitHub, y las pruebas se ejecutarán automáticamente en cada commit.

Estructura del Proyecto
El proyecto sigue una estructura estándar que incluye los siguientes directorios principales:

```bash
|-- tests/
|   |-- e2e/
|   |   |-- login.test.js
|   |   |-- checkout.test.js
|   |-- accessibility/
|   |   |-- homepage.accessibility.test.js
|   |   |-- login.accessibility.test.js
|-- features/
|   |-- login.feature
|   |-- checkout.feature
|-- reports/
|   |-- monocart-reports/
|   |-- test-results/

```

* tests/: Contiene los archivos de prueba automatizada, organizados por tipo de prueba (E2E y Accesibilidad).
* features/: Contiene los archivos de características de Cucumber que definen los flujos de usuario.
* reports/: Carpeta donde se almacenan los reportes generados tanto por Monocart como por Playwright.

## Ejecución con Jenkins
Si tienes Jenkins instalado localmente, sigue estos pasos para ejecutar el proyecto dentro de Jenkins:

Abre Jenkins y crea un nuevo pipeline.
Configura el pipeline para que ejecute el siguiente script:
```bash
pipeline {
    agent any
    stages {
        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }
        stage('Run Tests') {
            steps {
                sh 'npx playwright test'
            }
        }
        stage('Generate Reports') {
            steps {
                sh 'npx playwright show-report'
            }
        }
    }
}
```

## Contribución

Si deseas contribuir a este proyecto, por favor sigue estos pasos:

1. Haz un fork del repositorio.
2. Crea una nueva rama para tus cambios:
```bash
git checkout -b feature/nueva-funcionalidad
```
3. Haz commit de tus cambios
```bash
git commit -m 'Agrega nueva funcionalidad'
```
4. Haz push a la rama:
```bash
git push origin feature/nueva-funcionalidad
```
5. Abre un Pull Request y espera la revisión de los administradores del proyecto.


# RESUMEN

### Explicación del Instructivo:

- **Requisitos previos**: Aclara qué necesita instalar el usuario antes de clonar y ejecutar el proyecto.
- **Instalación**: Incluye pasos claros para clonar, navegar al directorio e instalar las dependencias del proyecto.
- **Configuración**: Explica cómo configurar las herramientas principales, como Playwright, Monocart, y Axe.
- **Ejecución de Pruebas**: Proporciona instrucciones tanto para la ejecución local como para la ejecución en Jenkins, GitHub Actions y Docker.
- **Estructura del Proyecto**: Detalla la estructura de carpetas para facilitar la comprensión de cómo está organizado el código.
- **Contribución**: Instrucciones claras sobre cómo contribuir al proyecto.

