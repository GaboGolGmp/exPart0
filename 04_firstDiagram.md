``` mermaid

sequenceDiagram
    participant browser
    participant server

    
    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note left of server: The server saves the note on the DB
    activate server

    server-->>browser: Code 302 'Redirection' GET https://studies.cs.helsinki.fi/exampleapp/notes
    Note right of browser: The server automatically redirects to refresh to show the new notes added by the user
    deactivate server


    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The JavaScript code fetches the notes 
    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: JSON file with the notes
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes


```
