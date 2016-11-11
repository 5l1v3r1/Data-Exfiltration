Name : Abhishek Rajshekhar Rao

ASU ID : 1210425135

Description :

* IP address, interface on which packet is to be sent, type of the message and the message to be sent is read as an input from the command line.

* IP address, interface, type of message is checked for invalid inputs , if so, the program stops the execution flow and quits.

* A random ID is generated for a particular message to be sent and each byte of the message is sent in one packet.

* Hex value of Each byte of the message(reffering to the code :hexval )and the random ID (reffering to the code :hexRandom )is found and concatenated. The concatenated value is converted to decimal(reffering to the code :decval) and is set in identification flag of the IP packet.

* The length of the message is incremented for each byte and corresponding hex value is found and converted to decimal(reffering to the code :fragpos ) and is set in fragment offset flag of the IP packet.

* The same procedure is repeated for all the bytes of the message and packets are sent successively.

* At the end, when all packets are done, the data is set as zero and concatenated with the hex value of the random ID and converted to decimal and is set in identification flag of the IP packet. The highest bit of the fragment offset flag is set to 1 and the length of the message is appended and the corresponding decimal value is found and is stored.

*The Ip packets are sent as an ICMP message or TCP SYN packet to port 80 or UDP packet to port 53 according to the type of the message.