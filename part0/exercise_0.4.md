``` mermaid
sequenceDiagram
    participant b as browser
    participant s as server
    b->>s:POST https://studies.cs.helsinki.fi/exampleapp/new_note
    note over b: data_form<br>note:text
    s-->>b:responds with code 302 (redirect)
    note over b,s: Server tells the browser to send another HTTP request <br> (GET) to the one specified on the location header 
    b->>s:GET https://studies.cs.helsinki.fi/exampleapp/notes
    s-->>b:HTML document
    b->>s:GET https://studies.cs.helsinki.fi/exampleapp/main.css
    s-->>b:main.css
    b->>s:GET https://studies.cs.helsinki.fi/exampleapp/main.js
    s-->>b:main.js
    Note right of b: The browser starts executing the JavaScript code that fetches the JSON from the server
    b->>s: GET https://studies.cs.helsinki.fi/exampleapp/data.json
    s-->>b: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]
```