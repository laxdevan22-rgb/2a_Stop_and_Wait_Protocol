# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
## SimpleServer.py:
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for connection...")
conn, addr = s.accept()
print("Connected to", addr)

while True:
    data = conn.recv(1024).decode()
    if not data:
        break

    print("Frame received:", data)
    conn.send("ACK".encode())

conn.close()
```
## SimpleClient.py:
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

n = int(input("Enter number of frames: "))

for i in range(n):
    msg = input("Enter frame: ")
    s.send(msg.encode())

    ack = s.recv(1024).decode()
    print("Received:", ack)

s.close()
```
## OUTPUT
## SimpleServer:

<img width="1432" height="325" alt="694351333-903695f2-cc1d-4f04-a76a-b9e61290baf6" src="https://github.com/user-attachments/assets/777a1941-2884-4681-8af2-ab0ec2e0c2bb" />

## SimppleClient.py:
<img width="1440" height="402" alt="694351795-50d6f101-887b-4c2a-afed-7204297a7c5b" src="https://github.com/user-attachments/assets/151aa98a-4db8-4e64-affb-295834428757" />



## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
