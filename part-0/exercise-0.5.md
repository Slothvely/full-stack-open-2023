```mermaid
sequenceDiagram
  participant browser
  participant server

  browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
  server-->>browser: The HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
      activate server
    server-->>browser: The CSS file
      deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
      activate server
    server-->>browser: the JavaScript file
      deactivate server
    Note right of browser: The browser begins to execute the JavaScript code that fetches the JSON from the server.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
      activate server
    server-->>browser: The JSON notes array
    server-->>browser: Status code 200 and ready state 4
      deactivate server
    Note right of browser: The browser translates the received JSON string to a JS object.
    Note right of browser: The browser renders the notes list with redrawNotes().

```
