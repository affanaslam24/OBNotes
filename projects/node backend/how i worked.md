
- now lets add the authentication system so that only the admin can add the doctor.
- So first we add the admin email and admin password for our admin in the .env file
- the go to the adminController only, and make the admin authentication api.


- the connection between backend and frontend was: i was creating a route in adminController, making an api, where the logic for api request and repsonse was happening, and then that was passed onto adminRoute for using as an api endpoint routing with all the (/api/admin/authentication, functionFromADminController) 

- so now that the routing is succesful between an endpoint and the function, we can successfully check if th eresponse form the endpoint is valid, based on the .env email and password for admin. Then we will use JWT for authetentication

- using this token, we will allow the admin to login
- so itll work like this, we wont be able to add doctor until its found the one adding the doctor is the admin with this token


- //so, well make a middleware, and if the admin is logged in, then only we will be able to add the doctor



---


CONNECTION BETWEEN FRONTEND AND BACKEND


- add a .env file wiht the backend url
- go to the context of the frontend where appcotext resides
- use axios
- insid eappcontextprovider (idk why specifically here), put the url from the .env for the backend.
- const backendURL= import.meta.env.VITE_BACKEND_URL
- 