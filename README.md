
# Projektdokumentation – M158 LB2 WordPress-Migration


## Aufgabe 1 – Projektplan

Den Projektplan hab ich mit Tomsplanner gemacht. Das Tool ist ganz praktisch, weil man da alles easy per Drag & Drop verschieben kann und direkt sieht, was wann passieren soll. So hatte ich immer den Überblick, was als Nächstes ansteht.
<img width="1584" height="558" alt="image" src="https://github.com/user-attachments/assets/fe9c994b-8afa-4ea7-8b96-d6b0050f35cf" />
https://plan.tomsplanner.com/#doc=WBnUTMsSTcwgZFHvCGcm

## Aufgabe 3 – Umgebung aufbauen

Ich hab mich an die Anleitung vom Lehrer gehalten, aber ein paar Sachen angepasst. Ich hab zwei Server gemacht: Einen für die Webseite und einen für die Datenbank. Danach hab ich geschaut, ob die beiden sich auch wirklich erreichen können dafür musst ich den net-tools instalieren mit dem Befehl sudo apt install net-tools damit ich zuerst die Netzwerckumgebung teste und dann beie gepingt.

<img width="340" height="178" alt="image" src="https://github.com/user-attachments/assets/ab01e4be-5a41-484c-b9d3-e5a3f10e53e1" />
<img width="328" height="174" alt="image" src="https://github.com/user-attachments/assets/22ae71d7-e8d1-492d-bd75-372e392ea7b3" />
<img width="305" height="119" alt="image" src="https://github.com/user-attachments/assets/918eeb12-fcac-4fc7-ab32-9b7947d2711e" />
<img width="298" height="117" alt="image" src="https://github.com/user-attachments/assets/27c9e63c-f2ce-4c47-91c6-8cfbe017d738" />


## Aufgabe 4 – DNS

Für die Domain hab ich eine Subdomain von Samuele ausgelehnt. Bei Cloudflare hab ich einfach einen neuen Eintrag gemacht, damit meine Subdomain „rewan“ auf die IP vom Webserver zeigt. Damit konnte ich dann die Seite direkt über die richtige Adresse aufrufen. https://rewan.cistri.org/

## Aufgabe 5 – Webserver

Ich musste mich entscheiden: Apache oder NGINX? Ich hab Apache genommen, weil ich das schon kannte und die Einstellungen da für mich übersichtlicher sind.  
Ich hab zwei VirtualHosts gemacht:  
- Einer für HTTPS (Port 443), der die Domain prüft und ein selbstgemachtes Zertifikat nimmt.  
- Einer für HTTP (Port 80), der alles direkt auf HTTPS weiterleitet.

<img width="369" height="160" alt="image" src="https://github.com/user-attachments/assets/2eba7ffc-a3cb-4d10-bdab-f111f78060c2" />

<img width="270" height="67" alt="image" src="https://github.com/user-attachments/assets/7fcc6afa-5194-48c3-b82b-effaa679de4e" />


Die Standardseite von Apache hab ich gelöscht, damit man direkt auf meine Seite kommt. Außerdem hab ich noch eingestellt, dass Anfragen, die auf nicht vorhandene Dateien gehen, an die index.php weitergeleitet werden.

## Aufgabe 6 – PHP

Ich hab erstmal nachgeschaut, welche PHP-Version WordPress aktuell braucht und dann PHP 8.2 installiert (mit FPM). In der Config hab ich die empfohlenen Einstellungen für WordPress übernommen, z.B. mehr Speicher und längere Ausführungszeit. Danach hab ich getestet, ob alles läuft.

```
memory_limit = 256M
upload_max_filesize = 64M
post_max_size = 64M
max_execution_time = 120
display_errors = Off
```
Dann habe ich getestet

<img width="796" height="536" alt="image" src="https://github.com/user-attachments/assets/1ab05d1d-4010-4783-b438-f20326680760" />


## Aufgabe 7 – MariaDB-Server

Ich hab mich für MariaDB entschieden, weil das schneller sein soll. Auf dem Datenbank-Server hab ich MariaDB installiert, so eingestellt, dass man auch von aussen darauf zugreifen kann, und dann einen eigenen User für WordPress angelegt. Das Root-Passwort hab ich natürlich auch geändert.

