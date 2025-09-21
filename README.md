# Curso: Despliegue de aplicaciones con Docker<br/>CEC-EPN<br/><br/>Tarea 3:  Análisis de vulnerabilidades con Docker Scout

![Lenguaje][lngsrv-shield]
![Servidor de contenedores][cont-shield]

## Integrantes Grupo 3

- [Glenda Pallo](https://github.com/glendypallo/DespliegueContenedores-Tarea3-GP)
- [Patricia Jaramillo](https://github.com/PatyJaramillo/DespliegueContenedores-Tarea3-PJ)
- [William Ayala](https://github.com/wrayalav/DespliegueContenedores-Tarea3-WA)
- [Guillermo Cifuentes](https://github.com/guillogps/DespliegueContenedores-Tarea3-GC)
- [Ruperto Cisneros](https://github.com/srcisnerosv-star/DespliegueContenedores-Tarea3-RC)

<br/>

## Introducción

El presente flujo de trabajo en GitHub Actions tiene como objetivo automatizar el proceso de construcción, publicación y análisis de imágenes Docker dentro de un entorno de integración continua. La configuración incluye la autenticación en Docker Hub, la construcción de la imagen con docker/build-push-action, y el posterior análisis de vulnerabilidades con Docker Scout, garantizando así que las imágenes generadas sean seguras y confiables antes de ser utilizadas en entornos de despliegue.
Este pipeline implementa buenas prácticas de DevSecOps, al integrar el análisis de seguridad directamente en la cadena de construcción, permitiendo detectar vulnerabilidades desde etapas tempranas y asegurando la trazabilidad de cada versión mediante el etiquetado con el hash del commit (sha). Asimismo, se incorpora la generación y almacenamiento del reporte en formato JSON como artefacto, lo que facilita la auditoría y el seguimiento de hallazgos de seguridad.

<br/>

## Construido con

- Docker
- Docker Scout
- Docker Compose
- [Python](https://hub.docker.com/_/python)

<br/>

## Archivos

La tarea contiene los siguientes archivos:

| Archivo | Descripción |
| ---- | ---- |
| [Dockerfile](Dockerfile) | Archivo que contiene las instrucciones para crear una imagen en Docker. |
| [requirements.txt](requirements.txt) | Archivo donde se define los requisitos de la aplicación python. |
| [index.html](index.html) | Página de inicio | 
| [scout.yml](.github/workflows/scout.yml) | Archivo que define la orquestación del análisis de la imagen de fast-api. |

<br/>

## Procedimiento

1. Recopilar archivos del ejercicio `fast-api`.

2. Cargarlos a GitHub.

   ![Imagen de WhatsApp 2025-09-20 a las 22 29 23_128dd842](https://github.com/user-attachments/assets/09d340e5-f517-4ee7-aec5-3c049eeb5ecf)

4. Definir las variables de entorno con las credenciales del Git Hub de cada integrante del Grupo 3

   <img width="886" height="440" alt="image" src="https://github.com/user-attachments/assets/c7ed43ff-1077-49aa-98eb-695b85b4cb1a" />

   <img width="886" height="437" alt="image" src="https://github.com/user-attachments/assets/3387aace-5b7f-4099-a9d0-95a2dd3a5d60" />

5. Construir el workflow del `Docker Scout`

   ![Imagen de WhatsApp 2025-09-20 a las 22 56 25_d6d5c415](https://github.com/user-attachments/assets/a532f837-2eda-4f14-a4e2-6a6be162d6cf)

5. Definir la orquestación para analizar la imagen de fast-api indicando el nombre de la imagen con la cual se creará el repositorio en el Docker Hub

   <img width="1920" height="945" alt="image" src="https://github.com/user-attachments/assets/b2bbefa9-546e-4053-b70a-9867578eeedb" />

   <img width="1920" height="945" alt="image" src="https://github.com/user-attachments/assets/57654097-72c6-43ce-be82-0c3b6da77d56" />

6. Validar la ejecución del workflow

   <img width="1920" height="945" alt="image" src="https://github.com/user-attachments/assets/330a9f29-cb9a-4a5f-96a3-63f5114115c0" />

   <img width="1920" height="945" alt="image" src="https://github.com/user-attachments/assets/aac1d903-033d-440d-a221-301350d93347" />

7. Resultado del análisis del Docker Scout

   ```
   ...Storing image for indexing
    ✓ Image stored for indexing
    ...Indexing
    ✓ Indexed 147 packages
    ✗ Detected 11 vulnerable packages with a total of 23 vulnerabilities
    ✓ Report written to json
   ```

8. Validar la creación de la imagen en el Docker Hub

   <img width="1920" height="945" alt="image" src="https://github.com/user-attachments/assets/7f8e7873-847f-428b-9517-9c9741cf9c6f" />

<br/>

## Conclusiones

- La integración de Docker Scout dentro del flujo de GitHub Actions representa un paso estratégico hacia la consolidación de un ciclo de vida seguro para las aplicaciones contenerizadas. Gracias a este proceso automatizado:

- Se asegura la consistencia en la construcción de imágenes, al centralizar la definición del Dockerfile y los parámetros de compilación.

- Se fortalecen los controles de seguridad preventiva, al identificar vulnerabilidades en librerías y dependencias antes de llegar a entornos productivos.

- Se mejora la trazabilidad y gobernanza, ya que los reportes JSON almacenados como artefactos permiten un análisis posterior y la integración con sistemas de gestión de seguridad.

- Se potencia la eficiencia operativa, al reducir riesgos de fallas o brechas de seguridad en fases posteriores del despliegue.

<!-- MARKDOWN LINKS & IMAGES -->
[lngsrv-shield]: https://img.shields.io/badge/LNG-PYTHON-9cf?style=for-the-badge&logo=python&logoColor=red
[cont-shield]: https://img.shields.io/badge/CONTAINER-DOCKER-red?style=for-the-badge&logo=docker
