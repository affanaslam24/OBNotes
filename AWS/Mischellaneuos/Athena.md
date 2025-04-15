- adhoc queries in super large datasets
- you ONLY pay for the data consumed while the query is being run, that all.
![[Pasted image 20250411183720.png]]
- so the schema to query on is just a schema type that you define, but there is no schema that gets made on the data.
- the data remains the same, and the translation of data to a table like format is done on the fly
- its a relational like schema

- the data stored in S3 is always read only
- important: it can read MANY forms of data. it can json, csv, xml, cloudtrail etc, any kind of data stored in S3, but make sur ethe S3 is not adding newer data by second. S3 cant be a write type of S3. No changes to the data.
- in the service, athena, we creare a schema with tables of our specification
- and this table is somethign that can be personalised in jowever way you want to!

![[Pasted image 20250411184200.png]]


-- example: if there is a hhuge data and they want to query it, but they dont want infrastructure cost on it, or they dont want to maintain database or overhead on this task

---

demo:

![[Pasted image 20250411190232.png]]



![[Pasted image 20250411190331.png]]

first, set up a query result location in s3:
![[Pasted image 20250411190400.png]]


create an S3 bucker:
![[Pasted image 20250411190427.png]]
![[Pasted image 20250411190448.png]]
then add it to the query result location
**This will store any outputs to the query that we will run on our data**


Steps:
![[Pasted image 20250411190605.png]]
create a database:
you defined the definitoin of the dataabse

Now, create the definition of table:
![[Pasted image 20250411190656.png]]
badically, creating a table
AND the location from where the queries will be run on this table will be an S3 bucket which we dont manage, the osm-pds planet. thats our datasource location

The table was created:
![[Pasted image 20250411190923.png]]



NOw, we run query on the data:

![[Pasted image 20250411190950.png]]
Limit 10 means, 10 items form the dataabse 


Now, you will be billed for this:
![[Pasted image 20250411191100.png]]
the amount of data that was scanned1


![[Pasted image 20250411191211.png]]


![[Pasted image 20250411191241.png]]

![[Pasted image 20250411191305.png]]


![[Pasted image 20250411191355.png]]


![[Pasted image 20250411191507.png]]


