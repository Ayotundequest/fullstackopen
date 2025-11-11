sequenceDiagram
    participant browser
    participant server

    Note right of browser: User enters https://studies.cs.helsinki.fi/exampleapp/spa

    browser->>server: GET /spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET /main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET /spa.js
    activate server
    server-->>browser: JavaScript (SPA logic)
    deactivate server

    Note right of browser: Browser executes spa.js<br/>and makes a request to fetch existing notes

    browser->>server: GET /data.json
    activate server
    server-->>browser: JSON data of all notes
    deactivate server

    Note right of browser: Browser renders notes using JavaScript<br/>No new page loads — everything happens inside the SPA
