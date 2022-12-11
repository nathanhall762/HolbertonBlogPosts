# What happens when you type holbertonschool.com in your browser and press Enter

<img src="/Untitled design (45).jpg" alt="Web Dev Blog Post Graphic"/>

Have you ever wondered what happens behind the scenes when you type a URL into your web browser and press Enter? This blog post will describe, in detail, each step that occurs when a person uses their web browser to go to a website.

From requesting the IP address of the website from the Domain Name System (DNS), to sending an HTTP GET request to the web server, to receiving data packets and building the webpage, there are many steps involved in the process of accessing a website. This blog post will provide a comprehensive overview of each of these steps, explaining how they work and how they fit together to allow you to access your favorite websites.

## DNS: I have a name, I need an address
When a web client (i.e. a web browser) needs to access a website, the first step in the process is to request the IP address of the website from the Domain Name System (DNS).

The DNS is a global network of servers that is responsible for mapping domain names (e.g. example.com) to their corresponding IP addresses (e.g. 192.0.2.1). This allows web clients to access websites using the familiar and easy-to-remember domain names, rather than having to remember the complex numerical IP addresses of each website.

When a web client needs to request the IP address of a website from the DNS, it first checks to see if the IP address is already cached in its local DNS cache. This is a temporary storage area on the web client's computer that holds the IP addresses of recently accessed websites. If the IP address is found in the local DNS cache, the web client can use that address to access the website.

If the IP address is not found in the local DNS cache, the web client must send a DNS query to the DNS server. A DNS query is a request for information that is sent to the DNS server. The query includes the domain name of the website that the web client is trying to access.

The DNS server receives the query and processes it. It first checks to see if it has the requested IP address in its own cache. If it does, it sends the IP address back to the web client in a DNS response.

If the DNS server does not have the requested IP address in its cache, it must forward the query to other DNS servers in order to find the IP address. This process is called DNS recursion, and it involves the DNS server sending the query to a series of other DNS servers in a hierarchical manner until the IP address is found.

Once the DNS server has found the IP address, it sends it back to the web client in a DNS response. The web client can then use that IP address to access the website.

## TCP/IP: Can you hear me now?
Once the IP address is determined, the browser sends a TCP SYN (synchronize) packet to the server. This packet contains the IP address of the browser and the port number that the browser wants to use for the connection.

The server receives the SYN packet and responds with a TCP SYN-ACK (synchronize-acknowledge) packet. This packet contains the IP address and port number of the server, as well as a unique number that is used to identify the specific connection.

The browser receives the SYN-ACK packet and responds with a TCP ACK (acknowledge) packet. This packet contains the same unique number that was received in the SYN-ACK packet, and is used to confirm that the connection has been established.

Once the connection has been established, the browser can send HTTP requests to the server and the server can respond with the requested web page.

## "Can I make a request?"
HTTP (Hypertext Transfer Protocol) is a communication protocol that is used to transfer data between a web server and a web client. The most common type of HTTP request is the GET request, which is used to request data from a server.

When a web client sends an HTTP GET request to a web server, it includes the URL of the website it is trying to access, as well as other information such as the type of browser being used and the type of data that the client is expecting to receive.

For example, if a web client wants to access the website https://holbertonschool.com, it might send the following HTTP GET request to the web server:
```
GET / HTTP/1.1
Host: holbertonschool.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.111 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9

```
The first line of the request (GET / HTTP/1.1) specifies the type of request (GET) and the URL of the website being accessed (/). The other lines of the request provide additional information about the web client and the type of data it is expecting to receive.

## Firewall
When a web client (such as a web browser) makes an HTTP request to a web server, the server's firewall is responsible for controlling access to the server and its resources. The firewall uses a set of rules to determine whether to allow or deny the request based on the IP address, port, and other characteristics of the request.

If the request is allowed by the firewall, it is forwarded to the web server. The server then processes the request and sends a response back to the client.

If the request is denied by the firewall, the server will not receive the request and the client will receive an error message. The specific error message and behavior will depend on the configuration of the firewall and the web server.

## Response
Once the web server receives the HTTP GET request, it processes it and generates a response. If the request is valid and the server has the requested information, it sends the response back to the web client. The response typically includes the data that the web client requested, as well as other information such as the type of data being sent and the status of the request.

For example, if the web server responds to the HTTP GET request with the following data:
```
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 23

<h1>Hello, World!</h1>
The first line of the response (HTTP/1.1 200 OK) indicates the type of response (HTTP) and the status of the request (200 OK). The other lines of the response provide additional information about the data being sent (Content-Type: text/html) and the length of the data (Content-Length: 23). The final line of the response contains the actual data that the web client requested (<h1>Hello, World!</h1>).
```

In some cases, the web server might not be able to fulfill the web client's request. For example, if the web client requests a URL that does not exist on the server, or if the server is unable to process the request for some other reason, the web server will return an error response instead of the requested data.

