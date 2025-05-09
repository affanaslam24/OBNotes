app=Flask(____name_____)is basically you creating an instance of flask
and app.run() is what we use to run the instance.



terms we need to work on:
- wsgi
- decorater attached with a function, this function is called binding function.
- template connnection with the data srource, dynamic rendering.

Now, on the app.run(), inisde the bracket we have host, port, debut and other options.
The debug option gives us opportunity to run the backend dynamically.
Whenever there is a change in the code, it automatically restarts the ***servcer***.

its possible that you can write 2 functions with same name, so beware of that.


---

using route with parameter:
![[Pasted image 20250425203747.png]]
these are making utilisation of rules in flask

to redirect to different pages, we use redirct package and url_for package.

![[Pasted image 20250425204155.png]]

result is the name of the string, and it contains sucees or fail. So using that as url_for will redirect to whichever api has the endpoint as success or fail. 


can also use html instead of returnong a string or anything:
![[Pasted image 20250425204608.png]]





