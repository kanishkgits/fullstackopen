```mermaid
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User writes a note and clicks Save

    browser->>browser: Update the notes array locally and redraw the notes list

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa (new note as JSON)
    activate server
    server-->>browser: Response 201 Created
    deactivate server

    Note right of browser: The new note is saved on the server without a page reload
