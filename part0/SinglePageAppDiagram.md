```mermaid
sequenceDiagram
    participant browser
    participant server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser executes JavaScript that fetches the notes data from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON data [{ "content": "SPA is cool", "date": "2023-01-01" }, ...]
    deactivate server

    Note right of browser: The browser parses the JSON data and renders the notes

    Note right of browser: User writes a note and clicks Save

    browser->>browser: Update the notes array and redraw the notes list

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa (new note as JSON)
    activate server
    server-->>browser: Response 201 Created
    deactivate server

    Note right of browser: The new note is sent to the server without reloading the page
