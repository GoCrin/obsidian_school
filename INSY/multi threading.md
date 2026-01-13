GIL
```
import os
import threading
import queue
from concurrent.futures import ThreadPoolExecutor
import tkinter as tk
from tkinter import ttk, messagebox

MAX_SECONDS_PER_PING = 2
MAX_THREADS = 50

# ------------------ IP UTILITIES ------------------

def getHelp(msg):
    raise ValueError(msg)

def ipArgToFirstAndLastIp(arg):
    ipAndSubnet = arg.split("/")

    if len(ipAndSubnet) != 2:
        getHelp("Invalid CIDR format")

    ip = list(map(int, ipAndSubnet[0].split(".")))
    if len(ip) != 4 or any(i < 0 or i > 255 for i in ip):
        getHelp("Invalid IP address")

    subnet = int(ipAndSubnet[1])
    if subnet < 0 or subnet > 32:
        getHelp("Invalid subnet mask")

    mask = [(0xff << (8 - max(0, subnet - i * 8))) & 0xff for i in range(4)]
    network = [ip[i] & mask[i] for i in range(4)]
    broadcast = [network[i] | (255 - mask[i]) for i in range(4)]

    return network, broadcast

def incrementIP(addr):
    addr = addr[:]
    for i in range(3, -1, -1):
        if addr[i] < 255:
            addr[i] += 1
            break
        addr[i] = 0
    return addr

def ipAreEqual(a, b):
    return a == b

def ipToString(ip):
    return ".".join(map(str, ip))

def generate_ips(start, end):
    current = incrementIP(start)
    while not ipAreEqual(current, end):
        yield ipToString(current)
        current = incrementIP(current)

# ------------------ PING WORKER ------------------

def ping_worker(ip, output_queue):
    response = os.system(
        f"ping -nqc 1 -W {MAX_SECONDS_PER_PING} {ip} > /dev/null"
    )
    if response == 0:
        output_queue.put(f"[Response] {ip}")
    else:
        output_queue.put(f"[Missed]   {ip}")

# ------------------ GUI ------------------

class NetworkScannerGUI:
    def __init__(self, root):
        self.root = root
        self.root.title("nfake – Network Scanner")

        self.queue = queue.Queue()

        ttk.Label(root, text="Destination Network (CIDR):").pack(pady=5)
        self.entry = ttk.Entry(root, width=30)
        self.entry.pack()

        self.start_btn = ttk.Button(root, text="Start Scan", command=self.start_scan)
        self.start_btn.pack(pady=10)

        self.output = tk.Text(root, height=20, width=60)
        self.output.pack(padx=10, pady=10)

        self.root.after(100, self.process_queue)

    def start_scan(self):
        cidr = self.entry.get().strip()
        if not cidr:
            messagebox.show_error("Error", "Please enter a network")
            return

        self.output.delete(1.0, tk.END)

        try:
            network, broadcast = ipArgToFirstAndLastIp(cidr)
        except ValueError as e:
            messagebox.showerror("Error", str(e))
            return

        self.start_btn.config(state=tk.DISABLED)

        threading.Thread(
            target=self.run_scan,
            args=(network, broadcast),
            daemon=True
        ).start()

    def run_scan(self, network, broadcast):
        ips = list(generate_ips(network, broadcast))

        with ThreadPoolExecutor(max_workers=MAX_THREADS) as executor:
            for ip in ips:
                executor.submit(ping_worker, ip, self.queue)

        self.queue.put("[Finished]")
        self.start_btn.config(state=tk.NORMAL)

    def process_queue(self):
        try:
            while True:
                msg = self.queue.get_nowait()
                self.output.insert(tk.END, msg + "\n")
                self.output.see(tk.END)
        except queue.Empty:
            pass
        self.root.after(100, self.process_queue)

# ------------------ MAIN ------------------

if __name__ == "__main__":
    root = tk.Tk()
    app = NetworkScannerGUI(root)
    root.mainloop()

```