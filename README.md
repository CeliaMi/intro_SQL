# **¿Qué es SQL y cómo funciona una base de datos relacional?**

### ¿Qué es SQL? 
(Structured Query Language)

---
 > 🗣 es un **lenguaje de consulta estructurado**. 
---


🖐Atención: No es un lenguaje de programación como JavaScript.


Es un **lenguaje de consulta**  diseñado específicamente **para gestionar y consultar bases de datos relacionales**. 

Vamos hacer hincapié en la parte de bases de datos relacionales, porqué es "la base" de las bases de datos SQL 👇

Una **base de datos relacional** organiza la información en **tablas**.
----
Cada tabla tiene:

- **Filas (registros):** cada fila representa un dato individual.
- **Columnas (atributos):** cada columna representa una característica de esos datos.

Por ejemplo, una tabla de usuarios puede tener columnas como `id`, `nombre`, y `email`.

>
>🗣 las **relaciones entre tablas**, ayudan a `evitar la duplicación de datos.`
>


### ¿Cómo funcionan las relaciones?

Para relacionar tablas, se usan **identificadores únicos** llamados `id`.

Por ejemplo:

- Una tabla de usuarios tiene un `id` único por cada persona.
- Una tabla de pedidos puede incluir un campo `usuario_id` que referencia al `id` de un usuario.

Esto permite conectar información entre tablas sin repetir datos. Es decir, los pedidos se relacionan con los usuarios mediante su `id`, en lugar de volver a escribir el nombre o correo del usuario en cada pedido.

---

### ¿Qué consultas puedo hacer?

Con SQL puedes hacer cosas como

- `SELECT`: consultar datos.
- `INSERT`: agregar nuevos registros.
- `UPDATE`: modificar datos existentes.
- `DELETE`: eliminar registros.
- `CREATE TABLE`, `ALTER`, `DROP`: modificar la estructura de la base de datos.

Ejemplo simple de consulta:

```sql

SELECT nombre, email FROM usuarios WHERE id = 1;
```

Esta consulta busca el nombre y el correo del usuario con ID 1.

---

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
