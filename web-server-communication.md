# Web server communication

## HTTP communication

In a standard http web request, The client opens a web connection and request data from server. The server then process the request and send builds the response. and Finally server send the response back to the client.

## Polling

Polling is the standard technique which is used by the mejority of ajax applications. The client repeatedly pulls or request a server for data. The client makes a request and waits for the server to respond with data. and if no data is available an empty response will return.

### how it works

1. The client opens a connection and requests data from the serverusing HTTP protocol.
2. The server calculates the response and send back to client.
3. The client send request to the server at regular intervels.


Disadvantages:
1. The client has to keep asking server for new data. Which results to lot of new connection and responses are empty. This creates HTTP overhead.


 ## HTTP long polling

 The variation of polling technique is HTTP long polling.
 This allows the server to push information to client whenever the data is available.

### How it works?
1. the client request information to the server exactly as an reguler polling. But the expectation is that server may not respond immediately. This technique is also called Hanging Get.
2. If the server does not have any data available for the client. instead of sending an empty resonse. The server simply holds the request and waits untill some data
3. Once the data becomes available, a complete response is sent to the client.
4. Each long poll request has a timeout. Therefore the client has to reconnect periodically.

## Web sockets
Web Sockets can open unique connection open while eleminating the latency problems. Web sockets is a full duplex asynchronous messaging that is supported. Both the client and server can stream messages to each other independently.
Web sockets sends and receives the connection over TCP connections.

### How it works?
1. Client establishes websocket connection using websocket handshake.
2. if the respective server support the protocol it responds via header to complete the handshake.
3. Then a websocket connection replaces the handshake with same TCP connection
4. At this point both parties can start sending data.

When a web socket is used, A websocket handler will be connected by the user. Web socket handler is a lighweight server machine which keeps a open connection with all the active users.

Used in real time web application,example stock trading website, Chat application, Gaming application

Disadvantage:
1. it will be overkilled if you want to fetch the old data or data which is not fetched very frequently.

   
 
