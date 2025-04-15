- where different parts of your office or whatever can pump data into it for long term analysis and working on it, and its designed for reporting and analytics, not for operational style usage.

RDS is oltp, this is OLAP
OLTP, is insert delete, update etc.
OLAP is where you put various OLTP data for analysis, trending, and etc.

- you can integrate with foreign databases using federated queries. Its like the federated identities in cognito.

![[Pasted image 20250411193805.png]]


Its not serverless like athena, or doesnt has ad hoc without base infrastructure like athena.
for ad hoc queries and such demands, go for athena


- its not highly available with design..
- we work with the leader node
- compute node performs queries assigned by the leader node.
- 
 