sequenceDiagram
	participant user
	participant browser
	participant server

	user->>browser: user writes note and clicks save button
	note right of browser: The browser captures the input and prepares to send it to the server.

	browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note_spa {"content": "new note", "date": "2024-07-30"}
	activate server
	note right of server: Server processes the new note and saves it.
	server->>browser: HTTP 201 created	
	deactivate server
	
	note right of browser: The browser updates the notes array with the new note.
	note right of browser: The browser re-renders the notes list with the new note included.
	

