                                                                  PROJECT SCENARIO
<img width="522" height="167" alt="image" src="https://github.com/user-attachments/assets/1e33f87b-f8e0-409c-98bc-a04b92b3f518" />

                                                TASK 1: Explore Wireshark’s interface and key features
THIS WAS A BASIC INTRODUCTION OF THE TOOL AND EXPLORATION OF IT:
•	Familiarity with the interface of analysis tools like Wireshark is crucial for effective and efficient workflows.
•	While tool interfaces may evolve over time, understanding the foundational structure makes adapting to updates easier.
•	Learning to organize your workspace and use shortcuts enhances productivity when analyzing large datasets.

                                               TASK 2: Capture and save live traffic
ANALYSED TRAFFIC BY USING CHROME AND SEEING HOW LOGS BE SHOWN:
<img width="624" height="184" alt="image" src="https://github.com/user-attachments/assets/58a611fc-b625-41a1-873d-616c14c08690" />

TO CHECK THE MADE REQUEST, WE USE dns.qry.name == "facebook.com", source is our system and destination is the DNS server who when we ask for the IP address of facebook.com he replies with a DNS query giving us the IP address, to confirm if our browser made request to this domain:
<img width="624" height="147" alt="image" src="https://github.com/user-attachments/assets/15422ea3-6692-4e34-a92d-41c64f2a5773" />

As we find the IP address, hence to see if the domain was accessed we confirm by filtering through its IP:
<img width="624" height="162" alt="image" src="https://github.com/user-attachments/assets/30babff3-e12b-46cc-9662-625446af626d" />

                                               TASK 3: Filter Captured Data

I tried filtering by host, this is when we confirm did my browser actually send a request to this domain:
<img width="624" height="360" alt="image" src="https://github.com/user-attachments/assets/bb4df1f7-169e-4f17-814a-3f41d165cade" />
<img width="624" height="135" alt="image" src="https://github.com/user-attachments/assets/aba04db2-f556-4892-9ec6-5f675d714b6e" />

played around with filtering:
<img width="624" height="120" alt="image" src="https://github.com/user-attachments/assets/76bc07b8-13f4-4601-8e57-fffba757be6e" />

                                               TASK 4: ANALYZE TRAFFIC FOR SECURITY THREATS:

We cover these 3 detection tasks:
•  Spotting SYN flood attacks, TCP packets having SYN flags set and no ACK flag set, Many UDP packets with either no response or lots of ICMP port-unreachable replies, different sources sending to same destination.
<img width="624" height="191" alt="image" src="https://github.com/user-attachments/assets/a4320b3f-9d1b-4c05-9ba7-3d92c607b4cd" />

•  identifying malformed packets (protocol violations or evasion attempts) eg Packets where header fields don’t match lengths (e.g., IP total length smaller than header size).
( frame smaller then standard ethernet 64 bytes ).
we go to Analyze → Expert Information.
See if Wireshark flags these frames as:
“Malformed”
“Checksum error”
“Truncated”
<img width="624" height="141" alt="image" src="https://github.com/user-attachments/assets/953459be-1fdb-431c-bf16-1cbfacf68d4b" />

•  finding unusual ports or protocols (anomalous services or covert channels)
filters like these help us to find uncommon ports:
<img width="624" height="65" alt="image" src="https://github.com/user-attachments/assets/3fbcdd99-e256-4eb2-961d-43a325292952" />
TCP port 25556 is not a standard service port, SYN with no reply makes it suspicious, frame length is less as well
<img width="624" height="241" alt="image" src="https://github.com/user-attachments/assets/3270b0dd-c2f1-4c50-bbab-11d5b65fe112" />


                                                      TASK 5: PRACTICAL ANALYSIS OF A TCP SYN FLOOD ATTACK
It is a DOS TECHINIQUE TO EXPLOIT TCP PROTOCOL ATTACKER SEND TCP PACKETS With SYN FLAG SET TO TAGRTE SERVER BUT ATTACKER NEVER COMPLETES THE HANDSHAKE AND SERVER RESOURCES ARE LOSED AND IT CRASHES EVENTUALLY. 
Different source IPs are sending packets to destination:
<img width="624" height="143" alt="image" src="https://github.com/user-attachments/assets/7735911b-c15b-4f5c-a8fe-1a8688c371f5" />

So as the dest port is same we can see that it is targeting a specific service and it shows seq 0 which means connection never completed:
<img width="370" height="164" alt="image" src="https://github.com/user-attachments/assets/f8617765-22d7-4681-911e-68fecec8bcb8" />

In the statistics I/O graphs we can see the spike in the SYN packets as well
<img width="624" height="398" alt="image" src="https://github.com/user-attachments/assets/889302b3-a729-4ab6-82a5-14dd7007773e" />

In statistics, converstaions we can see the communication between IP packets
<img width="624" height="295" alt="image" src="https://github.com/user-attachments/assets/07b8c70e-4a85-4d63-8db3-d384c33a77a6" />
















