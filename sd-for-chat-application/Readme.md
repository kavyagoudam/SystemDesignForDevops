# What is Whatsapp?

Whatsapp is a chat application that provides instant messaging services to its users. it is one of the most used mobile applications on the planet connecting over 2 billion users in 180+ countries. Whatsapp also available in web.

# Requirements

Funcional requirements:-
1. Should support one - on - one chat
2. Group chats
3. should support file sharing

Non Functional requirements:-
1. High availability with minimal latancy
2. the system should be scalable and efficient

Extended Reuirements:-
1. Sent Delivered and read receipts of the messages
2. show the last seen time of users
3. push notiofications

Estimation and Constraints:-

# Traffic

    Let us assume we have 50 million daily active users(DAU) and on average each user sends at least 10 messages to 4 different people everyday. this gives us 2 billion messages per day

```
50 million * 20 million = 2 billion/day
```

Messages can also contain media such as images videos ot other files. we can assume that 5 percent of messages are media files shared by the users, which gives us additional 200 million files we would need to store.

```
5 percent of 2 billion = 200 million/day
```
# what would be requests per second(RPS) for our system?

2 billion requests per day translate into 24k reuests per second.
```
2 billion / (24 hrs * 3600 seconds) = 24k requests /second
```

# storage
 if we assume each message on average is 100 bytes, we will require about 200 GB of database storage everyday.
```
2 billion *100bytes = ~ 200GB/day
```
  As per our requirements, we also know that around 5 percent of our dailt messages(100 million) are media files. if we assume each file is 50KB on average, we will require 10TB of storage every day.

```
100 million * 100KB = 10TB
```
And for 10 years, we will require about 38PB of storage.
```
(10TB + 0.2TB)*10 years* 265days = ~ 38PB
```

# Bandwidth
AS our system is handling 10.2TB of ingress everyday, we will require a minimum bandwidth of around 120MB seconds.

```
10.2TB/(24hrs*3600seconds)=~120MB/second
```
## High level estimation

Here os our high-level estimate

![image](https://github.com/user-attachments/assets/53cc0cb5-2989-4744-8b01-daa916f9133f)


## Data model design
This is the general data model which reflects our reuirements.

![image](https://github.com/user-attachments/assets/c46356ec-082e-45d7-a256-ef9212c363a7)

We have the following tables:
### users
this table will contains a users information such as name phonenumber, and other details.
### messages
this tables will store messages with properties such as type(text, image, video, etc), contect, and timestampls for messages delivery. the message will also have a corresponding chatID or GroupID.

### chats
This table basically represents a private chat between two users and can contain multiple messages

### users_chats

This table maps users and chats as multiple users can have multiple chats(N:M relationship) and vice versa

### groups:
 This table represents a group between multiple users
### users_groups
 This table maps users and groups as multiple users can be a part of multiple groups(N:M relationship) and vice versa.

 ## What kind of Detabase should we use?
  While our data model seems quite relational, we don't neccessarily need to store everything in a single database, as this can limit out scalability and quickly become a bottleneck.
  We will split the data between different services each having ownership over a particular table, then we can use a relational database such as PostgerSQK or a distributed NoSQL databse such as Apache Cassandra for our case.

## API Design
Let us do a basic API design for our services:

### Get all chat or Groups
Thhis API will get all chats or groups for a given userID.

```
getAll(userID:UUID):chat[] | Group[]
```

User ID (UUID): ID of the current user.

Returns:- Result (Chat[] | Group[]): All the chats and groups the user is a part of.

### Get messages
Get all messages for a user the channelID (chat or group id).

```
getMessages(userID: UUID, channelID: UUID): Message[]
```
User ID (UUID): ID of the current user.
Channel ID (UUID): ID of the channel (chat or group) from which messages need to be retrieved.
Returns:- Messages (Message[]): All the messages in a given chat or group.

### Send message
send a message from a user to a channel(chat or group)
```
sendMessage(userID: UUID, channelID: UUID, message: Message): boolean
```
User ID (UUID): ID of the current user.
Channel ID (UUID): ID of the channel (chat or group) user wants to send a message to.
Message (Message): The message (text, image, video, etc.) that the user wants to send.
Returns:- 
Result (boolean): Represents whether the operation was successful or not


### Join or leave a group
Send a message from a user to a channel.

```
joinGroup(userID: UUID, channelID: UUID): boolean
leaveGroup(userID: UUID, channelID: UUID): boolean
```
User ID (UUID): ID of the current user.
Channel ID (UUID): ID of the channel (chat or group) the user wants to join or leave.

Returns:-Result (boolean): Represents whether the operation was successful or not

## High-level Design

Now let us do a high-level design of our system

### Architecture
We will be using "microservice architecture" since it will make it easier to horizontally scale and decouple our service. each service will have ownership of its own data model.
lets try to divide our system into some core services.

#### UserService
This is an HTTP-based service that handles user-related concerns such as authentication and user information.

#### Chat Service

this chat service will use WebSockets and establish connections with the client to handle chat and group message-related functionality. we can also use cache to keep track of all the active connections sort of like sessions which will help us determine if the user is online or not.

#### Notification Service
This service will simply send push notification to the users. it will be discussed in detail seperately.

#### Presence Service
This presence service will keep track of the last seen status of all users. it will be discussed in detail separately.

#### Media service
This service will handle the media uploads. it will be discussed in detail separately.


### What about inter-service communication ans service discovery?

Since our architecture is microservies-based, services will be communicating with each other as well, Generally REST or HTTP performs will but further improve the performance using gRPC which is more lightweight and effifient.

Service Discovery is another thing we will have to take into account. We can also use a service mesh that enables managed, observable and secure communication between individual services.

### Real-Time messageing

How do we efficiently send and receive messages? we have two different options:

Pull Model

The client can periodically send HTTP request to servers to check if there are any new messages. this can be achieved via something like Long Polling.

Push model

The client a long-lived connection with the server and once new data is available it will be pushed to the client. we can use WebSockets or Server-sent-Event(SSE) for this

The pull model approach is not scalable as it will create unnecessary request overhead on our servers and most of the time the response will be empty, thus wasting our resources. To minimize latency, using the push model with WebSockets is a better choice because then we can data to the client once its available without any delay given the connection is open with client, Also WebSockets provide full-duplex communicaiotn unlike Server-sent Events, which are only unidirectional.


### Last seen

To implement the last seen functionality, we can use a heartbeat mechanism, where the client can periodically ping the servers indicating its liveness, Since this needs to be as low overhead as possible, we can store the last active timestamp in the cache as follows.


![image](https://github.com/user-attachments/assets/edf90c4c-820a-4bf7-bf0d-3ef42d28b022)

This will give us the last time the user was active, this functionlity will be handled by the presence service combined with Redis or Memcached as our cache.

Another way to implement this is to track the latest action of the user, Once the last activity crosses a certain threshold, such a "user hasn't performed any action in the last 30 seconds". We can show the user as offline and last seen with the last recorded timestamp. This will be more of a lazy update approach and might benefit us over heartbeat in certain cases.















