# Diagramas Parte 0 – Full Stack Open

Este documento contiene los diagramas de secuencia para los ejercicios **0.4**, **0.5** y **0.6** del curso Full Stack Open.

---

## 0.4 – Nueva nota (aplicación tradicional)

```mermaid
sequenceDiagram
    participant U as Usuario
    participant B as Navegador
    participant S as Servidor

    U->>B: Escribe nota y pulsa "Guardar"
    B->>S: POST /new_note (form-urlencoded)
    S-->>B: 302 Redirect -> /notes

    B->>S: GET /notes
    S-->>B: HTML /notes

    B->>S: GET /main.css
    S-->>B: CSS

    B->>S: GET /main.js
    S-->>B: JS

    B->>S: GET /data.json
    S-->>B: Notas (JSON)

    Note over B: JS renderiza lista de notas.<br/>La página se recarga completamente.
```

---

## 0.5 – Visitar la SPA (/spa)

```mermaid
sequenceDiagram
    participant U as Usuario
    participant B as Navegador
    participant S as Servidor

    U->>B: Navega a /spa
    B->>S: GET /spa
    S-->>B: HTML /spa

    B->>S: GET /main.css
    S-->>B: CSS

    B->>S: GET /spa.js
    S-->>B: JS (SPA)

    B->>S: GET /data.json
    S-->>B: Notas (JSON)

    Note over B: SPA renderiza notas en el navegador.<br/>Sin recarga adicional al cambiar de vista.
```

---

## 0.6 – Nueva nota en la SPA

```mermaid
sequenceDiagram
    participant U as Usuario
    participant B as Navegador
    participant S as Servidor

    U->>B: Escribe nota y pulsa "Guardar"
    B->>S: POST /new_note_spa (application/json)
    S-->>B: 201 Created (JSON)

    Note over B: JS (spa.js) preventDefault();<br/>notes.push(note); redrawNotes();<br/>La página NO se recarga y la UI<br/>ya muestra la nueva nota.
```
