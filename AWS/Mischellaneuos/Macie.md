![[Pasted image 20250410122842.png]]
- it uses data identifiers to find the data that needs to be protected.
- we can use managed DI or custom regex based
- now macie uses jobs to find these dats, which can then integrate with eventbridge.

- in the discovery job we mention which buckets we want to use macuie pon


![[Pasted image 20250410123112.png]]

this is how the working loks like.
- what the finding ecents do is, if it finds a data according to the data identifiers, it sends that data to the eventbridge managed service, like lambda and then lambda can perform certain action on that data.



![[Pasted image 20250410123312.png]]



![[Pasted image 20250410123516.png]]

- after macie is enabled, thats when the policy changes in the S3 bucket can be made to acknowdlege insid ethe policy finding.
- these are security chnges to the policy of the S3

