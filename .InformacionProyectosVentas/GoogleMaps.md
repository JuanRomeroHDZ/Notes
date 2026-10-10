Para la asignación (incrustación) del mapa del lugar podemos seguir los siguientes pasos (método con iframe, sin necesidad de API Key):

1. **Visitar la página oficial**: Entrar a Google Maps, [aquí](https://www.google.com/maps).
2. **Buscar el lugar**: Ingresar el nombre de la empresa, dirección o lugar que deseamos mostrar en el buscador del mapa.
3. **Compartir**: Una vez seleccionado el lugar en el panel lateral, hacer clic en el botón de "Compartir" (ícono de conexión/flecha).
4. **Incorporar un mapa**: En la ventana emergente que aparece, seleccionar la pestaña superior que dice "Incorporar un mapa".
5. **Ajustar el tamaño**: 
   - Elegir el tamaño del mapa en el menú desplegable (Pequeño, Mediano, Grande o Tamaño personalizado). 
   - *Tip:* Es recomendable usar un tamaño que luego puedas adaptar con CSS (ej. dándole `width="100%"` y `height="400"` al iframe).
6. **Copiar HTML**: Hacer clic en el botón "Copiar HTML". Esto te copiará un código de etiqueta `<iframe>`.
7. **Incrustarlo en el código**: 
   - Pegar el código del iframe en la estructura HTML de tu proyecto, en la sección donde deseas que aparezca el mapa.
   - *Recomendación:* Mantener (o agregar si no está) el atributo `loading="lazy"` dentro de la etiqueta iframe para mejorar los tiempos de carga de la página.
