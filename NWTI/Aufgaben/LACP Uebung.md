# Aufgabenstellung
Aufzubauen ist wie in folgender Grafik sichtbar. Die bonding-ports sollen auf 100 Mbit/s gedrosselt werden.

![[Pasted image 20261007082429.png|580]]
# Konfiguration der Switches

Um die Bandbreite zwischen den Switches zu regulieren wird auf einem der beiden die `advertised speed` der `auto negotiation` auf 100 Mbit/s gesetzt

Switch 1?
```
/interface bridge
add name=br

/interface bonding
add mode=802.3ad name=mybond slaves=ether1,ether2,ether3 transmit-hash-policy=layer-2-and-3

/interface bridge port
add bridge=br interface=mybond
add bridge=br interface=ether4
add bridge=br interface=ether5

/ip address
add address=10.0.0.5/24 interface=br network=10.0.0.0
```

# Ergebnis Überprüfung

Die Verbindung und die Geschwindigkeit dieser Verbindung wird mit dem Programm "iperf3" getestet. Das Ergebnis ist unerwarteter weiße, dass die Bandbreite weit unter 100 Mbit/s ist.

```
❯ iperf3 -c 10.0.0.11  
Connecting to host 10.0.0.11, port 5201  
[  4] local 10.0.0.10 port 46494 connected to 10.0.0.11 port 5201  
[ ID] Interval           Transfer     Bitrate         Retr  Cwnd  
[  4]   0.00-1.00   sec   256 KBytes  2.09 Mbits/sec   61   1.41 KBytes   
[  4]   1.00-2.00   sec  1.38 MBytes  11.5 Mbits/sec   67   2.83 KBytes
[  4]   2.00-3.00   sec  3.00 MBytes  25.2 Mbits/sec   51   1.41 KBytes
[  4]   3.00-4.00   sec  2.75 MBytes  23.1 Mbits/sec   61   1.41 KBytes
[  4]   4.00-5.00   sec  2.62 MBytes  22.0 Mbits/sec   49   1.41 KBytes
[  4]   5.00-6.00   sec  3.00 MBytes  25.2 Mbits/sec   48   2.83 KBytes
[  4]   6.00-7.00   sec  2.50 MBytes  21.0 Mbits/sec   57   1.41 KBytes
[  4]   7.00-8.00   sec  2.62 MBytes  22.0 Mbits/sec   44   2.83 KBytes
[  4]   8.00-9.00   sec  3.12 MBytes  26.2 Mbits/sec   58   1.41 KBytes
[  4]   9.00-10.00  sec  2.75 MBytes  23.1 Mbits/sec   72   1.41 KBytes          
- - - - - - - - - - - - - - - - - - - - - - - - -  
[ ID] Interval           Transfer     Bitrate         Retr  
[  4]   0.00-10.00  sec  24.0 MBytes  20.1 Mbits/sec  568            sender  
[  4]   0.00-10.01  sec  23.9 MBytes  20.0 Mbits/sec                  receiver  
  
iperf Done.
```