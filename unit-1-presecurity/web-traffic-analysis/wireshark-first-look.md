Wireshark: Cleartext vs Encrypted Traffic

Part A: HTTP capture

1. Username and password

Username: anna.virtanen

Password: Summer2026!

The credentials were visible in the HTTP stream:

The whole line:
username=anna.virtanen&password=Summer2026!&remember=on


2. HTTP method

The login was submitted using GET.

Relevant line from the HTTP stream:

The line:
GET /login HTTP/1.1


3. SESSIONID cookie

The SESSIONID is:a3f9c2e7b81d4f60a5e2c9d10f4b7e88

Relevant line from the HTTP stream:

Set-Cookie: SESSIONID=a3f9c2e7b81d4f60a5e2c9d10f4b7e88; Path=/; HttpOnly

An attacker who captures a valid SESSIONID may be able to hijack the user's logged-in session without knowing the password.

4. Sensitive information

Two sensitive pieces of information visible on the dashboard are:

1. Role: Finance Administrator
2. Email: [anna.virtanen@pohjola-logistics.local](mailto:anna.virtanen@pohjola-logistics.local)

Relevant dashboard content:

Last login from 10.10.10.50

Part B: HTTPS capture

5. Username and password

The username and password aren't readable because HTTPS uses TLS (Transport Layer Security), 
which encrypts the HTTP content before it is sent over the network. 
This means that someone monitoring the network can see the encrypted packets, 
but they cannot normally read the username or password from them.

6. Server Name / SNI

The server name shown in the TLS handshake is:

lab-portal.local

7. Information still visible

An eavesdropper can still see the client and server IP addresses, 
connection timing and packet sizes, even though the HTTP contents are encrypted.

The client IP address is 10.10.10.50 and the server IP address is 10.10.10.10.

Part C: Making sense of it

8. Why does HTTP vs HTTPS matter for confidentiality?

HTTP sends data without encryption, while HTTPS encrypts the HTTP contents using TLS.

9. Untrusted network
Let’s say I use public Wi-Fi in a library. 
Someone on the same untrusted network could try to monitor my web traffic. 
If I am using an HTTP site, they could technically read the data sent between my device and the website, 
including information shown on the page and possibly login credentials. If I use HTTPS, 
TLS encrypts the contents of the connection, 
so the person monitoring the network cannot normally read most of the data I do not want to share, 
although some metadata such as IP addresses, 
connection timing, and packet sizes can still be visible.
