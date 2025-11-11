```
sequenceDiagram
    participant browser
    participant server

    Note right of browser: User types "Hello Everyone" into the text field and clicks Save

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note<br/>Body: content="Hello Everyone"
    activate server
    Note right of server: Server saves the new note<br/>and updates the data.json file
    server-->>browser: 302 Redirect to /notes
    deactivate server

    Note right of browser: Browser follows the redirect to reload the notes page

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: JavaScript file
    deactivate server

    Note right of browser: Browser executes main.js,<br/>which fetches the updated JSON data

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: Updated JSON including "Hello Everyone"
    deactivate server

    Note right of browser: Browser executes the callback<br/>and re-renders the list of notes<br/>including the new note "Hello Everyone"
```