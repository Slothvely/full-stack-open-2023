```mermaid
sequenceDiagram
  participant browser
  participant server

  browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note
    activate server
  server-->>browser: POST https://studies.cs.helsinki.fi/exampleapp/data.json
    Note left of server: The server reads the data from body.req, creates a new note object and adds it to the note array.
  server-->>browser: Status code 302
    Note left of server: The server requests for the browser to do a new HTTP GET request.
    deactivate server
  browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
      activate server
  server-->>browser: The HTML document
    deactivate server
  browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
  server-->>browser: The CSS file
    deactivate server
  browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.js
    activate server
  server-->>browser: The JS file
    deactivate server
    Note right of browser: The browser begins to execute the JavaScript code that fetches the JSON from the server.

  browser-->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
  server-->>browser: The array of notes
    deactivate server
    Note right of browser: The browser executes the callback function that renders the notes.
```
