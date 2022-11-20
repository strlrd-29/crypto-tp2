## Cryptography Practical Tutorial 2

This is the second practical tutorial for the course "Cryptography", the goal of this tutorial is to implement a simple protocol for secure communication between two parties. The protocol is based on websockets.

## Folder Structure

The workspace contains two folders by default, where:

- `src`: the folder to maintain sources
- `lib`: the folder to maintain dependencies

Meanwhile, the compiled output files will be generated in the `bin` folder by default.

## Client-Side Programming

### Establish a Socket Connection

To connect to another machine we need a socket connection. A socket connection means the two machines have information about each other’s network location (IP Address) and TCP port. The java.net.Socket class represents a Socket. To open a socket:

```java
Socket socket = new Socket("127.0.0.1", 8080);
```

- The first argument – IP address of Server. ( 127.0.0.1 is the IP address of localhost, where code will run on the single stand-alone machine).
- The second argument – TCP Port. (Just a number representing which application to run on a server. For example, HTTP runs on port 8080. Port number can be from 0 to 65535)

### Communication

To communicate over a socket connection, streams are used to both input and output the data.

### Closing the connection

The socket connection is closed explicitly once the message to the server is sent.

_In the program, the Client keeps reading input from a user and sends it to the server until “Over” is typed._

### Java Implementation

go to file [Client.java](src/Client.java)

### Establish a Socket Connection

To write a server application two sockets are needed.

- A ServerSocket which waits for the client requests (when a client makes a new Socket())
- A plain old Socket to use for communication with the client.

### Communication

getOutputStream() method is used to send the output through the socket.

### Close the Connection

After finishing, it is important to close the connection by closing the socket as well as input/output streams.

### Important Points

- Server application makes a ServerSocket on a specific port which is 8080. This starts our Server listening for client requests coming in for port 8080.

- Then Server makes a new Socket to communicate with the client.

```java
socket = server.accept()
```

- The accept() method blocks(just sits there) until a client connects to the server.
- Then we take input from the socket using getInputStream() method.
- Our Server keeps receiving messages until the Client sends “Over”.
- After we’re done we close the connection by closing the socket and the input stream.
- To run the Client and Server application on your machine, compile both of them. Then first run the server application and then run the Client application.

