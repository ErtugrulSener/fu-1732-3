## 1. Please describe the differences between forensic investigation and incident response. (15) 
Beides sind ein wichtiger Teil der IT-Forensik.

Bei der incident response geht es darum die Ursache des Problems so schnell wie möglich zu finden und das System in einen stabilen und sicheren Zustand zu bringen. Selbst wenn hier ein Backup aufgespielt werden muss und dafür Beweise vernichtet werden.

Die forensic investigation dagegen bereitet Beweise für das Gericht auf, diese Analyse kann Wochen dauern. Das analysierte System darf nicht unternehmensentscheidend sein. Das Ziel ist es festzustellen was passiert ist, um solche Angriffe in Zukunft zu vermeiden.

## 2. Please identify how and where the forensic principles by BSI, Casedy and Freiling differ. (15)
Nope
    
## 3. For the following cases, argue why you prefer either a "clean" forensic process or incident response - and how you would mix and match to optimise your result:  
- Reacting to a ransomware attack
	- Beides, erst incident response um den Schaden schnell zu minimieren und dann eine länger dauernde forensische Analyse um den Schaden in Zukunft zu vermeiden, Ursachen zu finden, Daten für die Versicherung zu sammeln usw.
- suffering of a dDoS-attack 
	- Incident Response
- suffering of DoS due to a buffer overflow in a network daemon (20)
	- Forensic Investigation
        
## 4. Could you provide an automated script to identify files with a "tampered" extension - i.e. a .jpg hiding as .odt? (20)  
Prüfung auf: (file --extension -b "$file"

## 5. How would you suggest to delete a file in a forensically sound manner? (10)
a) Die Festplatte physisch zerstören
b) Auf der Festplatte überschreiben mit 0'en oder random Daten, die Gutmann Methode wäre eine mögliche
c) Backups, Systemwiderherstellungen usw. löschen
d) Festplatte vorher verschlüsseln
    
## 6. Looking at VeraCrypt's hidden volumes: Does a tool like tchunt actually find these? If not, what does it find - and if so, how? (20)
Nein
Es findet TrueCrypt Volumen indem es eine statistische Analyse macht nach bestimmten Parametern des Volumens.