
# Projektdokumentation – M158 LB2 WordPress-Migration


## Aufgabe 1 – Projektplan

Den Projektplan hab ich mit Tomsplanner gemacht. Das Tool ist ganz praktisch, weil man da alles easy per Drag & Drop verschieben kann und direkt sieht, was wann passieren soll. So hatte ich immer den Überblick, was als Nächstes ansteht.
<img width="1584" height="558" alt="image" src="https://github.com/user-attachments/assets/fe9c994b-8afa-4ea7-8b96-d6b0050f35cf" />
https://plan.tomsplanner.com/#doc=WBnUTMsSTcwgZFHvCGcm

## Aufgabe 3 – Umgebung aufbauen

Ich hab mich an die Anleitung vom Lehrer gehalten, aber ein paar Sachen angepasst. Ich hab zwei Server gemacht: Einen für die Webseite und einen für die Datenbank. Danach hab ich geschaut, ob die beiden sich auch wirklich erreichen können – hat geklappt.

## Aufgabe 4 – DNS

Für die Domain hab ich eine Subdomain von Samuele ausgelehnt. Bei Cloudflare hab ich einfach einen neuen Eintrag gemacht, damit meine Subdomain „rewan“ auf die IP vom Webserver zeigt. Damit konnte ich dann die Seite direkt über die richtige Adresse aufrufen.

## Aufgabe 5 – Webserver

Ich musste mich entscheiden: Apache oder NGINX? Ich hab Apache genommen, weil ich das schon kannte und die Einstellungen da für mich übersichtlicher sind.  
Ich hab zwei VirtualHosts gemacht:  
- Einer für HTTPS (Port 443), der die Domain prüft und ein selbstgemachtes Zertifikat nimmt.  
- Einer für HTTP (Port 80), der alles direkt auf HTTPS weiterleitet.

Die Standardseite von Apache hab ich gelöscht, damit man direkt auf meine Seite kommt. Außerdem hab ich noch eingestellt, dass Anfragen, die auf nicht vorhandene Dateien gehen, an die index.php weitergeleitet werden.

## Aufgabe 6 – PHP

Ich hab erstmal nachgeschaut, welche PHP-Version WordPress aktuell braucht und dann PHP 8.2 installiert (mit FPM). In der Config hab ich die empfohlenen Einstellungen für WordPress übernommen, z.B. mehr Speicher und längere Ausführungszeit. Danach hab ich getestet, ob alles läuft.

## Aufgabe 7 – MariaDB-Server

Ich hab mich für MariaDB entschieden, weil das schneller sein soll. Auf dem Datenbank-Server hab ich MariaDB installiert, so eingestellt, dass man auch von aussen darauf zugreifen kann, und dann einen eigenen User für WordPress angelegt. Das Root-Passwort hab ich natürlich auch geändert.

## Aufgabe 8 – PhpMyAdmin

PhpMyAdmin hab ich auf dem Webserver installiert. Bei der Installation hab ich die extra MySQL-Datenbank abgelehnt und danach in der Config eingestellt, dass PhpMyAdmin auf meinen Datenbank-Server zugreift. Damit ich es über die Subdomain aufrufen kann, hab ich noch ne Weiterleitung in Apache eingerichtet.

## Aufgabe 9 – FTP-Server

Für FTP hab ich vsftpd genommen. Ich hatte anfangs Probleme, die wir aber lösen konnten, da Samuele davor auch ähnliche Probleme hatte.

## Aufgabe 10 – WordPress-Migration

Die Daten hab ich per FTP vom Lehrer-Server runtergeladen. Die Datenbank hab ich auf dem Datenbank-Server importiert, die anderen Dateien auf den Webserver gepackt und in der wp-config.php alles angepasst. Erst hat die Seite noch auf die alte Domain weitergeleitet, aber nachdem ich die Werte in der Datenbank geändert hab, ging’s dann.

## Aufgabe 11 – Backup

Ich hab zwei Bash-Skripte geschrieben:  
- Eins für den Webserver, das ein Backup vom wp-content-Ordner macht und alte Backups löscht.  
- Eins für die Datenbank, das ein Backup der WordPress-DB macht und auch alte Backups löscht.

Beide Skripte schicken mir am Ende eine Mail, damit ich weiss, dass das Backup durchgelaufen ist. Die laufen automatisch jede Nacht mit Cron.

## Aufgabe 12 – Testing

Ich habe mir die Testfällen von Samuele ausgelehnt und habe sie mit meinem eigenen Projekt durchbearbeitet.

