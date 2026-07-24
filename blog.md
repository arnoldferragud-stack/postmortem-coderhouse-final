# Cuando un despliegue falló: análisis post-mortem de un incidente técnico

## Introducción

En el desarrollo de software es común enfrentar inconvenientes durante la publicación de una aplicación. Lo importante no es evitar todos los errores, sino aprender de ellos y documentar las soluciones para mejorar los procesos futuros.

Este artículo presenta un análisis post-mortem de un incidente ocurrido durante el despliegue de un proyecto ficticio llamado **TaskFlow**, desarrollado como ejemplo académico para demostrar buenas prácticas de documentación técnica y control de versiones.

---

# Contexto

TaskFlow es una aplicación web diseñada para ayudar a pequeñas empresas a gestionar tareas entre sus colaboradores.

El sistema permite crear tareas, asignarlas a distintos empleados, modificar su estado y eliminarlas cuando se completan.

Una vez finalizado el desarrollo, el equipo decidió publicar una versión de prueba utilizando GitHub Pages para compartirla con un grupo reducido de usuarios y recibir comentarios antes del lanzamiento oficial.

El despliegue parecía haberse realizado correctamente, pero al acceder a la página apareció un problema inesperado.

---

# Problema

Después de publicar el proyecto, los usuarios únicamente visualizaban una pantalla completamente en blanco.

La aplicación funcionaba sin inconvenientes en el entorno de desarrollo, por lo que inicialmente se pensó que GitHub Pages estaba experimentando algún problema.

Sin embargo, tras realizar una investigación más detallada, se comprobó que el inconveniente se encontraba en la propia aplicación.

Aunque el error era pequeño, impedía completamente el funcionamiento del sistema.

---

# Acciones realizadas

Para resolver el incidente se siguió un proceso ordenado.

## 1. Verificación del despliegue

Se comprobó que todos los archivos habían sido publicados correctamente.

## 2. Revisión de la consola del navegador

Se detectó un error indicando que un archivo JavaScript no podía encontrarse.

## 3. Identificación de la causa

El archivo principal del proyecto se llamaba:

App.js

Sin embargo, el archivo HTML intentaba cargar:

app.js

GitHub Pages diferencia las letras mayúsculas y minúsculas en los nombres de los archivos, mientras que durante el desarrollo local ese detalle había pasado desapercibido.

## 4. Corrección

Se modificó el nombre del archivo para que coincidiera exactamente con la referencia utilizada en el proyecto.

Posteriormente se publicó nuevamente la aplicación.

## 5. Validación

Después del nuevo despliegue el sitio volvió a funcionar correctamente.

---

# Post-Mortem Constructivo

## ¿Qué ocurrió?

El despliegue fue exitoso, pero la aplicación no cargó correctamente debido a un error en el nombre de un archivo.

## ¿Cuál fue la causa raíz?

Una diferencia entre mayúsculas y minúsculas provocó que GitHub Pages no pudiera localizar el archivo JavaScript principal.

## ¿Cómo se resolvió?

Se corrigió el nombre del archivo y se realizó un nuevo despliegue.

## ¿Qué acciones preventivas se implementarán?

- Crear una lista de verificación antes de cada despliegue.
- Revisar todos los nombres de archivos.
- Utilizar Pull Requests para revisar los cambios.
- Documentar cada incidente relevante.

---

# Aprendizajes

Este incidente permitió comprender que errores muy pequeños pueden generar consecuencias importantes durante un despliegue.

También reforzó la importancia de utilizar un sistema de control de versiones como GitHub, ya que facilitó identificar los cambios realizados y mantener un historial ordenado del proyecto.

Finalmente, quedó demostrado que documentar los incidentes ayuda a que todo el equipo aprenda y reduzca la probabilidad de repetir el mismo error.

---

# Feedback Radicalmente Sincero

Durante la elaboración de esta documentación se recibieron comentarios indicando que algunas explicaciones eran demasiado técnicas para personas sin experiencia en desarrollo.

Como respuesta, se reescribieron varios apartados utilizando un lenguaje más claro y ejemplos sencillos.

Este proceso permitió mejorar significativamente la calidad de la documentación y hacerla más accesible para cualquier integrante del equipo.

---

# Conclusión

La documentación técnica no solo sirve para registrar errores, sino también para compartir conocimiento y fortalecer el trabajo colaborativo.

Un análisis post-mortem bien realizado convierte un incidente en una oportunidad de aprendizaje y mejora continua.
