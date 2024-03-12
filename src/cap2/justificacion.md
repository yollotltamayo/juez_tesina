# Justificacion

1. **Rust**: Es un lenguaje de programación moderno y seguro que ofrece un rendimiento comparable a **C++** sin descuidar los aspectos de la seguridad de memoria. Su sintaxis es expresiva y ergonomica, lo que lo hace ideal para una amplia gama de aplicaciones, desde sistemas operativos hasta aplicaciones web.
Para el caso del juez en linea se selecciono Rust en base a los siguientes requerimientos:
    1. **Frugalidad**: Un juez en linea hace bastantes tareas que pueden calificarse como computacion intensiva, este proyecto no es la excepcion. Es por eso que muchos aspectos del diseno estan enfocados a reducir costos de computo o de almacenamiento. A diferencia de Go, otro lenguaje considerado para este proyecto, Rust [https://doc.rust-lang.org/book/ch04-00-understanding-ownership.html] no tiene un recolector de basura, lo que lo hace más eficiente en el consumo de memoria, sin descuidar la seguridad en el manejo de esta [https://security.googleblog.com/2022/12/memory-safe-languages-in-android-13.html].
    2. **Manejo de errores**: En un sistema que se enfoca en reportar diferentes estatus a diferentes usuarios en tiempo real ( el sistema de envios), es imperativo saber en que punto del sistema hay un error y reportarlo correctamente al usuario. 
    Mientras que en otros lenguajes como JavaScript, Java o Python se manejan excepciones, en Rust los errores son considerados como valores y no como excepciones.El lenguaje tiene mecanismos nativos (Tipo de dato algebraico (Algebraic data type) ) que permite tratar con los errores desde el principio, vease el siguiente ejemplo:
        ```javascript
         // Javascript
         async function fetchData(url) {
             const response = await fetch(url);
             const data = await response.json();
             return data;
         }
        ```
        En Javascript hacer una request es sencillo, pero `fetch()` o `response.json()` pueden fallar inadvertidamente, mientras que en Rust, la peticion regresa un `Result` que indica si la accion fallo o no:
        ```rust
        // Rust
        async fn fetch_data(url: &str) -> Result<String, Error> {
            let response: Response = reqwest::get(url).await?;
            let body: Result<String, Error> = response.text().await;
            match body {
                Ok(result) => Ok(result),
                Err(e) => Err(e),
            }
        }
        ```
2. **React**: Es una biblioteca de JavaScript de código abierto utilizada para construir interfaces de usuario interactivas y reutilizables. Desarrollada por Facebook, React se basa en un enfoque de programación declarativa que hace que la creación de componentes de interfaz de usuario sea más sencilla y eficiente. Con React es posible la creación de componentes que gestionan su propio estado y se actualizan automáticamente cuando cambian los datos.
3. **Next.js**: Es un framework de React de código abierto que se utiliza para construir aplicaciones web modernas y rápidas. Next.js proporciona funcionalidades adicionales que facilitan el desarrollo de aplicaciones web, como el enrutamiento basado en archivos, la generación de sitios estáticos y la capacidad de renderizar tanto en el servidor como en el cliente. 
----------------------------------
