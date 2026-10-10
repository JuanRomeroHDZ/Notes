Para realizar la configuración y obtener las reseñas de un negocio, utilizamos "Place IDs" y la API de Google. Aspectos a tener en cuenta:

1. **Obtener el Place ID**:
   - Es el identificador único de un lugar en la base de datos de Google.
   - Para conseguirlo rápidamente, podemos utilizar esta herramienta: [Enlace aquí](https://developers.google.com/maps/documentation/javascript/examples/places-placeid-finder).

2. **Configurar la API Key (Google Cloud)**:
   - Se debe acceder a la [Consola de Google Cloud](https://console.cloud.google.com/) y crear un proyecto.
   - Habilitar la **"Places API"**.
   - Crear una credencial de tipo "Clave de API" (API Key) y asegurarte de restringirla a tu dominio web por motivos de seguridad.

3. **Uso de la API para extraer las reseñas**:
   - Mediante código (JavaScript, Python, PHP, etc.), deberás realizar una consulta al endpoint de "Place Details" enviando el `Place ID` y tu `API Key`.
   - **Nota importante:** La API oficial de Google Maps actualmente solo devuelve por defecto las 5 reseñas más relevantes del lugar, no todas.

4. **Alternativas fáciles (sin código)**:
   - Si no deseas implementar la conexión a la API desde cero, existen plataformas externas (como Elfsight, EmbedSocial o widgets de WordPress) que facilitan integrar un carrusel de reseñas utilizando solo un iframe o un pequeño script.
