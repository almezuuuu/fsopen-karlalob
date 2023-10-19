```mermaid
    participant browser
    participant server
    participant user

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
    activate server
    server-->>browser: HTML document
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
    activate server
    server-->>browser: the css file
    deactivate server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
    activate server
    server-->>browser: the JavaScript file
    deactivate server

    Note right of browser: The browser starts executing the JavaScript code that fetches the JSON from the server

    browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    activate server
    server-->>browser: [{ "content": ---, "date": --- }, ... ]
    deactivate server

    Note right of browser: The browser executes the callback function that renders the notes

    user->>browser: enter's a text to the input box and click the save button
    browser->>server: send input to server POST https://fullstack-exampleapp.herokuapp.com/new_note_spa
    Note over browser,server: form data contains the input of user as json format
    activate server
    Note right of server: the server execute js script with the trigger onsubmit to insert user input and current date then send the data to server thru POST as json format.
    deactivate server

```