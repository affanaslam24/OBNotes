- EventBridges are superset of cloudwatchEvents, and can be used with other 3rd arty or custom apps as well.



![[Pasted image 20250408110635.png]]
- events pass through **Event bus**
- Rules are configured, and if the events inside the busses matches the rules configured, then they are routed to 1 or more **targets**.
- instead of rules you can also configure hcedules, which are basically patterm matchinng config for time related scheduling. like the unix cron scheduling.

![[Pasted image 20250408111023.png]]
- so you can generate event  busses for services that support the event bridge service, like ec2.
- and in this scenario, an instance changing state will generate an event.
- the event is then read or managed by the eventbridge, and if it matches the **Event pattern rule** or the **Schedule based rule** then the eventbridge invokes the target, here it is lambda.
- now, the events are JSON scripted, and it contains all the data about the event, what changes accoured, whta the current status, the date, time and everything necessary, which the Lmabda or any target can acess.



NOTE; if there are more than one targets, they are sent the events in any order. 