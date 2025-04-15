
![[Screenshot from 2025-03-30 18-19-22.png]]

![[Screenshot from 2025-03-30 18-20-25.png]]
- need to isntall agent
- create the config file or attach a pre made config file
- in the config file we mention which log files need to be sent through the agent
- we also mention if it needs to store basic metrics or advance
- we also mention where to store it, in the ssm store or the cloudwatch logs
- we would need to attach roles to access both the services.

## Steps
![[Screenshot from 2025-03-30 18-24-40.png]]

Install the agent:
![[Screenshot from 2025-03-30 18-24-45.png]]

Run the agent
![[Screenshot from 2025-03-30 18-24-52.png]]

Make a role:
![[Screenshot from 2025-03-30 18-25-35.png]]

Run the agent:
![[Screenshot from 2025-03-30 18-26-01.png]]

After config, where to store?
![[Screenshot from 2025-03-30 18-55-51.png]]


Files which would store the logs inside the instance:
![[Screenshot from 2025-03-30 18-57-59.png]]

Send the configs:

![[Screenshot from 2025-03-30 18-58-20.png]]

