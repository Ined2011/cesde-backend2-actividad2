# 🧪 Laboratorio: Documentación de Pruebas de API REST

 Esta actividad debe documentarse íntegramente en este archivo `README.md`. Por cada punto, el estudiante debe ejecutar la petición indicada y completar los espacios en blanco con la **Respuesta del Servidor** y el **Código de Estado** real obtenido en su entorno local.

---

## 🚀 Guía de Pruebas y Documentación

### 1. Crear un nuevo estudiante

* **Método:** `POST`
* **URL:** `http://localhost:8080/api/students`
* **Cuerpo de la Petición (JSON):**

```json
{
  "firstName": "Ana",
  "lastName": "García",
  "email": "ana.garcia@estudiante.com",
  "birthDate": "2001-03-12",
  "phone": "3004445566"
}

```

* **Respuesta del Servidor (Completar):**

```json

{
    "firstName": "Maria",
    "lastName": "Buitrago",
    "email": "maria.buitrago@estudiante.com",
    "birthDate": "1985-03-12",
    "id": 2,
    "phone": "3002221115"
}
```

* **Código de Estado (Status Code):** `201 Created`

---

### 2. Obtener la lista completa

* **Método:** `GET`
* **URL:** `http://localhost:8080/api/students`
* **Respuesta del Servidor (Completar):**

```json

[
    {
        "firstName": "Juan",
        "lastName": "Perez",
        "email": "juan.perez+test@example.com",
        "birthDate": "1995-06-15",
        "id": 1,
        "phone": "3001234567"
    },
    {
        "firstName": "Maria",
        "lastName": "Buitrago",
        "email": "maria.buitrago@estudiante.com",
        "birthDate": "1985-03-12",
        "id": 2,
        "phone": "3002221115"
    }
]

```

* **Código de Estado (Status Code):** `200 OK`

---

### 3. Buscar estudiante por ID (Existente)

* **Método:** `GET`
* **URL:** `http://localhost:8080/api/students/1`
* **Respuesta del Servidor (Completar):**

```json

{
    "firstName": "Juan",
    "lastName": "Perez",
    "email": "juan.perez+test@example.com",
    "birthDate": "1995-06-15",
    "id": 1,
    "phone": "3001234567"
}


```

* **Código de Estado (Status Code):** `200 OK`

---

### 4. Buscar estudiante por Email

* **Método:** `GET`
* **URL:** `http://localhost:8080/api/students/email/ana.garcia@estudiante.com`
* **Respuesta del Servidor (Completar):**

```json

{
    "firstName": "Maria",
    "lastName": "Buitrago",
    "email": "maria.buitrago@estudiante.com",
    "birthDate": "1985-03-12",
    "id": 2,
    "phone": "3002221115"
}


```

* **Código de Estado (Status Code):** `200 OK`

---

### 5. Actualizar datos del estudiante

* **Método:** `PUT`
* **URL:** `http://localhost:8080/api/students/1`
* **Cuerpo de la Petición (JSON):**

```json
{
  "firstName": "Ana María",
  "lastName": "García",
  "email": "ana.garcia@estudiante.com",
  "birthDate": "2001-03-12",
  "phone": "3119998877"
}

```

* **Respuesta del Servidor (Completar):**

```json

{
    "firstName": "Ana María",
    "lastName": "García",
    "email": "ana.garcia@estudiante.com",
    "birthDate": "2001-03-12",
    "id": 1,
    "phone": "3119998877"
}

```

* **Código de Estado (Status Code):** `200 OK`

---

### 6. Escenario de Error: Buscar ID inexistente

* **Método:** `GET`
* **URL:** `http://localhost:8080/api/students/999`
* **Respuesta del Servidor (Completar):**

```json
1

```

* **Código de Estado (Status Code):** `404 Not Found`

---

### 7. Eliminar el registro

* **Método:** `DELETE`
* **URL:** `http://localhost:8080/api/students/1`
* **Respuesta del Servidor (Completar):**

```json

1

```

* **Código de Estado (Status Code):** `204 No Content`

---

## 📝 Cuestionario de Análisis

**Instrucciones:** Responda las siguientes preguntas basándose en su experiencia durante el laboratorio y el código del proyecto.

1. **¿Cuál es la diferencia entre los códigos de estado 200 y 201? ¿En qué endpoints se obtuvieron cada uno?**
* *Respuesta:*
El código 200 es que confirma que fue exitoso y el 201 confirma que se creo un nuevo estudiante en la BD. En los endpoins: En crear,obtener la lista, buscar estudiante por ID y por Email, también en actualizar estudiante

2. **En el escenario de error (punto 6), ¿qué información devuelve la API y por qué es importante para un desarrollador frontend recibir un código 404 en lugar de un código 500?**
* *Respuesta:*
Devuelve un 404 Not Found. Dado a que este error es de un ID que no existe por parte del cliente y el error 500 hace referencia al servidor que falla en el backend.

3. **¿Qué sucede en la base de datos PostgreSQL cuando se ejecuta con éxito la petición DELETE? (Explique brevemente en términos de persistencia).**
* *Respuesta:*
Como su palabra lo dice se elimina definitivamnete el ID solcitado y se consulta por GET este ya no va a registrar.

4. **Si intentara crear un estudiante con el mismo email que ya existe en la base de datos, ¿qué cree que sucedería y qué código de error sería el más adecuado para devolver?**
* *Respuesta:*
De una la BD lanza el error por ser un email duplicado con datos existentes, el código de error más adecuado podria ser 409 Conflict, por que existe un conflicto en un dato ya existente como es el email.

5. **¿Por qué utilizamos el método PUT para actualizar y no el método POST? ¿Cuál es la convención técnica detrás de esta decisión?**
* *Respuesta:*
 El PUT actualiza el dato existente, y el POST se usa para crear nuevos datos. Por eso usamos PUT para actualizar, porque estamos modificando un dato existente por el identificador que es el ID.



