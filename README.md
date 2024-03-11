# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.
## PROGRAM
```
import socket
import threading

def receive_messages(client_socket):
    while True:
        try:
            message = client_socket.recv(1024).decode('utf-8')
            print("Received:", message)
        except Exception as e:
            print("Error receiving message:", e)
            break

def send_messages(client_socket):
    while True:
        try:
            message = input("Enter message: ")
            client_socket.send(message.encode('utf-8'))
        except Exception as e:
            print("Error sending message:", e)
            break

def main():
    host = '127.0.0.1'
    port = 12345

    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

    server_socket.bind((host, port))

    server_socket.listen(5)
    print("Server listening on {}:{}".format(host, port))

    while True:
        client_socket, client_address = server_socket.accept()
        print("Connected to", client_address)

        receive_thread = threading.Thread(target=receive_messages, args=(client_socket,))
        send_thread = threading.Thread(target=send_messages, args=(client_socket,))

        receive_thread.start()
        send_thread.start()

if __name__ == "__main__":
    main()
```
## OUPUT
![Screenshot (142)](https://github.com/RahulvVenugopal/3b_CHAT_USING_TCP_SOCKETS/assets/144132514/3e3a0986-6b05-4773-a524-86cd84631b95)

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
