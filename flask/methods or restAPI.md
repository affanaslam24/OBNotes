 just to keep it here,
 This is the html page
 ![[Pasted image 20250425205308.png]]

by now we have used:
flask, url_for(use it for redirection, used long iwht redirect), redirect(redirects you to a differenct endpoint), render_template(connects with an html page), request(will hellp you read the posted values.)



![[Pasted image 20250425205622.png]]

how do we know to write for 'post' method? because the html page has it as post. 

![[Pasted image 20250425205615.png]]

now, make sure to keep in mind the 'name' field from your html.

![[Pasted image 20250425205735.png]]
because we are gonna use the 'name' field for requesting the value.
Also, the request will give us a string so we will change it to desired data type.

so the final code inside the **def subimit func** will look like this:
![[Pasted image 20250425205943.png]]


we can use more than one html files for render_template.
basically like this:
![[Pasted image 20250425210102.png]]


Something like this if you wanna have the passed value form the previous endpoint to be shown:
![[Pasted image 20250425210212.png]]
that 'result' is in the html, remember we are rebderinng the html file over here:
![[Pasted image 20250425210255.png]]

