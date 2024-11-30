![[image-98.png]]
### Rámec
|       | Preambule | SOF 802.3 | MAC cíle | MAC zdroje | Typ/Délka     | Data a výplň  | CRC32   | Mezera mezi rámci |
| ----- | --------- | --------- | -------- | ---------- | ------------- | ------------- | ------- | ----------------- |
| 802.3 | 7 bajtů   | 1 bajt    | 6 bajtů  | 6 bajtů    | 2 bajty délky | 46-1500 bajtů | 4 bajty | 12 bajtů          |
| II    | 8 bajtů   | Není      | stejná   | stejná     | 2 bajty typu  | stejné        | stejné  | stejné            |
#### Preambule
 - 64 alternujících jedniček a nul - v 802.3 poslední bajt je **SOF**
 - Jejím účelem je synchronizovat frekvenci vysílače a přijímače
 
#### SOF - Začátek rámce 802.3
  -  7 alternujících jedniček a nul s jedničkou na konci

#### Adresy přijímače a vysílače
  - obě mají 6 bajtů
  - Zařízení zjišťuje jestli je přijímačem a proto je adresa přijímače první jestli není tak rámec vypustí

#### MAC Adresa
  - V hexadecimální soutavě
  - skládá se z 3 bajtů ID výrobce a 3 bajtů ID karty

 - Unicast Multicast - Poslední bit v prvním bajtu určuje jestli je adresa unicast *(v případě že bit je 0)* nebo multicast *(v případě že je jedna)* 

	 - Když poslední bit je **0** znamenaje že adresa je unicast *(můžete poznat jestli první bit je sudý 0,...,8,A,C,E)* `06:b2:d9:a2:32:9e | 06 => 00000110`

	- Když poslední bit je **1** znamenaje že adresa je multicast *(můžete poznat jestli první bit je sudý 1,...,9,B,D,F)*   `11:c0:ff:ee:d8:ab | 11 => 00010001`
	
	- Broadcast adresa, kde všechny bity jsou zapnuté  `FF:FF:FF:FF:FF:FF`

-  Globální unikátnost - předposlední bit určuje jestli je adresa globálně jedinečná nebo lokálně spravovaná 

	 - Když předposlední bit je **0** znamenaje že adresa je *globálně jedinečná* *(můžete poznat jestli první bit je sudý 0,...,8,A,C,E)* `06:b2:d9:a2:32:9e | 06 => 00000110`

	- Když předposlední bit je **1** znamenaje že adresa je *lokálně spravovaná* (můžete poznat jestli první bit je sudý 1,...,9,B,D,F)*  `11:c0:ff:ee:d8:ab | 11 => 00010001`

#### Typ a délka
 - 802.3 zamění typové pole za délku dat 
	 - Používá začátek dat pro *802.2 LLC (Logical LInk Control) protocol* pro typovou informaci
- Ethernet **II** považuje pole za typ
	- zpráva *A* a *A0* je stejná
- Hodnota do 1500 je délka protokol *802.3*. Hodnota od 1536 je typ Ethernet **II**.

#### Data a výplň
 - 46 až 1500 bajtů (minimální velikost rámce 64 bajtů)
	 - původní důvod pro maximální velikost byla omezenost RAM té doby
 - výplň se používá když zpráva je menší než 46 bajtů

#### CRC32 - kontrolní součet
 - Kontroluje jestli je rámec správný
	 - V případě chyby je vyhozen
- Je prováděno na celém rámci včetně hlavy
- nezáleže na délce dat, má 4 bajty (32 bitů)

#### Mezera mezi rámci
 - má 12 bajtů a slouží k rozdělení jednotlivých rámců 