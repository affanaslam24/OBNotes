### Limitations:
- Storing the pictures in wp-content
- and the metadata of the post at the local db that we configured.

### Steps
1. we will be configuring the parameter store:
![[Screenshot from 2025-04-07 12-20-27.png]]
![[Screenshot from 2025-04-07 12-20-43.png]]
![[Screenshot from 2025-04-07 12-20-55.png]]
![[Screenshot from 2025-04-07 12-21-11.png]]
![[Screenshot from 2025-04-07 12-21-39.png]]


REMember: IN sessions manager, we connect using **sudo bash**
![[Screenshot from 2025-04-07 12-22-49.png]]

#### STEP1:
Configuring the env variables:
![[Screenshot from 2025-04-07 12-23-16.png]]
#### Step 2:
DOwnload all the tools- apache, mariadb, php, docker, etc.

#### STEP 3:
Start adn enable the services:
![[Screenshot from 2025-04-07 12-24-58.png]]

#### Step4:
Set up the database server:
![[Screenshot from 2025-04-07 12-25-10.png]]

#### STEP 5:
Download the wordpress file in a folder and remove the files after unzipping them:
![[Screenshot from 2025-04-07 12-26-19.png]]
![[Screenshot from 2025-04-07 12-26-30.png]]

#### STEP 6:
Configure the wp-config file:
![[Screenshot from 2025-04-07 12-26-45.png]]

### STEP 7:
Give adequate permissions:
![[Screenshot from 2025-04-07 12-26-58.png]]

#### STEP 8:
SET up the database config file and then push it to the database:
![[Screenshot from 2025-04-07 12-27-15.png]]


THATS it!!
ITLL be up and running.

![[Screenshot from 2025-04-07 12-30-49.png]]

This is the model.


