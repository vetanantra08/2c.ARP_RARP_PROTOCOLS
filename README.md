# 2c.SIMULATING ARP /RARP PROTOCOLS
## NAME:R.S.VETANANTRA
##REG NO: 212225040486
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("ARP Server is listening on port 8000...")
c, addr = s.accept()

address = {
    "165.165.80.80": "6A:08:AA:C2",
    "165.165.79.1": "8A:BC:E3:FA"
}

while True:
    ip = c.recv(1024).decode()
    print(f"Received IP: {ip}")
    mac = address.get(ip, "Not Found")
    c.send(mac.encode())

client

import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    ip = input("Enter Logical Address (IP): ")
    s.send(ip.encode())
    print("MAC Address:", s.recv(1024).decode())
## OUPUT - ARP
server
<img width="775" height="332" alt="Screenshot 2026-03-18 082510" src="https://github.com/user-attachments/assets/7eaf175e-994a-4f86-9a2a-25119266cee8" />
client
<img width="722" height="175" alt="Screenshot 2026-03-18 082526" src="https://github.com/user-attachments/assets/bc5f7fb8-4709-4a61-8745-5d7e03407502" />
## PROGRAM - RARP
server
import socket

s = socket.socket()
s.bind(('localhost', 8001))
s.listen(5)
print("RARP Server is listening on port 8001...")
c, addr = s.accept()

address = {
    "6A:08:AA:C2": "165.165.80.80",
    "8A:BC:E3:FA": "165.165.79.1"
}

while True:
    mac = c.recv(1024).decode()
    print(f"Received MAC: {mac}")
    ip = address.get(mac, "Not Found")
    c.send(ip.encode())

client
s = socket.socket()
s.connect(('localhost', 8001))

while True:
    mac = input("Enter Physical Address (MAC): ")
    s.send(mac.encode())
    print("IP Address:", s.recv(1024).decode())

## OUPUT -RARP
server
<img width="754" height="192" alt="Screenshot 2026-03-18 082740" src="https://github.com/user-attachments/assets/e6aa64ac-df8d-4e35-87e0-69810ed2dcb9" />
client
img width="693" height="112" alt="Screenshot 2026-03-18 082753" src="https://github.com/user-attachments/assets/8530da85-6044-4e8f-b137-877ad8a5f6ff" />
## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
