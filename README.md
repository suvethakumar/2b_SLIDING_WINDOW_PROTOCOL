# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
SERVER
~~~
import socket 
s=socket.socket()
s.bind(('localhost',6000)) 
s.listen(5) 
c,addr=s.accept()
size=int(input("Enter number of frames to send : "))
l=list(range(size))
s=int(input("Enter Window Size : "))
st=0 
i=0
while True:
  while(i<len(l)): 
    st+=s 
    c.send(str(l[i:st]).encode()) 
    ack=c.recv(1024).decode() 
    if ack:
     print(ack)
     i+=s
~~~
CLIENT
~~~
import socket 
s=socket.socket() 
s.connect(('localhost',6000))
while True:
  print(s.recv(1024).decode())
  s.send("acknowledgement recived from the server".encode())
~~~
## OUPUT
<img width="1920" height="1080" alt="Screenshot 2026-05-21 161559" src="https://github.com/user-attachments/assets/aa2f5405-21f1-45f6-98ca-185cf46acda7" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
