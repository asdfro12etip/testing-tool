import socket
import requests
import threading
from queue import Queue

def scan_port(target_host, port):
    try:
        s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        s.settimeout(1.0)
        result = s.connect_ex((target_host, port))
        if result == 0:
            print(f"[+] Port {port} is OPEN!")
        s.close()
    except:
        pass

def start_port_scan(target_host, start_port, end_port):
    print(f"[*] Scanning {target_host} from port {start_port} to {end_port}...")
    for port in range(start_port, end_port + 1):
        scan_port(target_host, port)
    print("[+] Scan complete.")

if __name__ == "__main__":
    target = input("Enter Target IP: ")
    start_port_scan(target, 1, 1024)
