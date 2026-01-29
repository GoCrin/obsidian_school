Ein Laptop will mit einen anderen kommunizieren (Ein einziges Packet)

Packet schaut so aus
1. Ethernet header
	1. Dst Mac (als 1. damit man schneller überprüfen kann obs dem Empfänger gehört), 6 Byte
	2. Src Mac: 6 Byte
2. IP header
	1. Src IP
	2. Dst IP
3. tcp header (oder udp)
	1. Src Port
	2. Dst Port
4. Payload (e.g. http request)

## 1. Schritt


| Key      | Value                         |
| -------- | ----------------------------- |
| dst-mac  | mac1                          |
| src-mac  | mac0                          |
| src-ip   | ip0                           |
| dst-ip   | ip1                           |
| src-port | dynamic port (meist > 32.000) |
| dst-port | 22                            |
## 2. Schritt


| Key      | Value |
| -------- | ----- |
| dst-mac  | mac3  |
| src-mac  | mac2  |
| src-ip   | same  |
| dst-ip   | same  |
| src-port | same  |
| dst-port | 22    |

## Letzter Schritt


| Key      | Value                         |
| -------- | ----------------------------- |
| dst-mac  | mac11                         |
| src-mac  | mac10                         |
| src-ip   | ip0                           |
| dst-ip   | ip1                           |
| src-port | dynamic port (meist > 32.000) |
| dst-port | 22                            |

