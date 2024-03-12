# Tech Stack

El tech stack o conjunto de tecnologías, se refiere a la combinación de tecnologías y herramientas utilizadas para construir y ejecutar una aplicación.

 En esta seccion, se explora en detalle el tech stack seleccionado para el proyecto, destacando las razones detrás de cada elección.

1. **Axum**:Axum: Es un framework web construido en Rust, diseñado para ser fácil de usar y altamente escalable. Está basado en el framework HTTP hyper[^hyper] y en el sistema de componentes HTTP tower[^tower], lo que lo hace robusto y cuenta con una amplia comunidad. En la práctica, ofrece un alto grado de personalización. Dado que está basado en tower, varias funcionalidades como el tracing, rate limiting, deserialización y manejo de peticiones HTTP están automáticamente incluidas.
2. **RabbitMq**: Es un software de mensajería de código abierto que implementa el protocolo de mensajería avanzada (AMQP). Se utiliza para enviar y recibir mensajes entre microservicios. RabbitMQ actúa como intermediario de mensajes, recibiendo mensajes de productores (aplicaciones que envían mensajes) y entregándolos a consumidores (aplicaciones que reciben mensajes). Es especialmente útil en arquitecturas de aplicaciones distribuidas y microservicios, donde se necesita una comunicación eficiente y flexible entre componentes. En el caso de el juez, RabbitMQ comunica el servidor web con los evaluadores, los protocolo de intercambio nativos de RabbitMQ, facilitan la concurrencia de los sistemas, de esta forma es mas sencillo paralelizar algunas partes de los sistemas.
3. **PostgreSQL**: Es un sistema de gestión de bases de datos relacional de código abierto y potente. Se destaca por su capacidad para manejar cargas de trabajo complejas y grandes volúmenes de datos. A diferencia de **MySQL**, Su capacidad de lidiar con tipos de datos complejos ( `bits`, `jsonb`, `bytes`) y la facildad para agregar extensiones como `uuid-ossp` para generar `uuid` la hacen la opcion ideal para el juez.
4. **Redis**: Es un motor de base de datos en memoria, basado en el almacenamiento en tablas de hashes (clave/valor) pero que opcionalmente puede ser usada como una base de datos durable o persistente.

[^hyper]: https://hyper.rs/
[^tower]: https://docs.rs/tower/latest/tower/
