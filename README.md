
# Prueba Técnica: API REST para Gestión de Tareas (Task Manager)

## Descripción

Implementa una **API REST** usando **Node.js + Express** que permita a usuarios:

- Registrarse
- Autenticarse mediante JWT
- Gestionar tareas (CRUD)

> **Nota:** No es necesario usar una base de datos real. Se permite una implementación en memoria (arrays/objetos) para simplificar la prueba.

---

## Endpoints Requeridos

### Autenticación

- `POST /api/auth/register`  
  Registra un usuario: `{ name, email, password }`  
  **Respuesta:** 201 con `{ id, name, email }`

- `POST /api/auth/login`  
  Login: `{ email, password }`  
  **Respuesta:** `{ token }` (JWT)

### Tareas

- `GET /api/tasks`  
  Lista tareas del usuario autenticado.  
  **Opcional:** paginación y filtros: `?page=&limit=&completed=&search=`  
  Si el token es de admin, puede usar `?all=true` para ver todas las tareas.

- `POST /api/tasks`  
  Crea una tarea: `{ title, description, dueDate? }`  
  **Respuesta:** 201 con la tarea creada.

- `GET /api/tasks/:id`  
  Obtiene una tarea (solo owner o admin).

- `PUT /api/tasks/:id`  
  Actualiza una tarea (owner o admin).

- `DELETE /api/tasks/:id`  
  Borra una tarea (owner o admin).

- `PATCH /api/tasks/:id/complete`  
  Marca/desmarca como completada (owner o admin).

---

## Reglas y Expectativas Técnicas

- Usar **JWT** para autenticación en header: `Authorization: Bearer <token>`
- Validar entradas con **express-validator**
- Buen manejo de errores (códigos HTTP correctos)
- Estructura clara: `routes/`, `controllers/`, `middleware/`, `models/`
- **In-memory DB** (arrays) con funciones para crear/buscar/actualizar/reset (útil para tests)
- Añadir tests con **Jest + Supertest** cubriendo: registro/login, crear tarea, leer tarea, actualizar y borrar
- Documentar cómo ejecutar y cómo se evaluará (ver rúbrica abajo)

---

## Criterios de Evaluación

1. **Correctitud funcional:** los endpoints devuelven lo esperado
2. **Calidad del código:** legibilidad, modularidad, uso correcto de async/await
3. **Validación y manejo de errores**
4. **Tests automatizados que pasen**
5. **Bonus:** paginación, filtros, control de roles (admin), comentarios claros

---

## Tiempo

⏱️ 1.5–3 horas