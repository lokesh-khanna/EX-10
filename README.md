# EX-10 APPLICATION USING TCP SOCKETS - FILE TRANSFER PROGRAM

DATE :

AIM :
To write a python program for creating File Transfer using TCP Sockets Links.

ALGORITHM :
1. Start the program.
2. Get the frame size from the user.
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server, it will send ACK signal to client otherwise it
will sendNACK signal to client.
6. Stop the program

PROGRAM :

CLIENT:

import socket

s = socket.socket()

host = socket.gethostname()

port = 60000

s.connect((host, port))

s.send("Hello server!".encode())

with open('received_file', 'wb') as f:

while True:

print('receiving data...')

data = s.recv(1024)

print('data=%s', (data))

if not data:
break

f.write(data)

f.close()

print('Successfully get the file')

s.close()


print('connection closed')

SERVER:

import socket 

port = 60000 

s = socket.socket() 

host = socket.gethostname() 

s.bind((host, port)) 

REG NO:

s.listen(5) 

while True:

conn, addr = s.accept() 

data = conn.recv(1024)

print('Server received', repr(data))

filename='mytext.txt'

f = open(filename,'rb')

l = f.read(1024)

while (l):

conn.send(l)

print('Sent ',repr(l))

l = f.read(1024)

f.close()

print('Done sending')

conn.send('Thank you for connecting'.encode())

conn.close()

OUTPUT :
client : ![7client](https://github.com/lokesh-khanna/EX-10/assets/119606216/1b3877c9-fe00-4f55-ae61-a3c95e08b4d6)

server :![7server](https://github.com/lokesh-khanna/EX-10/assets/119606216/629c73a5-cf28-480b-81db-a94e03ce1519)

RESULT :
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed
