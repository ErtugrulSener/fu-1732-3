## 7.1 - Assembler
### Was passiert, wenn man AL auf 255 + 1 setzt, ändert sich AH?
- Ja, in AL passen genau 255 rein. Bei 256 würde es sich verändern

## 7.1.4.2 - Add
### It will output two “U”s. Why? (Hint look for an ASCII table)
- value1 dd 1234h
- value2 dd 4321h
	- 0x1234 + 0x4321 = 0x5555 => UU

### Könntest du alles in EBX printen?
- ...

## 7.2.1.1 - Simple programme 1.c
### After a has been assigned a random number (is it really that random? Why not?)
Nein, es ist nicht random. Der Seed ist ja immer der Selbe. Siehe erste Ziele in der Main-Methode
```C
srand ( 127 );
```

## 7.3.1.1 Could you spot the bug?
- Off by one error beim Buffer *numbers*, der Index 5 ist die 6. Stelle und befindet sich außerhalb des Arrays
- *Out of bounds read*
- Beim Auslesen steht da ein zufälliger Wert im Speicher