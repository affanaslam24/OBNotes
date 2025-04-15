![[Pasted image 20250410141650.png]]
- reference one logical resource to another one: ref or getAtt
- join and split are same types
- getAz ans select are often used together
- base64 and sub are used together. Sub can be used for substitution process seperately as well.
- Cidr is used to create cidr blocks


---
#### REF and getAtt

![[Pasted image 20250410141946.png]]

- can be used along with the Parameters.
- Ref can be used for both parameters as well as logical resources.
- getAtt we use to gain access to the physical resource attributes by using reference of the logical reosurce.
- Also, notice how ref gives back the main attribute, usually the id name. And getAtt will give you specialised attributes using a '.' function.


---

#### getAz and select
![[Pasted image 20250410142422.png]]
- now, getAz gives youb a list of Az in that region, BUT it uses default vpc to find the Azs.
- How? basically, each default VPC has a subnet in one AZ of that region.
- But lets say you misconfigured your Default VPC, then there would be a problem to getAZ list.

- Sleect uses indexing number like in arrays or list.

---
#### Join and split

![[Pasted image 20250410142713.png]]

- its self explanatory.

---

### base64 and sub (using userdata)

![[Pasted image 20250410142933.png]]
- now this one is interesting
- base64 requires a plaintext as input, the one we have written, and gives out an output which is encoded.
- NOTE: that the Sub and the piipe sign is not used for substituting the plaintxt of the bash script!
- the sub function is used for substituting the **Instance.IsntanceID** with real time value.
- ALthough that is an error, because its using **self substituiton**, meaning that its trying to substritute a value of its own instance id, but note that the instanc ehas not even been created, **so this is an error.**
- there arwe three types of **subs**: parameter, logical resource, attriv=butes of physical resoruce referecnwd tghrough logical resoruce.

Chatgpt this: difference between ref, getAt and sub.

---

#### cidr

![[Pasted image 20250410143856.png]]

- now this is a llil tricky to understand, but here it is:
- we use the getAtt to get the base Cidr block, and the CIdr function to make a **list** of cidr blocks that can be created.
- cidr function uses: 16 as the number oof subnets that needs to be generated out of the **parent cidr block**. **12 as the size of each subnet.**
- Since this gives us a **list**, we use **select function** to select the cidr block for our subnet.

this has limitation:
- it depends upon the parent cidr block.
- IT cannot allocate or unallocate ranges! we will understand later what this means.


