sequenceDiagram
	participant browser
	participant server

	browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa
	activate server
	server->>browser: HTML document for SPA
	deactivate server
	
	browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/main.css
	activate server
	server->>browser: css file
	deactivate server
	
	browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/spa.js
	activate server
	server->>browser: the JS file for SPA
	deactivate server

	note right of browser: The browser starts executing the JavaScript code for the SPA

	browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json 
	activate server
	server-->>browser: [{ "content": "HTML is easy", "date": "2023-1-1" }, ... ]	
	deactivate server

	Note right of browser: The browser executes the callback function that renders the notes


