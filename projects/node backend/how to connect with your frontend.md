
- go to the page jsx file in frontend
- here, lets go to the login.jsx file page

- files that we would visit-
	- the page that we would connect
	- the appcontext where we will make a state and then add it to value field.

![[Pasted image 20250513163155.png]]
these fields inside the login jsx will take the credentials, call the api and form a token in return.

we need to visit the appcontext file and make a state for that token.

![[Pasted image 20250513163645.png]]
in appcontext


then, in the login page jsx, add the backednurl, toke, settoke, from the useContext(appContext) jsx.
Then, we will ue these inside the submithandler, basically when the submit button is clicked, what would happen.


![[Pasted image 20250513165257.png]]

![[Pasted image 20250513165304.png]]


Then we went to navbar section

![[Pasted image 20250513170140.png]]

the token gets stored in local storage


if you dont want your account to log out on each refresh, you will have to load the token from the local storage to the state .

