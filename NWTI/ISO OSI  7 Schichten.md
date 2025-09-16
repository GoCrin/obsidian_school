
![[Pasted image 20250911115548.png]]

| Nummer | Name      |                                                                                                                  |
| ------ | --------- | ---------------------------------------------------------------------------------------------------------------- |
| 7      |           |                                                                                                                  |
| 6      |           |                                                                                                                  |
| 5      |           |                                                                                                                  |
| 4      | Transport | Addresierung von Diensten, Segmentierung von Daten                                                               |
| 3      | Network   |                                                                                                                  |
| 2      | Datalink  | Ethernet, arbeitet viel mit Broadcasts (Also muss größe begrenzt werden -> Layer 2 Segment muss begrenzt werden) |
| 1      | Physical  | Spannungen, Lichtimpulse, Elektromagnetische Wellen                                                              |

Layer 2 Segment / Broadcast Domaine -> Bereich in dem Rechner sich direkt erreichen können (Dürfen nicht zu Groß werden wegen Broadcasts)

Jede Layer muss auf das Protokoll im nächst höheren Layer hinweisen

| Name           | ka              |
| -------------- | --------------- |
| Network-Access |                 |
| Internet       | zwischen Netzen |
# ICMP
* Type
	* Echo Reply (0)
	* Echo Request (8)
* Code