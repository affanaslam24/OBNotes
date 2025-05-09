Things you need to udnerstand based on the understanding of get and post based on the current python usage is:

whenever we type in a url, we get a get request by defualt.
When we pass in some value,, we make a post request.

if a route has both get and post, that basically means, you can have both the properties:
- first you visit the route, ansd when you do that, we check in the code using 'if else', if the request is get, we render the index.html template.
- it the request is 'post', then we render it a different page, thats it.
so this means, for a route having both the request, when you trype the link to that route, it first opens the get template, because get is by default. But if you type in a value insid eht etemplate, then click something, like a button, the button will have an action and using that action we can route to a different page, but we use 'post' method for it.

two exammples:
![[Pasted image 20250505215903.png]]
![[Pasted image 20250505215912.png]]

and

![[Pasted image 20250505215937.png]]

So, our question would be- how do we determine, what do we do in the case of get or post:
![[Pasted image 20250505220101.png]]
in this login route?
we do it like this:
![[Pasted image 20250505220211.png]]

this is crucial also to understand how to navigate between html pages and routes.



