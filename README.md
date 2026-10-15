# TaskFlow - Tablero Kanban

Aplicación web de gestión de tareas estilo Kanban construida con Angular 18+, TypeScript y Signals.

## Stack Tecnológico
- **Frontend:** Angular, TypeScript (Modo Estricto)
- **Calidad de Código:** ESLint, Prettier, Husky, Conventional Commits

## Cómo ejecutar el proyecto
1. Instalar dependencias: `npm install`
2. Iniciar el servidor local: `ng serve`
3. Abrir en el navegador: `http://localhost:4200`

---

## Modelo de Base de Datos / Entidades

| Entidad | Campos principales | Relaciones |
| :--- | :--- | :--- |
| **Usuario** | id, nombre, correo, avatar, fecha de creación | Tiene muchos tableros (como miembro) |
| **Tablero** | id, nombre, descripción, color, archivado, fecha de creación | Tiene columnas y miembros |
| **Miembro** | usuario, tablero, rol (dueño, editor, lector) | Une usuarios y tableros |
| **Columna** | id, nombre, posición, límite de tarjetas (opcional) | Pertenece a un tablero |
| **Tarjeta** | id, título, descripción, prioridad, fecha límite, posición, completada | Pertenece a una columna; tiene etiquetas, checklist, comentarios, adjuntos |
| **Etiqueta** | id, nombre, color | Pertenece a un tablero; se asigna a tarjetas |
| **Ítem de checklist** | id, texto, hecho, posición | Pertenece a una tarjeta |
| **Comentario** | id, texto, autor, fecha | Pertenece a una tarjeta |
| **Actividad** | id, tipo de acción, autor, detalle, fecha | Pertenece a un tablero |
| **Invitación** | id, correo, rol, estado, vencimiento | Pertenece a un tablero |