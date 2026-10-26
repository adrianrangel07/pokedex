
# PokeDex en la nube (Microsoft Azure)

Realicé el despliegue de la aplicación **PokeDex**, de Pueblo Paleta Inc., utilizando **Microsoft Azure for Students** y el servicio **Azure App Service para Windows**.

-   **URL pública:**  [PokeDex en Azure](https://app-pokedex-web-prod-ar-asf6dtb5faczcsfv.westus3-01.azurewebsites.net/)
    
-   **Proceso de despliegue y seguridad:**  [Despliegue.md](https://Despliegue.md)
    
-   **Autor:** Adrian Rangel Vides — Tecnológico Comfenalco
    

----------

## 1. Objetivo del proyecto

El objetivo de este proyecto fue desplegar la aplicación PokeDex en una plataforma de nube pública, verificar su funcionamiento desde Internet y documentar el proceso de configuración, compilación y publicación.

También evalué la seguridad de la aplicación mediante SecurityHeaders.com e implementé encabezados HTTP para mejorar la protección de las comunicaciones y el comportamiento del navegador.

## 2. Creación de la cuenta en Azure for Students

### Paso 1. Ingresé a Azure for Students

Accedí al sitio oficial [Azure for Students](https://azure.microsoft.com/free/students) y seleccioné la opción para comenzar el registro.

### Paso 2. Inicié sesión con Microsoft

Inicié sesión con una cuenta Microsoft existente para continuar con el proceso de activación.

### Paso 3. Verifiqué mi condición de estudiante

Ingresé los datos solicitados y seguí el procedimiento de verificación de estudiante indicado por Microsoft.

### Paso 4. Completé el registro

Completé la información solicitada y acepté los términos de la oferta para finalizar la activación de Azure for Students.

### Paso 5. Accedí al portal de Azure

Ingresé a [Azure Portal](https://portal.azure.com/) y comprobé que podía acceder a la suscripción y administrar recursos en la nube.

### Paso 6. Revisé la suscripción

Antes de crear los recursos, revisé la información de la suscripción disponible y las opciones para consultar el consumo.

## 3. Configuración inicial de Azure

Para alojar la aplicación utilicé **Azure App Service** con sistema operativo **Windows**.

1.  Ingresé al portal de Azure y busqué el servicio **App Services**.
    
2.  Inicié la creación de una aplicación web.
    
3.  Seleccioné la suscripción y el grupo de recursos correspondientes.
    
4.  Definí el nombre del servicio y seleccioné la región **West US 3**.
    
5.  Seleccioné Windows como sistema operativo y el plan gratuito de mi suscripción.
    
6.  Revisé la configuración y creé el recurso.
    
7.  Cuando terminó la implementación, ingresé al App Service y localicé la URL pública asignada.
    

Los detalles de la compilación, publicación y verificación se encuentran en [Despliegue.md](https://github.com/adrianrangel07/pokedex/blob/main/DESPLIEGUE.md).

## 4. Tecnologías y herramientas utilizadas

-   **Angular:** framework utilizado para desarrollar la aplicación.
    
-   **Node.js y npm:** herramientas utilizadas para instalar dependencias y compilar el proyecto.
    
-   **Visual Studio Code:** editor utilizado para trabajar con el código y ejecutar comandos.
    
-   **Microsoft Azure App Service para Windows:** servicio utilizado para alojar la aplicación.
    
-   **Kudu — Zip Push Deploy:** herramienta utilizada para publicar los archivos compilados.
    
-   **StackEdit:** editor utilizado para trabajar con la documentación Markdown.
    
-   **SecurityHeaders.com:** herramienta utilizada para evaluar los encabezados HTTP de seguridad.
    

## 5. Despliegue y verificación de la aplicación

Preparé el proyecto Angular en mi computador, instalé las dependencias y generé la compilación de producción. Posteriormente, empaqueté los archivos generados en un ZIP y los publiqué en Azure mediante Kudu.

Después de la publicación, ingresé a la URL pública y comprobé que la aplicación cargara correctamente. Durante las pruebas también identifiqué y corregí un inconveniente con las rutas de las imágenes para que los recursos estáticos se cargaran desde su ubicación correcta.

**URL pública de la aplicación:**

[https://app-pokedex-web-prod-ar-asf6dtb5faczcsfv.westus3-01.azurewebsites.net/](https://app-pokedex-web-prod-ar-asf6dtb5faczcsfv.westus3-01.azurewebsites.net/)

## 6. Configuración y evaluación de seguridad

Para evaluar la seguridad de la aplicación, utilicé [SecurityHeaders.com](https://securityheaders.com/), que analiza los encabezados HTTP enviados por el servidor.

En la configuración final verificada, la herramienta otorgó una **calificación A** y reconoció la presencia de los siguientes encabezados:

-   `Strict-Transport-Security`: establece el uso de conexiones HTTPS durante el periodo definido.
    
-   `Content-Security-Policy`: establece las fuentes y los tipos de recursos que la página puede cargar.
    
-   `X-Frame-Options`: ayuda a prevenir la inclusión de la página en marcos de otros sitios.
    
-   `X-Content-Type-Options`: evita la interpretación de contenido como un tipo MIME distinto al declarado.
    
-   `Referrer-Policy`: controla la información de referencia que se envía al navegar hacia otros recursos.
    
-   `Permissions-Policy`: restringe el acceso a determinadas funciones del navegador.
    

El resultado confirmó que los seis encabezados fueron detectados correctamente por la herramienta.

### Advertencia identificada

El informe mostró una advertencia relacionada con la directiva `script-src` de la política CSP, debido al uso de `'unsafe-inline'`. Esta configuración permite determinados scripts en línea, pero reduce parte de la protección que ofrece una política de seguridad de contenido más estricta.

A pesar de esta advertencia, el análisis otorgó una calificación **A**.

## 7. Control del consumo de Azure

Para controlar el uso de los recursos, puedo consultar la información de mi suscripción y las opciones de costos desde Azure Portal, en la sección **Cost Management + Billing**, según las funciones disponibles en mi cuenta.

También es recomendable revisar periódicamente el estado del App Service y eliminar los recursos que ya no se necesiten, con el fin de evitar consumos innecesarios.

## 8. Conclusiones

Con este proyecto desplegué la aplicación PokeDex en Microsoft Azure mediante Azure App Service para Windows. Realicé la compilación de Angular, publiqué los archivos mediante Kudu y comprobé el acceso a la aplicación desde su URL pública.

Además, evalué los encabezados HTTP con SecurityHeaders.com y obtuve una **calificación A**, con los seis encabezados de seguridad reconocidos por la herramienta.

Este ejercicio me permitió practicar el despliegue de aplicaciones web en la nube, la solución de problemas durante la publicación y la aplicación de medidas de seguridad en el servidor web.

## 9. Referencias

-   [Azure for Students](https://azure.microsoft.com/free/students)
    
-   [Portal de Azure](https://portal.azure.com/)
    
-   [Documentación de Azure App Service](https://learn.microsoft.com/azure/app-service/)
    
-   [Angular](https://angular.dev/)
    
-   [StackEdit](https://stackedit.io/)
    
-   [SecurityHeaders.com](https://securityheaders.com/)
