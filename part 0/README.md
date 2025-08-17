# Diagramas Parte 0 – Full Stack Open

Diagramas realizados para los ejercicios 0.4, 0.5 y 0.6 del curso.

---

## 0.4 – Nueva nota (aplicación tradicional)

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    server-->>browser: 302 Found (redirect to /notes)

    browser->>server: GET /notes
    server-->>browser: HTML document

    browser->>server: GET /main.css
    server-->>browser: CSS file

    browser->>server: GET /main.js
    server-->>browser: JavaScript file

    Note right of browser: browser ejecuta el código JS para solicitar datos JSON

    browser->>server: GET /data.json
    server-->>browser: JSON (notas)

    Note right of browser: browser renderiza la lista de notas con el JSON recibido
```

---

## 0.5 – Visitar la SPA (/spa)

```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET /spa
    server-->>browser: HTML document

    browser->>server: GET /main.css
    server-->>browser: CSS file

    browser->>server: GET /spa.js
    server-->>browser: JavaScript file

    Note right of browser: browser ejecuta spa.js y hace petición de datos JSON

    browser->>server: GET /data.json
    server-->>browser: JSON (notas)

    Note right of browser: browser renderiza notas usando el JSON recibido
```

---

## 0.6 – Nueva nota en la SPA (corregido)

```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: submit handler:<br/>preventDefault();<br/>notes.push(note); redrawNotes()

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa\nContent-Type: application/json\nBody: {"content","date"}
    server-->>browser: 201 Created (JSON)

    Note right of browser: No redirect.<br/>No page reload.<br/>La UI ya muestra la nueva nota.
```
