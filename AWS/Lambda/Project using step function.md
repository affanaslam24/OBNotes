
![[Pasted image 20250408132550.png]]


### Notes on how this is working:

- general workflow looks like this:
	- the user selects the timer, the choice pf email and whatnot and sends it through API gateway to the API_lambda.
	- Apui_Lambda then sends all of this infoo to the state machine
	- Its the state machine which waits and uses the info to work the workflow accordingly.

