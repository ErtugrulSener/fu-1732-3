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

## 7.3.1.2
### What was I after when I tried to print the 16 Bytes following at EBP?
- Die Return-Addresse

### Side note: The programme would end in an endless loop, if I moved “i” from the heap to the stack. Why? Why would 2a.c und 2b.c both go into an endless loop? Verify your hypothesis using gdb!
- Weil dann die Variable im Stack wäre, immer wieder zurück auf 0 geschrieben wird -> Rekursion

## 7.3.2.1 - Analyse the code
### It would actually accept 23 bytes of input without crashing.
- Das Programm stürzt erst ab, wenn man die Returnadresse überschreibt
- Nach den lokalen Variablen kommen aber erst 4 Bytes EBP
- Warum es nicht schlimm ist, dass man den EBP überschreibt, weiß ich nicht

### Where do these 8 bytes come from? (Hint: What else is on the stack?)


## 7.3.2.2 - Looping
### If you compare this to the addresses in the disassembled main() function above, do you find the return address? Hint: It points to the address at “main+8”.
What do you notice? Why? (Hint: Remember Endianess)
- Die Adresse finde ich von rechts nach links geschrieben im Speicher

## 7.5.1.1
### Try also to identify, what you've read. (gdb might be useful)
- Mit Glück liest man nun EBP und die Return Adresse aus

```shell
(gdb) print $ebp
$1 = (void *) 0xbfffea98
```

### Could you imagine how this could actually be used to exploit a programme and inject shell code?
`./2 10 1 2 3 4 5 6 7 8 9 "\x13\x12\x22\xAA\x44\xbb\xef\xff"`

### 7.5.1.2
```C
data[i]=strtoull(argv[i + 1]);
```

## 7.5.12.1 - Strings
- In ~/boundary/1.c you'll be able to read the secret password provided – how and why?
```shell
[sose@localhost boundary]$ ./1 AAAAAAAAAA
AAAAAAAAAAtop secret!
[sose@localhost boundary]$ ./1 abc
abc
```