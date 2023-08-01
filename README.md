# MONGO DB

Es un sistema de bases de datos NoSQL, **Orientado a documentos** y de código abierto que guarda estructuras de datos JSON con un esquema dinámico.

## ¿Qué es mongoDB?

Es una base de datos de documentos con la escabilidad (**para el big data**) y flexibilidad que desea con la consulta e indexación que necesitas.

### ¿Que es NoSQL?
Es un termino que se le da a un conjunto de bases de datos que se diferencian en gran parte a las bases de datos convencionales. Son las que no usan SQL. 

Las bases NoSQL están diseñadas para modelos de datos específicos y tienen esquemas flexibles para crear aplicaciones modernas. Son fáciles de desarrollar, tienen una gran funcionalidad y un rendimiento a escala.

Las bases de datos NoSQL guardan y consulta datos fuera de las estructuras tradicionales SQL.

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

## Instalación de MongoDB

Inicialmente hay que instalar mongoDB, por lo que se debe dirigir a la página oficial de [mongoDB](https://www.mongodb.com/docs/manual/installation/) y descargará el archivo para su sistema operativo.

* Community Edition son las versiones gratuitas soportadas por la comunidad. No tienen respondo de mongoDB.
* Enterprise Edition o ediciones de empresas, son las pagas las cuales son soportadas por mongoDB.

Para efectos prácticos en este caso se realizará la instalación únicamente para un sistema operativo linux con distribución ubuntu. 

1. Vamos a importar la clave pública utilizada por el sistema de gestión de paquetes 

```bash
sudo apt-get install gnupg curl
```

2. Ejecute el siguiente comando para importar la clave GPG pública de MongoDB desde
```bash
curl -fsSL https://pgp.mongodb.com/server-6.0.asc | \
   sudo gpg -o /usr/share/keyrings/mongodb-server-6.0.gpg \
   --dearmor
```

3. Crear un archivo de lista para MongoDB
```bash
sudo touch /etc/apt/sources.list.d/mongodb-org-6.0.list
```

*Si no está seguro de qué versión de Ubuntu está ejecutando el host, abra una terminal o shell en el host y ejecute lsb_release -dc.*

4. En la documentación oficial se pueden ingresar disferentes versiones. Seleccione la que sea apropiada de su versión de ubuntu.

En este caso está el ejemplo de una distribución ubuntu 18.04 ingrese el siguiente comando:

```bash
echo "deb [ arch=amd64,arm64 signed-by=/usr/share/keyrings/mongodb-server-6.0.gpg ] https://repo.mongodb.org/apt/ubuntu jammy/mongodb-org/6.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-6.0.list
```

5. Ingrese el siguiente comando para recargar los paquetes de las bases de datos locales 
```bash
sudo apt-get update
```
6. Para instalar los paquetes de mongoDB. Hay opción de instalar la versión estable o alguna vesión específica de mongoDB, para el caso actual se utilizará la versión estable:

```bash
sudo apt-get install -y mongodb-org
```

Cabe aclarar que los pasos mencionados en esta fase son específicos de ubuntu 18.04 y que si se desea hacer la instalación con otro sistema operativo o con otra distribución es importante que se observen los pasos de la documentación oficial.

### Ejecutar MongoDB en linux - ubuntu

1. Para iniciar MongoDB es importante abrir una terminar y escribir el siguiente comando:

```bash
sudo systemctl start mongod
```

Si por algún motivo se llega a observar un error cuando se inicia mongo

```bash
sudo systemctl daemon-reload
```

### Otros comandos útiles para MongoDB

* Si deseas observar el estado de mongoDB en tu computadora ejecuta el siguiente comando:

```bash
sudo systemctl status mongod
```

Sin embargo, por defecto mongodb se va a apagar cada vez que reinicias el computador, por lo que opcionalmente puedes asegurarte de que MongoDB comenzará después de un reinicio del sistema emitiendo el siguiente comando:

```bash
sudo systemctl enable mongod
```

* Si deseamos detener los servicios de mongoDB solo debemos ingresar el siguiente comando: 

```bash
sudo systemctl stop mongod
```

* Si lo que necesitamos es reiniciar mongoDB escribiremps:

```bash
sudo systemctl restart mongod
```

* Si llegamos a necesitar desinstalar mongodb, detenemos el servicio de mongo y escribimos los siguientes comandos: 

```bash
sudo apt-get purge mongodb-org*
```
```bash
sudo rm -r /var/log/mongodb
sudo rm -r /var/lib/mongodb
```
De esta forma no tendremos a mongo en nuestro sistema.


## MongoDB con COMPASS

### Instalación de MongoDB Compass

Antes de instalar MongoDBCompass verifique que tenga mongoDB en su sistema:

```bash
mongod --version
```

Una vez confime que tiene mongo en su sistema diríjase a la documentación oficial de MongoDB donde encontrará información de la instalación de COMPASS (https://www.mongodb.com/try/download/compass)

Seleccione la versión que desee (en preferencia la versión estable), la plataforma y el tipo del archivo que va a instalar. 

Una vez descargado para el caso de la distribución Ubuntu, el archivo a descarga sería un .deb. Para ejecutar este archivo se tiene que escribir el siguiente comando en la terminal (en la ruta donde se encuentre el archivo. Lo más lógico sería que fuera en /Downloads):

```bash
chmod +x mongodb-compass-community-*-linux-x64*.AppImage
```

Y para ejecutar MongoDB Compass. 

```bash
./mongodb-compass-community-*-linux-x64*.AppImage
```

### Extensiones útiles para el desarrollo

Si estás trabajando con Visual studio code, existe una extensión bastante útil llamada mongoDB. 

Con ella puedes conectarte a cloud Mongo con Compass y genarar un archivo *.mongodb* para escribir consultas de mongo desde el editor de código.




## Mongoose

Permite un desarrollo rápido y simple de mongoDB y tener interacciones con la base de datos.

Es una biblioteca de datos de objetos (ODM) para MongoDB y Node.js para tener un mayor nivel de abstracción. 

* Mongoose no solo permite conectarme a la base de datos si no que también permite modelar la base de datos.  