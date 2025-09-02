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
```
1) CLIENT
import socket

client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
client_socket.connect(('localhost', 9000))   # Connect to server

print("✅ Connected to server. Type 'exit' to close.")

while True:
    message = input("👉 Enter message: ")
    client_socket.send(message.encode())
    
    if message.lower() == "exit":
        print("❌ Closing connection.")
        break

    reply = client_socket.recv(1024).decode()
    print(f"💬 Server says: {reply}")

client_socket.close()
```
```
2) SERVER

import socket

# Create socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
server_socket.bind(('localhost', 9000))   # Bind server to port 9000
server_socket.listen(1)

print("✅ Server is running and waiting for connection...")

conn, addr = server_socket.accept()
print(f"🔗 Connected to {addr}")

while True:
    data = conn.recv(1024).decode()
    if not data or data.lower() == "exit":
        print("❌ Connection closed by client.")
        break
    print(f"📩 Received from client: {data}")
    
    response = f"Server received: {data}"
    conn.send(response.encode())

conn.close()
```

## OUTPUT

CLIENT 
<img width="1920" height="1200" alt="Screenshot (100)" src="https://github.com/user-attachments/assets/593a775c-e29e-4d8e-a474-b93560029b2a" />

SERVER
<img width="1920" height="1200" alt="Screenshot (99)" src="https://github.com/user-attachments/assets/5d7f1ed5-de0b-48f3-a0e3-343fd5bc1e32" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
