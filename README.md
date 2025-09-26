# 2c.SIMULATING ARP /RARP PROTOCOLS
# NAME: MOHAMED NIZAMUDDIN A
# REG NO: 212224040194
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between the client and the server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to the server.
5. Server returns the MAC address to the client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.

## PROGRAM - ARP
# CLIENT 
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
# SERVER 
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
``` 
## OUTPUT - ARP
<img width="1847" height="990" alt="image" src="https://github.com/user-attachments/assets/0bcce4e1-ead6-42d2-96b4-7e21920f7e58" />

## PROGRAM - RARP
# CLIENT
```
import socket 
s=socket.socket() 
s.bind(('localhost',9000)) 
s.listen(5) 
c,addr=s.accept() 
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}; 
while True: 
            ip=c.recv(1024).decode() 
            try: 
                c.send(address[ip].encode()) 
            except KeyError: 
                c.send("Not Found".encode())
```
# SERVER
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ")
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode())
```

## OUTPUT -RARP
<img width="1850" height="975" alt="image" src="https://github.com/user-attachments/assets/8a853ad4-2d01-4bf5-948b-b8e939be6571" />



## RESULT
Thus, the Python program for simulating ARP protocols using TCP was successfully 
executed.
