sequenceDiagram
	participant browser
        participant server

	user->>browser: user writes note and clicks save button
	note right of browser: browser captures the input and prepares it to send server
	
	browser->>server: POST https://studies.cs.helsinki.fi/exampleapp/new_note {"content": "new note", "date": "2024-07-30"}
	activate server
	note right of server: Server processes the new note and saves it
	server-->>browser: HTTP 201 Created
	deacrtivate server

	note right of browser: The browser recieves the response and refreshes list
	
	browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/notes
	activate server
	server-->browser: Updated HTML document
	decativate server
		
	browser->>server: GET https://studies.cs.helsinki.fi/exampleapp/data.json
   	activate server
   	server-->>browser: Updated JSON data with new note
    	deactivate server
	
	note right of browswr: now we have updated list displayed with new notes.


