
# Despliegue de PokeDex en Microsoft Azure

## 1. Introducción

En este documento explico el proceso que realicé para desplegar la aplicación PokeDex de Pueblo Paleta Inc. en Microsoft Azure, utilizando Azure App Service para Windows.

El procedimiento incluyó la preparación del proyecto Angular, la compilación para producción, la publicación de los archivos mediante Kudu y la evaluación de los encabezados HTTP de seguridad con SecurityHeaders.com.

## 2. Creación del servicio en Azure

Primero ingresé al [Portal de Azure](https://portal.azure.com/) con mi cuenta de Azure for Students.

Después realicé los siguientes pasos:

1.  Busqué el servicio **App Services**.
    
2.  Inicié la creación de una aplicación web.
    
3.  Seleccioné la suscripción y el grupo de recursos disponibles.
    
4.  Asigné un nombre al servicio web.
    
5.  Seleccioné la región **West US 3**.
    
6.  Elegí **Windows** como sistema operativo.
    
7.  Seleccioné un plan de alojamiento disponible para mi suscripción.
    
8.  Revisé la configuración y creé el recurso.
    
9.  Cuando terminó la implementación, ingresé al App Service y localicé la URL pública.
    

La dirección que utilicé para acceder a la aplicación es:

[https://app-pokedex-web-prod-ar-asf6dtb5faczcsfv.westus3-01.azurewebsites.net/](https://app-pokedex-web-prod-ar-asf6dtb5faczcsfv.westus3-01.azurewebsites.net/)

## 3. Preparación del proyecto Angular

Abrí el código fuente de PokeDex en Visual Studio Code y localicé la carpeta del proyecto Angular, donde se encuentra el archivo `package.json`.

Desde la terminal integrada ejecuté el siguiente comando para instalar las dependencias:

```
npm install
```

Una vez finalizada la instalación, ejecuté el comando de compilación:

```
npx ng build
```

Este proceso generó los archivos optimizados para producción dentro de la carpeta `dist`.

Después localicé el directorio que contenía el archivo `index.html`, junto con los recursos estáticos, archivos JavaScript y hojas de estilo generados por Angular.

## 4. Preparación de los archivos para publicación

Para publicar la aplicación, preparé un archivo ZIP con el contenido de la carpeta compilada.

Incluí el archivo `index.html`, la carpeta `assets` y los archivos JavaScript, CSS y demás recursos generados durante la compilación.

Antes de publicar, comprobé que `index.html` estuviera directamente en la raíz del ZIP, sin una carpeta adicional que contuviera todos los archivos.

## 5. Publicación mediante Kudu

Después de preparar el ZIP, realicé la publicación de la siguiente manera:

1.  Ingresé al recurso App Service desde Azure Portal.
    
2.  Abrí las herramientas de Kudu correspondientes al servicio.
    
3.  Accedí a **Zip Push Deploy**.
    
4.  Cargué el archivo ZIP con los archivos compilados.
    
5.  Esperé a que terminara el proceso de publicación.
    
6.  Ingresé al explorador de archivos de Kudu y comprobé que los archivos estuvieran publicados en `site/wwwroot`.
    

Verifiqué que `index.html` y los recursos generados por Angular estuvieran en la ubicación desde la que Azure sirve la aplicación.

## 6. Pruebas de funcionamiento

Después de publicar los archivos, abrí la URL pública de PokeDex en el navegador.

Comprobé que la aplicación cargara y revisé la disponibilidad de los recursos estáticos.

Durante las pruebas encontré un inconveniente con la ruta de algunas imágenes. La ruta `/pokedex-angular/assets/images/` no respondía correctamente, mientras que `/assets/images/` sí funcionaba.

Por ese motivo, ajusté la ruta de las imágenes en la configuración de producción de Angular y generé una nueva compilación para publicar los archivos actualizados.

Finalmente, comprobé nuevamente el acceso a la aplicación desde su URL pública.

## 7. Resultado final

En la evaluación, SecurityHeaders.com otorgó a la aplicación una calificación **A**.

El informe confirmó la presencia de los siguientes encabezados:

Encabezado

Función

`Strict-Transport-Security`

Indica al navegador que utilice HTTPS durante el periodo establecido.

`Content-Security-Policy`

Define qué recursos puede cargar la aplicación.

`X-Frame-Options`

Ayuda a prevenir la inclusión de la página en marcos de otros sitios.

`X-Content-Type-Options`

Evita la interpretación de contenido con un tipo MIME diferente al declarado.

`Referrer-Policy`

Controla la información de referencia enviada a otros sitios.

`Permissions-Policy`

Permite limitar determinadas funciones del navegador.

El resultado mostró que los seis encabezados fueron reconocidos correctamente.

### 7.2. Advertencia de Content-Security-Policy

Aunque el resultado final fue **A**, la herramienta mostró una advertencia relacionada con el uso de `'unsafe-inline'` en la directiva `script-src` de Content-Security-Policy.

Esta opción permite determinados scripts en línea y reduce parte de la protección que ofrece una política más estricta. Por tanto, la calificación obtenida es satisfactoria, pero existe una oportunidad de mejora para reforzar la política CSP.

## 8. Conclusiones

Mediante este procedimiento desplegué PokeDex en Microsoft Azure utilizando Azure App Service para Windows y Kudu para publicar los archivos compilados de Angular.

Durante las pruebas corregí un problema con las rutas de las imágenes y verifiqué que la aplicación estuviera disponible desde su URL pública.

Finalmente, evalué los encabezados HTTP de seguridad con SecurityHeaders.com y obtuve una calificación A. El informe también permitió identificar una advertencia relacionada con la política CSP, que puede mejorarse para reducir el uso de scripts en línea.

Este ejercicio me permitió practicar el despliegue de aplicaciones web en la nube, la solución de inconvenientes durante la publicación y la evaluación de medidas básicas de seguridad web.

## 9. Referencias

-   [Portal de Microsoft Azure](https://portal.azure.com/)
    
-   [Documentación de Azure App Service](https://learn.microsoft.com/azure/app-service/)
    
-   [Angular](https://angular.dev/)
    
-   [StackEdit](https://stackedit.io/)
    
-   [SecurityHeaders.com](https://securityheaders.com/)
