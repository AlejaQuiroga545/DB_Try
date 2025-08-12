# DB_Try

**Docs** - Documentación - Modelo relacional.jpg / script_db.js (base de datos de workbench
**Sever** - Toda la lógica del Backend

- index.js | Lógica de carga, endpoints, conexión db
- conexión_db.js | Conectar la db (instalo todos los paquetes con npm i)

**Librerias indispensables**
mysql2 - Me permite crear la conexión entre la db y el conexión_db.js
npm install mysql2

**Pool**| Sistema que me permite crear una piscina de conexiones (abre la conexión, trae lo que necesito y cierra la conexión)

import mysql2 from "mysql2/promise" para poder usarlo (promise para trabajar con asincronismo)
export const pool = mysql.createPool ({creo un objeto})


Para ejecutarlo (conectar la db) es node server/conexión_db.js

**Pasamos el archivo (excel) a JS a través de CSV**
- Creamos entidades fuertes primero (las que no tienen FK)
- Se guarda en la carpeta de server, dentro de una carpeta llamada data

![Imagen de WhatsApp 2025-08-11 a las 21 14 54_088b92c9](https://github.com/user-attachments/assets/c58a0089-741f-4e58-819d-04c792a66b68)
**Dentro de server creo una carpeta llamada Seeders**
Dentro esta:
- load_usuarios (se encargará de cargar los usuarios a la db)
- run_seeders (se encargará de llamar a los load)

**fs** y **path** ya están

toca instalar **csv-parser** - Librería que se encarga de leer los archivos en formato csv
npm install csv-parser
e importamos el pool | import {pool} from "../conexión_db.js" siempre debe ir el js para que funcione en la conexión

con el **path** indico la ruta donde esta nuestro csv, y luego creamos un array vacío [ ] porque es donde se van a almacenar los datos


![Imagen de WhatsApp 2025-08-11 a las 21 14 54_dc9b23f7](https://github.com/user-attachments/assets/473a6843-5af1-4e30-9e00-1f0e73296b94)
![Imagen de WhatsApp 2025-08-11 a las 21 15 07_65727380](https://github.com/user-attachments/assets/e09175da-c1fa-48a5-92e5-2c0a3915755b)
Leeme una rchivo y pasalo a .csv

**on data** - que quiero que haga con los datos
**on end** - que quiero que haga después de que tenga los datos
**on error** - error al leer los archivos

![Imagen de WhatsApp 2025-08-11 a las 21 17 39_dac6d09b](https://github.com/user-attachments/assets/d9d42f58-5334-477c-b84f-bb01432ddcff)
Le estoy indicando que vaya **fila por fila**

![Imagen de WhatsApp 2025-08-11 a las 21 18 17_88646da4](https://github.com/user-attachments/assets/8e210c4d-c0a8-41ee-9e25-7cb5c60ccfde)
Método push para insertar los datos uno por uno, fila por fila

![Imagen de WhatsApp 2025-08-11 a las 21 24 14_69ef7182](https://github.com/user-attachments/assets/4e1d1a85-e6c9-45da-9e33-457ce1e25507)
En el END, quiero crear un sql  través de un **INSTER INTO** para ingresar nuevos registros, y en **VALUES** solo le pongo un signo de pregunta **?**

![Imagen de WhatsApp 2025-08-11 a las 21 25 27_de9fa746](https://github.com/user-attachments/assets/90131d7f-ca1f-4c10-92b2-bee6f0ab0f6e)
Aquí cargamos los usuarios a la bd

Para ejecutarlo es: node server/seeders/run seeders.js

![Imagen de WhatsApp 2025-08-11 a las 21 52 21_0546d8da](https://github.com/user-attachments/assets/57978aa5-93ca-4e58-b962-6f26b2413461)
**index.js** | Donde creo los endpoints (backends)

- Instalar librería: npm install express | se hace para traer nuestra info y mostrarla al mundo
npm i

importo la librería y creo un const llamada **app**
app.use(express,json()) - Perparate porque la info va a llegar en formato json

en mis peticiones GET pongo req(request) para que entre la info, y res(response) para que salga la info

Después de que hago mi CRUD, levanto mi servidor
node server/index.js
Para ver los cambios en el server debo limpiarlo y volverlo a subir

![Imagen de WhatsApp 2025-08-11 a las 21 52 22_d74b687e](https://github.com/user-attachments/assets/35289ffa-757d-4bce-8d66-5d72c1922986)
**CRUD**

- GET | Traer todos los datos
- POST | Crear un dato
- PUT | Actualizar un dato existente
- DELETE | Eliminar un dato existente

- ![Imagen de WhatsApp 2025-08-11 a las 22 00 16_8487cb3f](https://github.com/user-attachments/assets/0f77e411-8f42-4936-ac63-0467910c4345)
Construyo la query con lo que necesito.

Uso JOIN ON(donde) para llamar otras tablas, y en mi SLEECT le muestro al usuario lo que yo decida, con los títulos que quiera a través del AS

![Imagen de WhatsApp 2025-08-11 a las 22 03 10_89b6b577](https://github.com/user-attachments/assets/2dc20ba9-0f2a-42cd-ac17-5d6f1fb77ae6)
Dentro de mi const query debo usar backtips para que no se rompa le código

![Imagen de WhatsApp 2025-08-11 a las 22 03 10_d7c0753f](https://github.com/user-attachments/assets/cca4a975-1411-494c-9732-835d4e80069a)
![Imagen de WhatsApp 2025-08-11 a las 22 07 26_f0aee6ad](https://github.com/user-attachments/assets/33bd25b5-fe6e-469b-a192-8da0d8c43da0)
Endpoint de prestamo

Colección en **POSTMAN**, creo una nueva carpeta con el nombre de mi bd, un nuevo archivo llamado prestamos, en GET le pongo la url de mi servidor http://localhost:3000/prestamos

![Imagen de WhatsApp 2025-08-11 a las 22 14 58_29a9b489](https://github.com/user-attachments/assets/0050b9ac-f9fa-4860-bcb9-7058f294e414)
![Imagen de WhatsApp 2025-08-11 a las 22 25 26_7498191c](https://github.com/user-attachments/assets/b14e3a67-8aa0-4d39-a546-84c2af68239f)
Método POST - Crear

- En POSTMAN debo tener mi biblioteca donde tenga todo mi CRUD y los endpoints (consultas) especiales
- Levantar front  - npm run dev
- Levantar back | node server/index.js
- Sacar variables de entorno del script, meterlas a un .env
En conexión_db.js poner: npm install dotenv, y allí pegar las variables de entorno
---
# Better way

## Backend de Sistema de Gestión de Biblioteca
Este documento detalla la estructura y el funcionamiento del backend monolítico para un sistema de gestión de biblioteca. El backend está desarrollado en Node.js con Express, y utiliza MySQL como base de datos.

### Estructura del Proyecto
La lógica del backend se encuentra dentro de la carpeta server/.

```Bash

biblioteca/
│
├── server/ # Backend
│   ├── data/ # Archivos CSV para la carga inicial de datos
│   ├── seeders/ # Scripts para cargar datos en la base de datos
│   │   ├── load_usuarios.js
│   │   └── run_seeders.js
│   ├── conexion_db.js # Módulo para la conexión a la base de datos
│   └── index.js # Lógica principal, endpoints y servidor
│
├── .env # Variables de entorno
└── ...
```
---
### Tecnologías y Librerías
El proyecto utiliza las siguientes librerías de Node.js:

- **Express.js:** Framework para construir la API y gestionar las rutas (endpoints).
- **mysql2:** Driver para conectar Node.js con la base de datos MySQL. Se utiliza en modo promise para manejar operaciones asíncronas de manera más sencilla.
- **csv-parser:** Librería para leer y procesar archivos en formato CSV. Es fundamental para la carga de datos inicial.
- **dotenv:** Permite gestionar las variables de entorno para la configuración de la base de datos.
---
### Configuración y Dependencias
Antes de ejecutar el backend, es necesario instalar las dependencias y configurar el entorno.

**Instalar librerías:**

```Bash

npm install express mysql2 csv-parser dotenv
Configurar la base de datos:
Crea un archivo .env en la raíz del proyecto para definir las variables de entorno de la conexión.

Fragmento de código

DB_HOST=localhost
DB_USER=root
DB_PASSWORD=password
DB_NAME=nombre_de_tu_bd
DB_PORT=3306
```
---
### Lógica del Backend
**Conexión a la Base de Datos**
El archivo server/conexion_db.js se encarga de establecer la conexión con MySQL.

Se utiliza el concepto de pool de conexiones (mysql.createPool) para gestionar de manera eficiente las peticiones a la base de datos, abriendo y cerrando conexiones automáticamente.

Las variables de entorno definidas en el archivo .env se cargan y se utilizan para esta conexión.

**Carga Inicial de Datos (Seeders)**
Para poblar la base de datos con datos iniciales, se utilizan los scripts en la carpeta server/seeders.

**Archivos CSV:** Los archivos de datos, como los de usuarios, se guardan en la carpeta server/data.

**Scripts de carga (load_*.js):** Estos scripts leen los archivos CSV con csv-parser y utilizan el pool de conexiones para insertar los datos en las tablas correspondientes de la base de datos. Se recomienda cargar primero las tablas sin claves foráneas (entidades fuertes).

**Ejecución de Seeders:** El archivo run_seeders.js coordina la ejecución de todos los scripts de carga. Para ejecutarlo, utiliza el siguiente comando:

```Bash

node server/seeders/run_seeders.js
```
---
### Endpoints (CRUD y Consultas)
El archivo principal server/index.js define la lógica de la API, creando los endpoints para gestionar los recursos (libros, usuarios, préstamos, etc.).

Se utiliza app.use(express.json()) para que la aplicación pueda interpretar los cuerpos de las peticiones en formato JSON.

El CRUD (Crear, Leer, Actualizar, Eliminar) se implementa de la siguiente manera:

**GET: Para traer datos.***
app.get('/ruta'): Trae todos los datos.
app.get('/ruta/:id'): Trae un dato específico por su ID.

**POST:** Para crear un nuevo dato.

**PUT:** Para actualizar un dato existente.

**DELETE:** Para eliminar un dato existente.

Además del CRUD básico, se pueden crear consultas más complejas utilizando JOIN para combinar datos de múltiples tablas y AS para renombrar columnas en las respuestas.

---
### Puesta en Marcha del Servidor
Para levantar el servidor del backend, ejecuta:

```Bash

node server/index.js
```

Para ver los cambios en el servidor, es necesario detenerlo (Ctrl + C) y volver a ejecutar el comando.

Se recomienda usar herramientas como Postman para probar los diferentes endpoints y verificar que el backend funciona correctamente. Puedes crear una colección para organizar todas las peticiones.
