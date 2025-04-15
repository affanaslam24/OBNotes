Difference between basic aurora arch and multi master
![[Pasted image 20250402160822.png]]

Its architecture is similar to the default aurora BUT
![[Pasted image 20250402161027.png]]

in this there is no load balanced read concept, in this any endpoint can be used for both read and write actions. And because of that each write in the data will be done to all the storage units at the same time. Now in this scenario there can be conflicts or errors, and i did not understand whatever all this was about because i lost focus.
Nexgt up, it also replicates those changes or somwthing like a log to the other instances working, so that the memory is up to date and no dispenseriaes occurs.


Difference between this and the single master Aurora?

better availibility and fault tolerance.
In single master aurora, if the cluster endpoint goes down, then the replica instance takes its time to become reader and write endpoint, and that takes times. which is not really fault tolerant.
But with multi master, all the instances are ready to read and write,  adn since each instance is not dependant on other, its not only fault tolerance, but the no distruption in read and write provides a huge availibilty remark.

