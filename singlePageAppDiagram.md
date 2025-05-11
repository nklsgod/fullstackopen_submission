sequenceDiagram
participant Browser
participant Server

    Note over Browser: User writes note in text field
    Note over Browser: User clicks "Save" button

    Browser->>Server: HTTP POST https://studies.cs.helsinki.fi/exampleapp/new_note
    Note over Browser: Form data contains the new note content

    Server-->>Browser: HTTP Status Code 302 (URL Redirect)
    Note over Server: Server processes the note and adds it to the notes array

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/notes
    Server-->>Browser: HTML Document

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.css
    Server-->>Browser: CSS File

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/main.js
    Server-->>Browser: JavaScript File

    Note over Browser: Browser starts executing JS code that requests JSON data from server

    Browser->>Server: HTTP GET https://studies.cs.helsinki.fi/exampleapp/data.json
    Server-->>Browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]

    Note over Browser: Browser executes the event handler that renders notes to display
