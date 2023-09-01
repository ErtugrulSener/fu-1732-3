## 1. Describe how an HTML-attack could be abused to gain access to credentials. (25)  
- Phishing (Weiterleiten von Daten)
- Double Form Tags
- Browser Autofil
- Steal user session cookie

## 2. Explain how PHP-code-injections via include / require could be achieved - and prevented. (25)  
- include / require bindet andere Skripte in das aktuelle Skript ein
- Dynamisch Code einzubinden könnte gefährlich werden (User Input für require)
	- Local File Inclusion
	- Remote File Inclusion

*Wie verhindert man das?*
- Konstanten als Mapping
- Whitelist
- Remote File Includes ausschalten (allow_url_include=off + allow_url_fopen=off)
- Malicious Inputs verhindern + Firewall

## 3. Discuss how PRNGs could put session-management at risk. (25)  


## 4. How would secure programming create session IDs? (25)
