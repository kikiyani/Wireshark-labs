Use a display filter to detect HTTPS packets:


<img width="624" height="193" alt="image" src="https://github.com/user-attachments/assets/8afe1b8b-4560-43af-825e-87968359d989" />




Visit a web page and detect its IP address using a display filter:
●A TLS handshake display filter may be used to detect a website visit in a packet list
●The IP address is used in a filter to obtain packet information for a particular website
<img width="624" height="195" alt="image" src="https://github.com/user-attachments/assets/275f6f1e-6db8-48b2-89bf-52e7f0dc5d22" />
<img width="452" height="179" alt="image" src="https://github.com/user-attachments/assets/3da99e32-7738-47d7-a673-e02f46fc7b03" />
<img width="624" height="168" alt="image" src="https://github.com/user-attachments/assets/8f103f81-827e-4cee-87e6-8b8474906f5d" />




( ip.src will show all all the results where the source ip address is the one as we specified)
<img width="624" height="202" alt="image" src="https://github.com/user-attachments/assets/3ae9aad7-9f03-4cb0-961b-832be8d10400" />






Locate all HTTPS packets from a capture not containing a certain IP address:
●A Conditional statement may be used to include and eliminate packets from a Wireshark capture
●A compound conditional should include parentheses to avoid order of execution errors
<img width="624" height="79" alt="image" src="https://github.com/user-attachments/assets/5b6f2ca1-8850-4c4d-b975-272b6843d19b" />
<img width="624" height="132" alt="image" src="https://github.com/user-attachments/assets/483a578a-7946-43cb-abd3-d9ac40835549" />

