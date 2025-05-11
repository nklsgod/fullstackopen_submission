sequenceDiagram
participant Browser
participant Server

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/spa
    Server-->>Browser: HTML Document

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Server-->>Browser: CSS File

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    Server-->>Browser: JavaScript File

    Note over Browser: Browser starts executing the JS code
    Note over Browser: JS code requests JSON data from server

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/data.json
    Server-->>Browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]

    Note over Browser: Browser executes the event handler
    Note over Browser: that renders notes using DOM-API
    Note over Browser: No additional page reloads after initial load
