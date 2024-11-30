![[image-98.png]]
### Rámec
| Preambule | SOF    | MAC cíle | MAC zdroje | Typ/délka | Data a výplň  | CRC32   | Mezera mezi rámci |
| --------- | ------ | -------- | ---------- | --------- | ------------- | ------- | ----------------- |
| 8 bajtů   | 1 bajt | 6 bajtů  | 6 bajtů    | 2 bajty   | 46-1500 bajtů | 4 bajty | 12 bajtů          |
|           |        |          |            |           |               |         |                   |
#### Preambule
 - 64 alternujících jedniček a nul
 - Jejím účelem je synchronizovat frekvenci vysílače a přijímače
 
#### SOF - Začátek rámce
  - 7 alternujících jedniček a nul s jedničkou na konci

#### Adresy přijímače a vysílače
  - obě mají 6 bajtů
  - Zařízení zjišťuje jestli je přijímačem a proto je adresa přijímače první jestli ne tak rámec vypustí

#### Typ a délka

#### Data a výplň
 - 46 až 1500 bajtů (minimální velikost )
 - výplň se používá když zpráva je menší než 46 bajtů