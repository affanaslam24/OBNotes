![[Pasted image 20250508122012.png]]

packages we would need:
mongoose express multer bcrypt cloudinary cors dotenv jsonwebtoken nodemon


---


make the type as module isnide your package,json

import express from 'express'

import cors from 'cors'

import 'dotenv/config'

---

first we make some configursation for our project:
And then we add a middleware, middleware being the intermediatory through which our app will process:
here we are using express.json, so 
We will also use a middleware like cors for it to connect to backend.

![[Pasted image 20250508123913.png]]

---

![[Pasted image 20250508124245.png]]

- **`app.get()`**:  
    This defines a route handler for HTTP GET requests.
- **`'/'`**:  
    The path `'/'` refers to the root URL of your server (e.g., `http://localhost:3000/`).
- **`(req, res) => { ... }`**:  
    This is a callback function that will run when someone makes a GET request to the `'/'` path.
    - `req` (request): Holds info about the request sent by the client.
    - `res` (response): Used to send back data to the client.        
- **`res.send('API working')`**:  
    Sends the plain text string `'API working'` as the response to the client.


---


  

app.listen(port, ()=> console.log("Server Started", port))

- **`app.listen(port, ...)`**:  
    Starts the server and makes it listen on the specified `port` (e.g., 3000). This is where your backend will run.
    
- **`port`**:  
    A variable (typically set earlier like `const port = 3000` or `process.env.PORT`) indicating which port the server should use.
    
- **`() => console.log("Server Started", port)`**:  
    A callba

---

