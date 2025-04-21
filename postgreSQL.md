# PostgreSQL
---

## Índice
- [Qué es](#qué-es)
- [Paso a paso para utilizar PostgreSQL](#paso-a-paso-para-utilizar-postgresql)
- [Relaciones entre tablas](#relaciones-entre-tablas)

---

## Qué es

👉**PostgreSQL** es un sistema de gestión de bases de datos relacional **de código abierto**, muy potente, que soporta tanto SQL como consultas avanzadas, y está enfocado en la **extensibilidad** y el cumplimiento de estándares.

👉Es muy utilizado en ambientes profesionales y productivos gracias a su **robustez**, **seguridad** y **soporte a transacciones avanzadas**.

👉**pgAdmin** es la herramienta gráfica oficial que se utiliza para gestionar PostgreSQL de manera visual.

👉Al igual que otros RDBMS, PostgreSQL permite la concurrencia, relaciones complejas entre datos y operaciones seguras sobre la información.

---

## Paso a paso para utilizar PostgreSQL

Primero de todo instalamos **PostgreSQL y pgAdmin** 💻

🔗 Sitio oficial: [https://www.postgresql.org/download/](https://www.postgresql.org/download/)

💻 **Windows/Mac**: instalador gráfico que incluye PostgreSQL y pgAdmin.

💻 **Linux (Ubuntu)**:

```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
```

Para acceder al intérprete de comandos de PostgreSQL:

```bash
sudo -i -u postgres
psql
```

### Comandos básicos

> 💡 👀 *Las tablas suelen tener nombres en plural y en minúscula*

```sql
-- Ver todas las bases de datos
\l

-- Conectarse a una base de datos
\c nombre_base

-- Crear una base de datos
CREATE DATABASE nombre_base;

-- Ver todas las tablas
\dt

-- Crear una tabla
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    email VARCHAR(255) NOT NULL,
    role VARCHAR(50),
    password TEXT NOT NULL
);

-- Insertar registros
INSERT INTO users (name, email, role, password)
VALUES ('Ana', 'ana@email.com', 'admin', 'passwordSegura');

-- Ver estructura de una tabla
\d users
```

---

## Relaciones entre tablas

### one-to-one

En PostgreSQL, una relación **uno a uno** se crea usando una clave foránea con restricción `UNIQUE`:

```sql
CREATE TABLE dni (
    id SERIAL PRIMARY KEY,
    user_id INT UNIQUE,
    dni_number VARCHAR(100),
    expiry_date DATE,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

### one-to-many

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(100)
);
```

```sql
CREATE TABLE posts (
    id SERIAL PRIMARY KEY,
    title VARCHAR(100),
    content TEXT,
    user_id INT,
    FOREIGN KEY (user_id) REFERENCES users(id)
);
```

### many-to-many

Para una relación muchos a muchos usamos una **tabla intermedia**:

```sql
CREATE TABLE tags (
    id SERIAL PRIMARY KEY,
    name VARCHAR(50)
);
```

```sql
CREATE TABLE posts (
    id SERIAL PRIMARY KEY,
    title VARCHAR(100),
    content TEXT
);
```

```sql
CREATE TABLE posts_tags (
    post_id INT,
    tag_id INT,
    PRIMARY KEY (post_id, tag_id),
    FOREIGN KEY (post_id) REFERENCES posts(id),
    FOREIGN KEY (tag_id) REFERENCES tags(id)
);
```

> `PRIMARY KEY (post_id, tag_id)` asegura que una misma relación no se repita.

---

### Comandos para relaciones entre tablas

```sql
-- Crear tabla con clave foránea
CREATE TABLE comments (
    id SERIAL PRIMARY KEY,
    content TEXT NOT NULL,
    post_id INT,
    FOREIGN KEY (post_id) REFERENCES posts(id),
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

```sql
-- Añadir una foreign key a una tabla existente
ALTER TABLE comments
ADD user_id INT,
ADD CONSTRAINT fk_comments_users FOREIGN KEY (user_id) REFERENCES users(id);
```

---

### Notaciones

`1:1` → Uno a uno  
`1:N` → Uno a muchos  
`N:M` → Muchos a muchos
