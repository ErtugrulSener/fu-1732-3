## 6.2 Identification
### Identify what filesystem is being used
- Es gab in der MBR bei `0x01BE` bis `0x01EE` keine Partitionen
- Für Aufbau siehe hier: https://en.wikipedia.org/wiki/Master_boot_record
	- disk1.hdd öffnen
	- file -s sagt "FAT-16" obwohl in der MBR "FAT-32" steht

### How many partitions do you find?
- 1

### Which filesystems were used?
- FAT32
- Fragen an der Session

### Could you identify the OS with which the disk was formatted and written?
- BSD 4.4

### Are there any hints to this?
- You can find it at the position of the first partition inside of disk1 (offset 200)

### Is there any sign of tampering with filesystem data?
- Ja, weil wir bei der MBR FAT-32 und bei der Partition FAT-16 finden

## 6.3 Identify what has been purposefully hidden
### Which files were hidden?
- z.B: pdfs, direkt im disk1 Ordner die "XPOCOR~1.PDF"

### Which files were tampered with?
- file --extension *
- z.B: IMG1195.jpg wurde modifiziert (irgendwelche Kommentare drin)
- IMG1198 und IMG1205 wurden auch modifiziert, weil die Informationen nicht mehr im Header stehen

### Did you find the keywords I hid?
- Nope, aber der Betrunke Tobias hats gefunden!
- CAFFEEAFFE und sowas

### Would you be able to identify where I found the pictures I used?
- Steht nicht in den EXIF Informationen bzw. hab ichs nicht gefunden

### Why would you think I used them?

### 