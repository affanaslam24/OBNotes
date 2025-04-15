![[Screenshot from 2025-03-29 14-51-13.png]]

management events are logs related to creation deletion, actions performed on the management area, but nothing to do with the data that passes thorugh, or the bandwithc or other things. 

![[Screenshot from 2025-03-29 14-53-31.png]]

what does cloudTraill do?
takes a service, global or regional, then checks for one region or all region, as per required by us, then checks for data events and management events and stores these logs in cloudwatch logs, or if configured can stpre in S3.

Also, the S3 created here will be visible to us, because the S3 will be configured by us
now, by default only management event 8is allowed, and i dont know which regions are allowed by default.

![[Screenshot from 2025-03-29 14-54-18.png]]

