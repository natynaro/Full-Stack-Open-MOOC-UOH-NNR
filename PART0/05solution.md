sequenceDiagram
    participant user
    participant browser
    participant server
    user->>browser: Writes note and clicks Save
    Note right of browser: The browser captures the input and prepares an HTTP POST request

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note (with note content)
    activate server
    server-->>browser: Redirect to /exampleapp/notes
    deactivate server

    Note right of browser: The browser performs the redirection and reloads the notes page

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... , { "content": "new note content", "date": "2024-7-11" }]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes, including the new note
