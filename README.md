# **¿Qué es SQL y cómo funciona una base de datos relacional?**

### ¿Qué es SQL? 
(Structured Query Language)

---
 > 🗣 es un **lenguaje de consulta estructurado**. 
---


🖐Atención: No es un lenguaje de programación como JavaScript.


Es un **lenguaje de consulta**  diseñado específicamente **para gestionar y consultar bases de datos relacionales**. 

Bien, no demos nada por sentado.
### ¿Sabemos qué es una base de datos?

Es un sistema para almacenar datos y conectarlos entre sí en una unidad lógica,  un conjunto de datos estructurados que pertenecen a un mismo contexto.

> 📖Si yo tengo un cuaderno donde apunto todos los pedidos que hacen mis clientes, mi cuaderno es una base de datos.

Volviendo al punto en el que estabamos antes, hablando de SQL como un **lenguaje de consulta**  diseñado específicamente **para gestionar y consultar bases de datos relacionales**. 
Vamos hacer hincapié en la parte de bases de datos relacionales, porqué es "la base" de las bases de datos SQL 👇

Una **base de datos relacional** organiza la información en **tablas**.
----
Cada tabla tiene:

- **Filas (registros):** cada fila representa un dato individual.
- **Columnas (atributos):** cada columna representa una característica de esos datos.

| id | name | email |
| --- | --- | --- |
| 1 | Juana | juana@email.com |
| 2 |  Roberto| roberto@email.com|

 La tabla del ejemplo tiene 2 registros, 3 columnas:
 
- **Filas:**  `1, Juan, juana@email.com`, `2, Roberto, roberto@email.com`
- **Columnas :** `id`, `nombre`, `email`

### ¿Cómo funcionan las relaciones?

---
>🗣 las **relaciones entre tablas**, ayudan a `evitar la duplicación de datos.`
---

Para relacionar tablas, se usan **identificadores únicos** llamados 🗝`id`🗝.

Veamos un ejemplo:

Una tabla de usuarios tiene un `id` único por cada persona.
Una tabla de pedidos puede incluir un campo `user_id` que referencia al `id` de un usuario.

` tabla users 👇 `
| id | name | email |
| --- | --- | --- |
| 1 | Juana | juana@email.com |
| 2 |  Roberto| roberto@email.com|

` tabla pedidos 👇 `
|id | user_id | article | number |
| --- | --- | --- | --- |
| 1 | 2 | patatas-small | 2 |
| 2 | 2 | pizza-jamon-piña| 1 |

Esto permite conectar información entre tablas sin repetir datos. Es decir, los pedidos se relacionan con los usuarios mediante su `id`, en lugar de volver a escribir el nombre o correo del usuario en cada pedido.

En el ejemplo podemos ver como el usuario 2, es decir, Roberto, es el único que ha realizado pedidos.

---

### ¿Qué consultas puedo hacer?

Con SQL puedes hacer cosas como

- `INSERT`: agregar nuevos registros. CREATE
- `SELECT`: consultar datos. READ
- `UPDATE`: modificar datos existentes. UPDATE
- `DELETE`: eliminar registros. DELETE
- `CREATE TABLE`, `ALTER`, `DROP`: modificar la estructura de la base de datos.

Aquí acaba de aparecer el famoso CRUD, que son las acciones que se pueden hacer sobre los datos
Crearlos, Leerlos, Actualiarlos y eliminarlos.

Bien, llegados a este punto, no podemos ponernos a escribir así de la nada directamente SQL.
Necesitas un SGBD (Sistema de Gestión de Bases de Datos) como PostgreSQL, MySQL, SQLite, etc.
te estarás preguntandoo ¿porqué?

SQL es un lenguaje, no un programa o sistema que pueda ejecutar instrucciones por sí mismo.

[¿Cómo trabajar con MySQL?](./MySQL.md)
[¿Cómo trabajar con PostgreSQL?](./PostgreSQL.md)



### ❌ ¿Qué es NoSQL y en qué se diferencia?

**NoSQL** se refiere a bases de datos **no relacionales**. En lugar de tablas, organizan los datos en:

- **Documentos (como JSON)**
- **Colecciones**
- **Claves y valores**

A diferencia de SQL:

No usan relaciones entre entidades.

**Duplican datos** (por ejemplo, la información del usuario puede aparecer en cada documento de pedido).

Son más flexibles en estructura, pero menos consistentes si no se gestionan bien.

---

## Ventajas y desventajas

| Tipo | Ventajas | Desventajas |
| --- | --- | --- |
| **Relacional (SQL)** | Organización clara, sin datos repetidos | Requiere múltiples consultas para reunir datos |
| **No Relacional** | Rápida y flexible para ciertos escenarios | Duplica información, sin relaciones reales |

---



- **SQL** es un lenguaje estándar para gestionar **bases de datos relacionales**.
- Las bases de datos relacionales usan **tablas, columnas e IDs** para mantener los datos organizados y conectados.
- Las bases de datos **NoSQL** usan documentos, no hacen relaciones reales y tienden a duplicar datos.
- SQL es ideal cuando se necesita integridad y organización en los datos.
