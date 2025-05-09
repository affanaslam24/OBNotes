![[Pasted image 20250426210141.png]]
so we removed our css to a seperate style/css folder under style.css filename.
And to call upon that css file, we will use this method of: 
- <link rel="stylesheet" href="{{ urk_for('static', filename='css/style.css')}}" />
now, to understand what we have done is:
- we are using url_for, to create a url for the style.css's static component and then use it as href.
- So, as you can see, me just made use of jinja2 template again.

---

for integration of javascript:
![[Pasted image 20250426210833.png]]

script, and alert



and then shift that to a folder inside 'static' folder, named script.js:
![[Pasted image 20250426211032.png]]

and isnide the html file:
![[Pasted image 20250426211208.png]]


![[Pasted image 20250504144634.png]]

![[Pasted image 20250504144658.png]]

so this is how you send things between python and html

![[Pasted image 20250504145011.png]]
if we want to use a for loop inside of our html

![[Pasted image 20250504145152.png]]
so a common mistake, we need to put the variable inside ht ecurly bracets


to send in a list:

![[Pasted image 20250504145344.png]]
![[Pasted image 20250504145334.png]]


![[Pasted image 20250504145429.png]]

![[Pasted image 20250504161906.png]]
look that the action is #, meaning, itll redirect to /# which means the same page

![[Pasted image 20250504162008.png]]

## How to cehckk if the page is get or post, and how to work with ut?
![[Pasted image 20250504162213.png]]
if its post, then we perform the action of takking the data from the page and redirect to another page
if its get, it shows a particular page