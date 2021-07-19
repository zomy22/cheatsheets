### General Enumeration tips and reminders

- Reset the Machine before you start. 

- Exploits can render systems unexploitable, revert them again!

- Scan all ports TCP and UDP, Review every scan report

- Getting errors? Google every bit ! Cause an error on purpose

- Google banners, responses, comments on source code 

- Make sure to get all versions of all running services ( Use Wireshark and try to connect to it)

- Remember a little difference in versions may not matter, research a bit more and try the exploit if it's a close match

- Try to find the version of the service, use multiple tools(eg samba version may not show up, try with. Several tools). Run Wireshark and try to connect to the service

- That high port appears to be HTTP (eg port 8000), have to also checked if it's running on HTTPS. ?

- Is the web page a custom one or some type. Of CMS?

- Try defaults on all services

- Try the most stupid things, even the username as password, productname:productname servicename:servicename

- Password Brute forcing ? Start with a custom wordlist if possible (cewl -m 4 http://127.0.0.1/somepage.php)

- The vulnerability exists, you just have to find it. The strategy has for sure been listed in exploit db, there's nothing new here.

- Got directory traversal ? Try LFI and RFI

- Found code? hint ? or any important thing? Read it from top to bottom several times. READ THE DAMN CODE!

- You can read the exploit in Metasploit, you don't have to run it!

- If exploiting something that should work does not, consider going back and performing proper enumeration, maybe you need to unlock something or run as a different user context.

- Have problems with the code execution? -- Url encode properly, check backslashes in windows and also try double back slashes and forward slashes, other types of encoding/bypassing filters or whitelists etc

Full SQL injection cheat sheet:

- MYSQL: https://www.exploit-db.com/papers/13045

- MSSQL: https://www.exploit-db.com/papers/12975

Automeated enumeration with Autorecon: https://github.com/Tib3rius/AutoRecon


- Privilege Escalation:

- Always check for other sources and versions of your exploit on the web (eg, pre-compiled kernel exploit may already exist, search with cve like cve-2009-2698 exploit github)

-  Pay very close attention to which CVE's I'm looking, sometime the numbers are very similar and tired eyes don't help

- Exploit suggester (WES-NG etc) does not always show you all the available exploits, sometimes you need to google the OS and version for priv esc, eg "windows xp servcice pack 1 privilege escalation", "windows server 2008 SP1 privilege escalation" etc
