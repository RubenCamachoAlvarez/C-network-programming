To start the development of an network application using the C programming language, we must to know about the following fundamentals.

The C sockets API is a set of header files, as well as its implementations, that provides computational abstractions to deal in an easier way with the communication between two or more computers that are connected directly (e.g. in the same network) or indirectly (e.g. in differents networks).

In the socket API, each end point of an connection between devices are represented using the concept of "socket", which is nothing more that an computational abstraction that represents the access point in each end, respectively, to the data flow between the devices.

At this point is important to remark that in the modern computer network applications, are mainly two architectures:

- Client-server architecture.
- Peer-to-Peer archicture.

The former represents network applications in which there is only one server that awaits until one or more clients connect to it, and it mainly purpose is to provide a service to the client, for example, sending the enough (or necessary) files to represent a web page in a web browser on the client, or sending the required bytes to watch a video through the Internet, etc.

The later refers to network applications which not use a centralized model, that is, there is not the classic concept about only one server and several clients which attempt to connect to him. Instead, in each Peer-to-Peer (P2P) network application each device (for example a computer, a smartphone, laptop, etc.) is represent by a node in the application network, and each node communicates with the other ones. Thus, in a P2P application, each node represents both a server and a client at the same time. For that, the nodes often are called as a servent, which is a combination of the words "Server" and "Client".

Now, the most use architecture today is still the Client-Server architecture which is present in everything, from bank services, social media, video-on-demand (VOD) platforms like Youtube, Netflix, Amazon Prime Video, Max, etc.

Essentially, when we want to create a new network application, we start by creating a new socket.

In the case of Client-Server application, there is "two types" of sockets. The socket that represents the client, and the socket that represents the server.
In fact, there is not two different types of sockets, instead there is only one type of socket that can be use in different ways  depending on the context in which it will be used.

For example, if we are coding the client-side application, we first will create the new socket, and then we will specified to the new socket the address and port of the server to established a connection and transfer information between the host.

If we are coding the server-side application, we will create the new socket, and then we specified the port that will be used by the computer to pass the data send by the client to the server(server-side incoming data), as well the data send by the server to the client (server-side outcoming data). Also, we tell to the socket from what devices the socket must accept established a new connection and from what devices not. Finally we indicate the maximum number of requests that will be queued to be handled as appropiate by the server.

At the end, we only need to put a infinite loop and within of it call the function accept() which will unblock the execution flow and return the integer descriptor that references the client socket of the incoming request that is being handled.

**Fundamental headers, functions and data types for networking using the UNIX socket API**

**Header files**

- sys/types.h
- sys/socket.h
- netinet/in.h
- arpa/inet.h

**Functions**

- sock() -> Creates a new socket on the underlying UNIX system and returns an integer descriptor represent the descriptor or the handle of the socket created. If this function returns a negative integer value, then the function failed to create the requested socket.
- htons() -> This function translates the local host representation of an 16-bit (short) integer value to the correct 16-bit (short) network representation, so this data can be send correctly through the network to the destination hosts.
- ntohs() -> This function translates the network representation of an 16-bit (short) integer value to the 16-bit local host representation, so in this way the value can be read or write propertly on the current machine.
- htonl() -> This function translates the local host representaton of an 32-bit integer value to their 32-bit network representation.
- ntohl() ->This function translates the network representation of an 32-bit integer value to their 32-bit local host representation.
- memset() ->This mainly purpose of this functions is to set all memory bytes of the given object with the specified value while called the function.
- inet_pton() ->This function translate the network address pointed by a char pointer to their 32-bit integer value as a network representation.
- inet_ntop() -> This function translate the 32-bit integer value network representation to their respectively local host string representation pointed by a char pointer.
- connect() -> This function is used to attempt to make a connection on a socket. This function recieved as arguments the file descriptor to the socket, the memory address to sockaddr object which store the peer address, and the length of the sockaddr structure passed as a second argument.
  
  If the connection is established sucessfully, then the function returns 0, otherwise it shall returns -1 and set the errno variable to indicate the error.
  
  Is important to remark that the socket in use may require the process to have appropiate privileges to use the **connect()** function.

- send() -> This function is used to initiate the transmission of a message from the specified socket to its peer. This function shall send the message only when the socket is connected via the **connect()** function (including when the peer of a connectionless socket has been set).
  
  This function takes the following arguments.
  
	- **socket**: This arguments specifies the socket file descriptor that will be use to convey/transmit the message.
	- **buffer**: A char pointer to point the buffer containing the message to send.
	- **length**: This argument specifies the length of the message measured in bytes.
	- **flags**
  
- recv()
- close()
- bind()
- listen()
- accept()

**Data types**

- in_port_t
- struct sockaddr
- struct sockaddr_in
- socklen_t
- ssize_t

**Symbolic constants**

- BUFSIZE