For example, if the web client sends the following HTTP GET request:
```
GET /invalid-url HTTP/1.1
Host: example.com
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/86.0.4240.111 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
```

The web server might respond with the following data:
```
HTTP/1.1 404 Not Found
Content-Type: text/html
Content-Length: 35

<h1>404: Page Not Found</h1>
```

When a web server returns a response to a web client, it sends the response in the form of data packets. These packets are small chunks of data that are sent over the network and reassembled by the web client in order to build the webpage.

Each packet contains a small amount of data, typically around 1,500 bytes. This allows the packets to be transmitted efficiently over the network, even if the network is congested or has a low bandwidth.

When a web server sends a response to a web client, it sends the response as a series of data packets. Each packet is sent individually, and the web client must reassemble the packets in order to recreate the original response.

Each packet is sent individually to the web client, and the web client must reassemble the packets in order to recreate the original response.

In order to ensure that the packets are delivered to the web client in the correct order, each packet includes a sequence number. The sequence number indicates the position of the packet in the overall response, and the web client uses this information to reassemble the packets in the correct order.

For example, the packets might include the following sequence numbers:
```
Packet 1:
HTTP/1.1 200 OK
Content-Type: text/html
Content-Length: 23

Sequence Number: 1

Packet 2:
<h1>Hello, World!</h1>

Sequence Number: 2
```

## Piecing it all together
When a web client receives data packets from a web server, it uses those packets to build the webpage that the user is trying to access. This involves rendering the HTML, CSS, and JavaScript that make up the website, as well as downloading any images, videos, or other media that are included on the page.

When the web client receives a data packet from the web server, it first checks the sequence number of the packet to determine its position in the overall response. The web client maintains a buffer that holds the packets as they are received, and it inserts each packet into the buffer in the correct order based on its sequence number.

Once all of the packets have been received and placed in the buffer, the web client can begin to process the data and build the webpage. This typically involves the following steps:

The web client parses the HTML in the data packets to identify the different elements of the webpage (e.g. text, images, links, etc.).

The web client applies the CSS styles in the data packets to the HTML elements in order to determine their appearance on the page.

The web client executes the JavaScript code in the data packets, which can modify the HTML elements or add additional functionality to the webpage.

The web client downloads any images, videos, or other media that are included in the data packets and displays them on the webpage.

Once the web client has processed all of the data packets and built the webpage, it displays the webpage to the user. The user can then interact with the webpage, clicking on links, filling out forms, or performing other actions.

## Conclusion
In conclusion, accessing a website involves many steps and technologies working together. From requesting the IP address of the website from the DNS, to sending an HTTP GET request to the web server, to receiving data packets and building the webpage, each step plays a crucial role in allowing you to access the information you need. Understanding how these steps work can help you to appreciate the complexity and power of the web, and can also help you to diagnose and troubleshoot problems that may arise when accessing websites.

### Bonus! Secure communication between client and server with HTTPS
When a web client (such as a web browser) communicates with a web server using HTTPS (Hypertext Transfer Protocol Secure), it uses the Secure Sockets Layer (SSL) protocol to establish a secure, encrypted connection. This ensures that the data exchanged between the client and server cannot be intercepted or tampered with by third parties.

Here is a step-by-step breakdown of how a web client uses HTTPS/SSL to communicate with a web server:

The client initiates an HTTPS connection by sending a request to the server. This request includes the desired URL and other HTTP headers, as well as a request for the server to establish an SSL connection.

The server responds by sending its SSL certificate to the client. This certificate contains information about the server's identity, including the server's public key.

The client verifies the server's certificate to ensure that it is authentic and has not been tampered with. If the certificate is valid, the client generates a symmetric key and sends it to the server encrypted with the server's public key.

The server receives the encrypted key and uses its private key to decrypt it. Once the key is decrypted, both the client and server use it to encrypt and decrypt all further communication.

The client and server can now communicate securely, with all data being encrypted and decrypted using the shared symmetric key.

### Bonus Bonus: Things about a web server I couldn't fit into the main blog post
In the context of a web server, a load balancer is a critical component that helps to distribute incoming requests among multiple servers in order to improve the performance and reliability of the system. This is especially important for high-traffic websites, where a single server may not be able to handle the volume of requests on its own.

A load balancer works by receiving incoming requests and then forwarding them to one of the web servers in its pool. This is typically done using a load-balancing algorithm, which determines which server to send the request to based on factors such as the server's current load, the type of request, and other factors.

In addition to the load balancer, a web server is the core component of the system. This is the server that actually receives the incoming requests from the load balancer and responds by sending the requested web page or other resource back to the client.

An application server is a type of server that is designed to run specific applications or services that are required by the web server. This can include things like web application frameworks, middleware, and other services that are needed to support the web server's operations.

Finally, a database is a crucial component of many web server systems. This is where the web server stores and retrieves the data that is used to generate the web pages and other resources that it serves to clients. A database typically uses a structured query language (SQL) to manage and access the data, and can be optimized for the specific needs of the web server.
