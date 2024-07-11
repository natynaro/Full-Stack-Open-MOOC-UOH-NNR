# New Note in Single Page App Diagram

This diagram depicts the situation where a user creates a new note in the single-page app version by writing something into the text field and clicking the Save button.

```mermaid
sequenceDiagram
    participant user
    participant browser
    participant server

    user->>browser: Writes note and clicks Save
    Note right of browser: The browser captures the input and prepares an HTTP POST request

    browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa (with note content)
    activate server
    server-->>browser: Response with status and new note data
    deactivate server

    Note right of browser: The browser updates the UI to include the new note without a full page reload
