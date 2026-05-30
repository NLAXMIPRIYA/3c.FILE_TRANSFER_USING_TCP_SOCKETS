# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS
## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM
```
server.py
import socket

port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)

print("Server listening on port", port)

while True:
    conn, addr = s.accept()
    print("Connected to", addr)
    
    data = conn.recv(1024)
    print('Server received', repr(data))

    filename = 'MyFile.txt'
    with open(filename, 'rb') as f:
        l = f.read(1024)
        while l:
            conn.send(l)
            print('Sent', repr(l))
            l = f.read(1024)
    
    print('Done sending')
    conn.send('Thank you for connecting'.encode())
    conn.close()




client.py
import socket

s = socket.socket()

host = socket.gethostname()
port = 60000

s.connect((host, port))
s.send("Hello server!".encode())

with open('received_file', 'wb') as f:
    print('receiving data...')
    while True:
        data = s.recv(1024)
        print('data=%s'%(data))
        if not data:
            break
        f.write(data)

print('Successfully received the file')
s.close()
print('connection closed')



MyFile.txt
The earth provides a boundless feast,Enough for every man and beast,Rich soil, fresh water, and the sun,To nourish lives for everyone.

Yet in the sorting of the spoil,Some reap the fruits of others' toil.While tables overflow with bread,A quiet street goes underfed.

The rivers flow, the rains descend,But pipelines twist and walls ascend.The drops of life are priced and sold,Measured out by lines of gold,Leaving the thirsty forced to plead,For what was meant to meet a need.

The tragedy is not the yield,But how we fence the harvest field.For hands are plenty, barns are deep,Yet justice is too dear to keep,Until the day the basics fallNot by the luck of birth, but all


received_file

The earth provides a boundless feast,Enough for every man and beast,Rich soil, fresh water, and the sun,To nourish lives for everyone.

Yet in the sorting of the spoil,Some reap the fruits of others' toil.While tables overflow with bread,A quiet street goes underfed.

The rivers flow, the rains descend,But pipelines twist and walls ascend.The drops of life are priced and sold,Measured out by lines of gold,Leaving the thirsty forced to plead,For what was meant to meet a need.

The tragedy is not the yield,But how we fence the harvest field.For hands are plenty, barns are deep,Yet justice is too dear to keep,Until the day the basics fallNot by the luck of birth, but allThank you for connecting









```
## OUPUT



<img width="1215" height="272" alt="image" src="https://github.com/user-attachments/assets/acee70dc-faa3-45f4-990e-00211118a7d5" />








<img width="1188" height="291" alt="image" src="https://github.com/user-attachments/assets/3ffef763-12d8-42d6-bc69-99a90ea4c337" />






## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
