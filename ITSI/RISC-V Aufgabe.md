Debian VM erstellen und starten
[setup instructions](https://pdos.csail.mit.edu/6.1810/2025/tools.html)
Auf Debian Maschine
```
sudo apt install build-essential gdb-multiarch qemu-system-misc gcc-riscv64-linux-gnu
```
oder auf Arch
```
sudo pacman -S riscv64-linux-gnu-binutils riscv64-linux-gnu-gcc riscv64-linux-gnu-gdb qemu-emulators-full bc git base-devel
```


```
git clone git://g.csail.mit.edu/xv6-labs-2025  
cd xv6-labs-2025  
git checkout net
make qemu
```

Jetzt ist man im XV6 Betriebssystem.

https://pdos.csail.mit.edu/6.1810/2025/labs/net.html

QEMU simuliert eine intel e1000 Netzwerkkarte mit IP `10.0.2.15` auf der Guest (VM) Seite und IP `10.0.2.2` auf Host Seite.

QEMU beendet man mit `CTRL + a` dann `x`.

In Host in `kernel/e1000.c` in der Funktion, ein beliebiges print-statement einfügen.
```c
int  
e1000_transmit(char *buf, int len)  
{
 printf("C war zuerst da.\n");    
 return 0;  
}
```

Kernel neu kompelieren und starten.
```
make -s qemu
```

Die Änderungen sollten bei diesem Befehl sichtbar sein.
```
nettest txone
```

Es werden jetzt die Tipps abgearbeitet bis die Funktion so aus sieht. (Die Funktion hat einen Memory-Leak)
```c
int e1000_transmit(char *buf, int len)  
{
 printf("C war zuerst da.\n");  
 uint32 tail = regs[E1000_TDT];  
 printf("Tail found at: %d\n", tail);  
 if(tx_ring[tail].status != E1000_TXD_STAT_DD) {  
   return -1;  
 }  
  
 //kfree(); 
  
 tx_ring[tail].addr = (uint64)buf;  
 tx_ring[tail].length = len;  
 tx_ring[tail].cmd = E1000_TXD_CMD_EOP;  
  
 regs[E1000_TDT] = (tail + 1) % TX_RING_SIZE;  
  
 return 0;  
}
```

Jetzt wird die Funktion noch mal ausgeführt
```
nettest txone
```

Qemu wird gestoppt und dieser Befehl wird benutzt um das Frame zu sehen.
```
tcpdump -XXnr packets.pcap
```

Der Output zeigt zuerst das gesuchte Packet.
```
 reading from file packets.pcap, link-type EN10MB (Ethernet), snapshot length 65536  
11:47:41.809677 IP 10.0.2.15.2003 > 10.0.2.2.26099: UDP, length 5  
       0x0000:  5255 0a00 0202 5254 0012 3456 0800 4500  RU....RT..4V..E.  
       0x0010:  0021 0000 0000 6411 3ebc 0a00 020f 0a00  .!....d.>.......  
       0x0020:  0202 07d3 65f3 000d 0000 7478 6f6e 65    ....e.....txone  
11:47:41.892254 ARP, Request who-has 10.0.2.15 tell 10.0.2.2, length 46  
       0x0000:  ffff ffff ffff 5255 0a00 0202 0806 0001  ......RU........  
       0x0010:  0800 0604 0001 5255 0a00 0202 0a00 0202  ......RU........  
       0x0020:  0000 0000 0000 0a00 020f 0000 0000 0000  ................  
       0x0030:  0000 0000 0000 0000 0000 0000            ............
```