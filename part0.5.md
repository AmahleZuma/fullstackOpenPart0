sequenceDiagram
    participant browser
    participant server 

    Note over browser, server: Browser loads HTML document once. Dynamically makes changes using Javascript.

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: CSS document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: JS document
    deactivate server

    Note right of browser: Browser will now run javascript that will call the JSON

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": "single page app does not reload the whole page", "date": "2019-05-25" }, ... ]
    deactivate server

    Note right of browser: Javascript runs callback function that executes the notes
