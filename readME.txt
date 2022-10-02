Submitted BY :-
	Aosenba longchar- 214101010
	Atul Bunkar - 214101011
	Ayon Chhattopadhya - 214101012

We have implemented 3 programs, namely, client.cpp, proxy_server.cpp and dns_server.cpp

To compile the 3 programs, open 3 different terminal windows and run the below commands, one in each window:

	$ g++ dns_server.cpp -o dns_server
	$ g++ proxy_server.cpp -o proxy_server
	$ g++ client.cpp -o client

Now, there will be 3 executable files dns_server, proxy_server, and client, that will be created.

While running dns_server.c we have to input the DNS server's port, running proxy_server.c requires us to input the Proxy Server's port, and while running client.c, we have to input the IP address and the Port of the proxy server. 

For simplicity, we can consider all the 3 programs to run on the local host, i.e. 127.0.0.1

We need to execute the programs in the order dns_server.c, proxy_server.c and client.c . We can choose some non-restricted port numbers for these programs, and we've taken ports 4000 and 4201 as an example.

To execute the 3 programs, we need to run the following commands, in the respective windows:

	$ ./dns_server 4000
	$ ./proxy_server 4201
	$ ./client 127.0.0.1 4201

This assigns the port number 4000 to the dns server, and 4201 to the proxy server, and tells the client program, the IP address(127.0.0.1) and the port number(4201) of the proxy server.

Next, we need to input the request(either IP address or Domain name) and the type of request(1 for requesting IP address, 2 for requesting Domain name) in the client program(Eg. www.google.com 1). 

If the proxy cache contains an entry corresponding to the requested domain name/IP address, the proxy server program sends back the data to the client program. 

If the proxy cache doesn't contain an entry corresponding to the requested domain name/IP address, then the proxy server will ask the user to input the DNS server's IP address and port number, which in our example are 127.0.0.1 and 4000 respectivly. After establishing a connection with the DNS server, the proxy server will now forward the request to the DNS server, which will check if there is an entry corresponding to the request. If there doesn't exist any entry, the DNS server sends a message(code 4) to the proxy server saying that it can't service the request, which the proxy server will forward to the client program.

If a corresponding entry exists, the DNS server will send the required data( along with code 3) to the proxy server, which will now update it's proxy cache using the FIFO algorithm, and then it forwards the data to the client program.

We have implemented the proxy cache and the DNS database as text programs with the names proxy_cache.txt and dns.txt
