# MONGO DB

Es un sistema de bases de datos NoSQL, **Orientado a documentos** y de código abierto. 

* No guarda datos en tablas

Mongo BD guarda estructuras de datos JSON con un esquema dinámico.

## ¿Qué es mongoDB?

Es una base de datos de documentos con la escabilidad (**para el big data**) y flexibilidad que desea con la consulta e indexación que necesitas.

### Características: 

* **Basado en documentos:** Almacena datos en documentos, en estructuras de datos pares de valor.
* **Escalable:** Fácil distribución de datos entre máquinas a medida que crecen los usuarios y los datos.
* **Flexible:** No requiere un esquema de datos del documento.
* **Rendimiento:** Modelos de datos integrados, indexación, fragmentación, códigos flexibles.



La base de datos contiene una serie de colecciones (tablas) y cada colección tiene un número de documentos (filas).

## Operaciones CRUD

Crean, leen, actualizan y eliminan documentos

* **CREAR OPERACIONES:** las operaciones de creación o inserción agregan nuevos documentos a una colección. 
  * Si la colección no existe, las operaciones de creación también crea la colección.
  * Se puede insertar uno o varios documentos en una sola operación.

* **LEER OPERACIONES:** Recuperan documentos de una colección, es decir, consultar una colección de documentos.
  * Se pueden especificar criterios o filtros para identificar los documentos a devolver.
* **ACTUALIZAR OPERACIONES:** Modifican los documentos existentes en una colección. 
  * Puede especificar si se actualiza un solo documento o varios en una sola operación.
  * Además, se pueden crear filtros para dicha actualización
* **ELIMINAR OPERACIONES:** Eliminan documentos de una colección. 
  * Puede eliminar un solo documento o varios en una sola operación
  * Se le pueden crear filtros o criterios para que identifiquen ciertos documentos que serán eliminados.

* * 

## Funciones CRUD

La sintaxis para el crud es la siguiente:

```
Nombre_basedatos.nombre_colección.funcionCRUD
```

#### ¿Qué es un JSON?

Sus siglas en ingles "javascript  object notation". Es un formato para guardar e intercambiar información que cualquier persona pueda leer. Lo más importante de este tipo de dato es que su estructura es clave valor. Las claves deben ser strings y los valores pueden tener cualquier tipo de dato de js.



## Estructura del documento

**BSON:** Formato de datos que utiliza MongoDB para almacenar datos. Muy parecidos a los JSON.

```json
{
    "_id": Object('343423424'),
    "title": "Something here",
    "author": "Elonk musk",
    "length": 3280,
    "published": true,
    "tags": ["MongoDB", "space", "ev"],
    "comments": [
        {"author": "Jonas", "text": "Amaizing"},
        {"author": "Pepo", "text": "super"},
        {"author": "PIG", "text": "Increbible"}
    ]
}
```

En mongoDB existe algo llamado **Incrustación y desnormalización** esto permite la inclusión de datos relacionados en un solo documento. 

* Esto permite aplicaciones más rápidas ya que el acceso a los datos es más rápido.
* En base al ejemplo anterior la tabla comments en SQL debería ser otra tabla o existir más normalización en la basa de datos.

Sin embargo no siempre es la mejor solución.