<img width="558" height="188" alt="image" src="https://github.com/user-attachments/assets/ca44264b-87b7-4263-907f-f245a00886f5" />

## Aufgabe 8 – PhpMyAdmin

PhpMyAdmin hab ich auf dem Webserver installiert. Bei der Installation hab ich die extra MySQL-Datenbank abgelehnt und danach in der Config eingestellt, dass PhpMyAdmin auf meinen Datenbank-Server zugreift. Damit ich es über die Subdomain aufrufen kann, hab ich noch ne Weiterleitung in Apache eingerichtet.

<img width="838" height="413" alt="image" src="https://github.com/user-attachments/assets/5c6f1a1d-20d2-459d-b0ae-d66fa981651c" />


## Aufgabe 9 – FTP-Server

Für FTP hab ich vsftpd genommen. Ich hatte anfangs Probleme, die ich lösen konnten, da Samuele davor auch ähnliche Probleme hatte.

<img width="929" height="119" alt="image" src="https://github.com/user-attachments/assets/f39631ac-5d54-4055-aac2-73c86edbcafd" />


## Aufgabe 10 – WordPress-Migration

Die Daten hab ich per FTP vom Lehrer-Server runtergeladen. Die Datenbank hab ich auf dem Datenbank-Server importiert, die anderen Dateien auf den Webserver gepackt und in der wp-config.php alles angepasst. Erst hat die Seite noch auf die alte Domain weitergeleitet, aber nachdem ich die Werte in der Datenbank geändert hab, ging’s dann.

<img width="1143" height="395" alt="image" src="https://github.com/user-attachments/assets/480a536f-cc5f-4633-af6b-d89a0f219f6a" />


## Aufgabe 11 – Backup

Ich hab zwei Bash-Skripte geschrieben:  
- Eins für den Webserver, das ein Backup vom wp-content-Ordner macht und alte Backups löscht.  
- Eins für die Datenbank, das ein Backup der WordPress-DB macht und auch alte Backups löscht.

<img width="482" height="143" alt="image" src="https://github.com/user-attachments/assets/b11ae1c2-7950-46cf-8c91-f81d88a8c05f" />

<img width="443" height="209" alt="image" src="https://github.com/user-attachments/assets/b5ef784b-ce0b-4bd3-95f4-a3df50394dc1" />

<img width="337" height="224" alt="image" src="https://github.com/user-attachments/assets/d155516c-b1f1-427f-a36e-5f556958d1f4" />

<img width="323" height="219" alt="image" src="https://github.com/user-attachments/assets/724c8e66-e72c-4d8d-a3e7-76530c864d61" />

Beide Skripte schicken mir am Ende eine Mail, damit ich weiss, dass das Backup durchgelaufen ist. Die laufen automatisch jede Nacht mit Cron. Natürlich auch getestet

<img width="589" height="180" alt="image" src="https://github.com/user-attachments/assets/d0768c21-f92b-45c3-9921-643309681d5c" />

<img width="611" height="178" alt="image" src="https://github.com/user-attachments/assets/326e9982-84cd-4353-b80a-0cdc1a0999d7" />

## 12 - Testing

Ich habe mir die Testfällen von Samuele ausgelehnt und habe sie mit meinem eigenen Projekt durchbearbeitet und geschaut ob alles Funktioniert

<img width="703" height="367" alt="image" src="https://github.com/user-attachments/assets/d663f82a-7c27-4ca2-864f-727e889137ae" />

<img width="587" height="444" alt="image" src="https://github.com/user-attachments/assets/c02cbe47-afc5-4500-9919-7f18c31e6091" />

<img width="949" height="312" alt="image" src="https://github.com/user-attachments/assets/bba3d2b9-6d7c-4d3b-af56-c18b1a6e91b2" />

## Reflexion

Ich fand das Projekt super, auch wenn es mich anfangs überfordert hat. Es ist schade, dass wir in der Schule wegen der Ausfälle zu wenig Zeit dafür hatten. Trotzdem konnte ich am Schluss mit Hilfe von Samuele – zuhause nochmals von null anfangen und alles fertig machen. Jetzt kann ich mir gut vorstellen, so etwas auch privat und im Geschäft zu nutzen.
