# Estructura del codigo

## Repositorios

El codigo esta _hosteado_ en github [link](https://github.com/Club-de-Algoritmia-Acatlan-GUAPA/juezGUAPA) y tiene la siguiente estructura:

<!---
JuezGUAPA
  backend
   @evaluator
   @primitypes
   @web_server
   Cargo.lock
   Cargo.toml
   README.md
   rustfmt.toml
   .gitignore
   src
  @frontend
  .gitignore
  .gitmodules
  README.md
-->

```
JuezGUAPA
 ├──backend
 │   ├──@evaluator
 │   ├──@primitypes
 │   ├──@web_server
 │   ├──Cargo.lock
 │   ├──Cargo.toml
 │   ├──README.md
 │   ├──rustfmt.toml
 │   ├──.gitignore
 │   └──src
 ├──@frontend
 ├──.gitignore
 ├──.gitmodules
 └──README.md
```

El directorio `backend` contiene toda la infraestructura del juez, valores que tienen `@` como prefijo son sub repositorios, en este caso `evaluator`, `primitypes`, `web_server` son los servicios que conforman al juez y `frontend` hace referencia a su nombre, cada uno tiene su propio repositorio:

- `web_server`: [link](https://github.com/Club-de-Algoritmia-Acatlan-GUAPA/web_server/tree/6e2871c020a60f8c16df250cfe366a66492af8cb)
- `evaluator`: [link](https://github.com/Club-de-Algoritmia-Acatlan-GUAPA/evaluator/tree/b6cd24994367db9108575410b4f575f3f46e8c97)
- `primitypes`: [link](https://github.com/Club-de-Algoritmia-Acatlan-GUAPA/primitypes/tree/3dc8afbb3c8846a3106e6856c8bb09a15c7b9169)
- `frontend`: [link](https://github.com/Club-de-Algoritmia-Acatlan-GUAPA/judge_client/tree/0dabfe0f822985eb83e746eb2ad55ce117728561)

En esta seccion solo se expone la estructura del _backend_, la estructura del _frontend_ se explica en su propio capitulo.

## Workspaces

Como todo los servicios estan escritos en _Rust_, administrar los distinos repositorios como uno solo es bastante conveniente. Por lo tanto se hace uso de los `worskpaces`, una caracteristica del lenguaje que permite compartir caracteristicas entre `crates`[^crate].

El archivo `juezGUAPA/backend/Cargo.toml` contiene la informacion sobre nuestro `workspace`, esto permite que los `crates` puedan compartir metodos y constantes.

```toml
[workspace]
members = [
    "web_server",
    "primitypes",
    "evaluator"
]
```

## Formateo de codigo

Para mantener el formateo de codigo consistente en todos los `crates` se hace uso del archvio `rustfmt.toml`, este archivo nos perimte indicar las reglas de formato que el codigo debe seguir.

```toml
imports_granularity = "Crate"
group_imports = "StdExternalCrate"
reorder_impl_items = true
wrap_comments = true
match_block_trailing_comma = true
```
## Primitypes

Rust es un lenguaje fuertemente tipado, eso significa que los tipos de todas las variables deben ser conocidos en tiempo de compilacion. Los tipos de dato que usa el juez son primitivos ( Cadenas, Enteros, Flotantes, etc...) y compuestos ( una combinacion de tipos primitivos). Los servicios del juez muchas veces usan el mismo tipo de dato para comunicarse, por ejemplo considere el tipo de dato que se usa para representar el envio de un usuario, el tipo `Submission` :

```rust
pub struct Submission {
    pub problem_id: ProblemID,
    pub user_id: Uuid,
    pub contest_id: Option<ContestId>,
    pub language: Language,
    pub code: Vec<u8>,
    pub id: SubmissionID,
}
```

El servidor web usa este tipo para poder registrarlo en el encolador, las instancias de evaluadores lo usan para pode consumir de la cola de envios. Este escenario de compartir tipos entre `crates` sucede a menudo. Para evitar repetir cada tipo de dato en cada servicio, se opto por crear un repositorio que contenga todos los tipos de datos, de esta forma todos los `crates` pueden consumir los tipos de dato de una sola fuente de verdad.

Este repositorio tiene el nombre de `primitypes` (**PRIMI**tive **TYPES**).

[^crate]: Un crate es un sinónimo para 'biblioteca' o 'paquete' en otros lenguajes.
