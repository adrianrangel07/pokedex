# PokeDex — Despliegue en Azure

## 1. Descripción del proyecto

PokeDex es una aplicación web desarrollada con Angular que permite explorar diferentes especies de Pokémon y consultar información relacionada con sus características y habilidades.

Este proyecto hace parte del caso de estudio propuesto para practicar el despliegue de aplicaciones web en una plataforma de nube pública y evaluar aspectos básicos de seguridad.

## 2. Objetivos

- Desplegar la aplicación PokeDex en una plataforma de nube pública.
- Utilizar Azure App Service para publicar la aplicación web.
- Documentar el procedimiento de compilación y despliegue.
- Evaluar la seguridad mediante SecurityHeaders.com.
- Identificar oportunidades de mejora en la configuración de encabezados HTTP.

## 3. Tecnologías utilizadas

- **Angular:** framework utilizado para desarrollar la aplicación.
- **Node.js y npm:** herramientas para gestionar dependencias y ejecutar la compilación.
- **Azure App Service:** servicio de alojamiento de la aplicación web.
- **Kudu:** herramienta utilizada para publicar los archivos compilados.
- **SecurityHeaders.com:** herramienta para evaluar los encabezados HTTP de seguridad.
- **StackEdit:** editor de documentos Markdown.

## 4. Requisitos previos

- Una cuenta de Microsoft con acceso a Azure.
- Un proyecto PokeDex descargado en el computador.
- Node.js y npm instalados.
- Visual Studio Code o un editor de código equivalente.
- Acceso a Azure App Service y Kudu.

## 5. Despliegue en Azure

La aplicación se compiló localmente utilizando Angular y posteriormente se publicaron los archivos generados en Azure App Service para Windows mediante Kudu y la herramienta Zip Push Deploy.

El procedimiento detallado se encuentra en el archivo [Despliegue.md](Despliegue.md).

## 6. Dirección de la aplicación

URL pública:

https://app-pokedex-web-prod-ar-asf6dtb5faczcsfv.westus3-01.azurewebsites.net/

## 7. Evaluación de seguridad

Se utilizó SecurityHeaders.com para analizar los encabezados HTTP de la aplicación.

En el análisis inicial se obtuvo una calificación **F**, debido a la ausencia de los siguientes encabezados:

- Strict-Transport-Security
- Content-Security-Policy
- X-Frame-Options
- X-Content-Type-Options
- Referrer-Policy
- Permissions-Policy

Se intentó configurar encabezados mediante el archivo `web.config`, pero la configuración generó errores HTTP 500 en el servidor. Por este motivo, el archivo se desactivó para recuperar el funcionamiento de la aplicación.

La configuración de encabezados queda pendiente de corrección y verificación. La calificación inicial no debe interpretarse como el resultado final de seguridad.

## 8. Conclusiones

El proyecto permitió practicar la compilación de una aplicación Angular, su publicación en Azure App Service y la evaluación inicial de su seguridad.

Como mejora pendiente, se requiere implementar una configuración de encabezados HTTP compatible con el servidor y volver a ejecutar el análisis para comprobar los resultados.

## 9. Referencias

- Azure: https://azure.microsoft.com/
- Angular: https://angular.dev/
- StackEdit: https://stackedit.io/
- SecurityHeaders.com: https://securityheaders.com/
