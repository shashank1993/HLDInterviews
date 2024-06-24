# Live comments service

User journey
1. Comment only start when video start and end with video
2. User is seeing the video can see the live comments coming in
3. These comments keep coming without reloading
4. User can also post any comment while viewing video
5. After user post any comment they should be visible to 
    his page also and also to others in same order
   a. What will happen if my connectivity breaks - user should not be able to post
5. User seeing old video can see the old comments also



Problem of logic :
- Keeping posting as losely coupled with 

Estimations and Challenges : 
How many people checking comments - 1000_000 
Challenge #1 : Scale of broadcast (No of clients)
Challenge #2 : Number of messages at a time
Challenge #3 : Lag between writing messages and reading and also order on 2 machines

Estimates
1. Size of data for a comment


Q:  What happen to customer who joined in mid
Sol: Like snapshot, start getting latest and read older from backup copy


For writing logic, we have one solution
Problem:
- Numberof messages will be too high for one topic/ single partition


Kafka parameter:
((processing time for one message in seconds x number of msgs per second) / num of partitions) << 1
i.e producing rate and consuming rate for each partition should be same


When same single machine can consume all incoming messages load then why cant one partition handle it.
When consumer is ideally 1 then no need


Notes:
We will be needing websocket connection for incoming messages to client
