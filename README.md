# Echoserver...

Echo server and client using python socket.

# AIM:

To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:

### STEP 1:

Design of echo server and client using python socket.

### STEP 2:

Implementation using Python code.

### STEP 3:

Testing the server and client.

### STEP 4:

Run the server side which is listening (or) waiting for the connection with the client side.

### STEP 5:

After that run the client side.

### STEP 6:

Finally, the desired output is received as "HELLO! WORLD" .

## PROGRAM:

#### CLIENT SIDE SOCKET CODE:

```python

import socket
HOST = "127.0.0.1"  # The server's hostname or IP address
PORT = 65432  # The port used by the server
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    s.sendall(b"Hello, world")
    data = s.recv(1024)
print(f"Received {data!r}")

```

#### SERVER SIDE SOCKET CODE:

```python

import socket
HOST = "127.0.0.1"  # Standard loopback interface address (localhost)
PORT = 65432  # Port to listen on (non-privileged ports are > 1023)
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    try:
        s.bind((HOST, PORT))
    except Exception as e:
        print(f"Error binding to {HOST}:{PORT}: {e}")
        exit()
    s.listen()
    print(f"Listening on {HOST}:{PORT}...")
    try:
        conn, addr = s.accept()
    except Exception as e:
        print(f"Error accepting connection: {e}")
        exit()
    with conn:
        print(f"Connected by {addr}")
        while True:
            try:
                data = conn.recv(1024)
                if not data:
                    break
                conn.sendall(data)
            except Exception as e:
                print(f"Error receiving/sending data: {e}")
                exit()

```

## OUTPUT:

#### CLIENT SIDE SOCKET CODE OUTPUT:

![ep1](https://github.com/anto-richard/Echoserver/assets/93427534/250afe9e-53d2-4fd6-a416-4b6cfbbcb7c6)

#### SERVER SIDE SOCKET CODE OUTPUT:

![ep2](https://github.com/anto-richard/Echoserver/assets/93427534/c89aa01d-1d95-4100-9586-31e2be379ee4)

## RESULT:

Thus, the socket programs to execute the echo server with the client and server sides using python is executed successfully.
