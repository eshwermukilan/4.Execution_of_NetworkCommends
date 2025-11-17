# 4.Execution_of_NetworkCommands
# NAME: ESHWER M
# REG.NO: 212224040086
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>

## Program

server.py
```
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))  # Fix: comma was missing
s.listen(5)
print("Server listening on port 8000...")

c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    hostname = c.recv(1024).decode()
    if not hostname: 
        break
    try:
        response = ping(hostname, verbose=False)
        c.send(str(response).encode())
    except Exception as e:  
        c.send(f"Error: {e}".encode())
```
client.py

```
import socket

s = socket.socket()
s.connect(('localhost', 8000))
print("Connected to server on port 8000.")

try:
    while True:
        ip = input("Enter the website you want to ping (or 'exit' to quit): ")
        if ip.lower() == 'exit':
            break
        s.send(ip.encode())
        response = s.recv(1024).decode()
        print(f"Server response:\n{response}")
finally:
    s.close()
    print("Connection closed.")

```
trace.py

```
import subprocess

def traceroute(host):
    print(f"Traceroute to {host}:\n")
    try:
        output = subprocess.check_output(["tracert", "-d", host], stderr=subprocess.STDOUT, text=True)
        print(output)
    except subprocess.CalledProcessError as e:
        print("Error executing traceroute:")
        print(e.output)

if __name__ == "__main__":
    target = input("Enter the website or IP to traceroute: ")
    traceroute(target)

```

## Output

<img width="1554" height="927" alt="Screenshot 2025-10-16 112209" src="https://github.com/user-attachments/assets/18c6d817-32fa-4154-9798-7058575203f2" />


<img width="1552" height="931" alt="Screenshot 2025-10-16 112228" src="https://github.com/user-attachments/assets/68f9e28b-fa9e-42e2-908f-15b4c23324d7" />


## Result
Thus Execution of Network commands Performed 
