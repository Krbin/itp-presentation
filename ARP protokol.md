 - překládá z třetí vrstvy na druhou
 - Zkusí najít IP v ARP cache/table mapuje IP na MAC. Pokud ho nenajde tak pošle ARP request s polem indikujícím že je to ARP protocol. Potom to přidá do tabulky a použije tento zápis

### Pole ARP request
 - Typ hardwaru - vždy na jedničce pro Ethernet
 - Typ protokolu - nastaveno na 0x0800
 - Velikost MAC adresy - 6 bajtů
 - Velikost IP adresy - 4 bajty
 - Opcode - na **1** pro ARP request
 - MAC adresa odesilatele
 - IP adresa odesilatele
 - MAC adresa příjemce - všechno na nule `00:00:00:00`
 - IP adresa příjemce - adresa toho koho hledá

 - #### Pole ARP odpovědi
	 - příjemce je nastaven na původního odesilatele
	 - MAC adresa je nastavena na tohoto příjemce
	 - nastaveno na ARP
	 - **Údaje prohozeny**