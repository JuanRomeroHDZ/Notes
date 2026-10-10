Es necesario obtener el fragmento de código de seguimiento, el cual se genera desde la plataforma de Google Analytics. Pasos a seguir para configurarlo (actualmente en GA4):

1. Entrar a la página oficial, [aquí](https://analytics.google.com/analytics/web/).
2. Crear una nueva "Propiedad" con el nombre del proyecto (de preferencia).
3. Configurar un "Flujo de datos" seleccionando la plataforma "Web" e ingresando la URL del sitio.
4. Una vez creado el flujo, copiar el "ID de medición" (tiene el formato `G-XXXXXXXXXX`).
5. Seguir los pasos de inserción del código global (`gtag.js`):
   - Deberás copiar el bloque de código proporcionado e incrustarlo dentro de la etiqueta `<head>` de todas las páginas de tu sitio web, lo más arriba posible.
6. Verificar el funcionamiento:
   - Una vez subido el sitio web, puedes revisar los reportes en "Tiempo real" en Analytics, o utilizar la extensión de navegador "Google Tag Assistant" para comprobar que se envían datos correctamente.
