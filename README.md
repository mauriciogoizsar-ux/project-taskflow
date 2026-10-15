# TaskFlow - Tablero Kanban

Aplicación web de gestión de tareas estilo Kanban construida con Angular 22, TypeScript y Signals.

## Requisitos

- **Node.js:** 22.22.3 o superior

## Stack Tecnológico

- **Frontend:** Angular 22, TypeScript (Modo Estricto), Signals
- **Calidad de Código:** ESLint, Prettier, Husky, lint-staged, Conventional Commits

## Cómo ejecutar el proyecto

1. Instalar dependencias: `npm install`
2. Iniciar el servidor local: `ng serve`
3. Abrir en el navegador: `http://localhost:4200`

## Roadmap

- [x] Fase 0: Preparación y configuración inicial.
- [ ] Fase 1: Tablero local (nivel 1).
- [ ] Fase 2: Tarjetas y formularios.
- [ ] Fase 3: Drag and drop y múltiples tableros.

---

## Modelo de Base de Datos / Entidades

```mermaid
erDiagram
erDiagram
    USUARIO ||--o{ MIEMBRO : es
    TABLERO ||--o{ MIEMBRO : tiene
    TABLERO ||--o{ COLUMNA : tiene
    TABLERO ||--o{ ETIQUETA : tiene
    TABLERO ||--o{ ACTIVIDAD : registra
    TABLERO ||--o{ INVITACION : recibe
    COLUMNA ||--o{ TARJETA : contiene
    TARJETA }o--o{ ETIQUETA : se_asigna
    TARJETA ||--o{ ITEM_CHECKLIST : tiene
    TARJETA ||--o{ COMENTARIO : posee
    USUARIO ||--o{ COMENTARIO : escribe
    USUARIO ||--o{ ACTIVIDAD : realiza
```

| Entidad               | Campos principales                                                     | Relaciones                                                                 |
| :-------------------- | :--------------------------------------------------------------------- | :------------------------------------------------------------------------- |
| **Usuario**           | id, nombre, correo, avatar, fecha de creación                          | Tiene muchos tableros (como miembro)                                       |
| **Tablero**           | id, nombre, descripción, color, archivado, fecha de creación           | Tiene columnas y miembros                                                  |
| **Miembro**           | usuario, tablero, rol (dueño, editor, lector)                          | Une usuarios y tableros                                                    |
| **Columna**           | id, nombre, posición, límite de tarjetas (opcional)                    | Pertenece a un tablero                                                     |
| **Tarjeta**           | id, título, descripción, prioridad, fecha límite, posición, completada | Pertenece a una columna; tiene etiquetas, checklist, comentarios, adjuntos |
| **Etiqueta**          | id, nombre, color                                                      | Pertenece a un tablero; se asigna a tarjetas                               |
| **Ítem de checklist** | id, texto, hecho, posición                                             | Pertenece a una tarjeta                                                    |
| **Comentario**        | id, texto, autor, fecha                                                | Pertenece a una tarjeta                                                    |
| **Actividad**         | id, tipo de acción, autor, detalle, fecha                              | Pertenece a un tablero                                                     |
| **Invitación**        | id, correo, rol, estado, vencimiento                                   | Pertenece a un tablero                                                     |
