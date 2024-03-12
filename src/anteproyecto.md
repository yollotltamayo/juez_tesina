# Anteproyecto

## Título del trabajo

**"HERRAMIENTA DE EVALUACIÓN DE PROBLEMAS, GESTIÓN DE CONCURSOS Y PUBLICACIÓN DE CONTENIDOS EN PROGRAMACIÓN COMPETITIVA: JUEZ EN LÍNEA"**

## Objetivo del trabajo

El objetivo de la tesina es dotar al grupo de algoritmos (GUAPA) y a terceros con roles de problem setter (organizador) ,por medio de una pagina web, de la capacidad de crear y calificar problemas individuales, incluyendo la automatización de casos de prueba, la calificación y el reporte del estado del envío en tiempo real. Además, se busca que puedan crear concursos con varios problemas, gestionar estos concursos, publicarlos y controlar quién puede acceder a ellos. También se incluye la posibilidad de publicar contenido relacionado con la programación competitiva, como blogs.

## Indice
- Capítulo I Introducción
- Capítulo II.-Justificación
- Capítulo III.-Características del juez
- Capítulo IV.- Infraestructura
- Capítulo V.- Frontend
- Capítulo VI.- Dev ops y CI
- Capítulo VII.- Documentación
- Capítulo VIII.- Conclusiones

## Resumen de cada capitulo
### Capítulo I Introducción
En este capítulo se introduce el concepto de un juez en línea, programación competitiva y cual es el proposito del juez.

### Capítulo II Justificación
Se detalla la necesidad de un nuevo juez en línea, destacando las limitaciones y deficiencias de los sistemas existentes. Se explica por qué se elige Rust como lenguaje de programación, señalando sus ventajas en términos de rendimiento y seguridad. También se justifica la elección de React y TypeScript para el frontend eficiencia en el desarrollo de interfaces de usuario interactivas. Además, se menciona por qué se elige Postgres como base de datos, destacando su capacidad para manejar grandes volúmenes de datos de manera eficiente. 

### Capítulo III  Características del juez
Este capítulo enumera todas las funcionalidades ofrecidas por el juez en línea, presentándolas de manera clara y concisa como un manual de usuario. Cada característica se describe en términos de su utilidad y modo de operación, proporcionando ejemplos graficos cuando sea necesario. Se incluyen tanto las funciones básicas, como el registro de usuarios y el envío de soluciones, como las funciones avanzadas, la gestión de concursos y la creación de problemas.

### Capítulo IV Infraestructura
En este capítulo se explica a fondo toda los servicios internos del juez. Se detalla la tecnología utilizada, incluyendo Axum, RabbitMQ y Redis . Además, se profundiza en la base de datos, presentando el diagrama entidad-relación y las migraciones. Se describen también aspectos clave del servidor web, como la autenticación de usuarios, el uso de web sockets, medidas de seguridad implementadas, el servidor SMTP y aspectos de rendimiento como el server side rendering. El capítulo también aborda el evaluador, detallando su arquitectura, diseño del código, medidas de seguridad implementadas y optimización. Finalmente, se presenta el sistema de envíos y concursos, explicando el flujo de un envío, el funcionamiento de un concurso y el sistema de notificaciones en tiempo real. Por ultimo se detalla los aspectos de la administración del juez, incluyendo el modelo de roles y grupos.

### Capítulo V Frontend
En este capítulo se detalla la estructura del código del frontend, explicando cómo se organiza para garantizar la mantenibilidad y escalabilidad del sistema. Se presenta el stack tecnológico utilizado, que incluye React, Next.js y TypeScript, destacando las ventajas que cada uno aporta al desarrollo de la interfaz de usuario. Se profundiza en el uso de TypeScript y cómo se aprovecha junto a Rust para mantener la coherencia en el intercambio de peticiones HTTP. Además, se aborda el proceso de diseño de la interfaz de usuario utilizando Figma, detallando las reglas de diseño que sigue la interfaz del juez.

### Capítulo VI DevOps
En este capítulo se describe el proceso de dockerización del proyecto, que consiste en empaquetar cada microservicio del juez en un contenedor Docker para facilitar su implementación y gestión. Se aborda la cross compilacion entres sistemas (ARM y x86). Se explica la comunicación entre microservicios, que se realiza a través de solicitudes HTTP y con el protocolo bincode. También se describe la seguridad de las instancias y la red compartida del juez.

### Capítulo VII Documentación
En este capítulo se describe el proceso de documentación en Rust utilizando la auto documentación proporcionada por el lenguaje. Se explica cómo se generan y organizan automáticamente los documentos. Además, se detalla el proceso de implementación de la documentación en GitHub, explicando cómo se realiza el despliegue para que esté disponible para los usuarios finales.

### Capítulo VIII Conclusiones
El capítulo de conclusiones destaca los principales logros y desafíos enfrentados durante el desarrollo del juez. Se resalta la importancia de la elección de tecnologías como Rust, React, TypeScript y Postgres para elp royecto. Se hace énfasis en la importancia de una documentación detallada y accesible, así como en la atención al diseño y la usabilidad en todas las etapas del desarrollo. También se mencionan  áreas de mejora y sugerencias para futuras iteraciones del proyecto.

