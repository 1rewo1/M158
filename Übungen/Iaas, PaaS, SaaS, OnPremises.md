Welche Gemeinsamkeiten und Unterschiede lassen sich erkennen?
Welche unterschiedlichen Schwerpunkte setzen die Diagramme?
Wie lassen sich die Inhalte beider Grafiken sinnvoll miteinander in Verbindung bringen?

1. Gemeinsamkeiten und Unterschiede:
•	Beide zeigen das Prinzip von Shared Responsibility (wer verwaltet was?).
•	IaaS, PaaS und SaaS werden gestuft dargestellt – je weiter rechts, desto mehr übernimmt der Anbieter.
Unterschiede:
Das erste Diagramm zeigt technische Schichten (z. B. OS, Middleware) als Farbenblock für jede Rolle (du vs. Anbieter).
Das zweite Diagramm (SVG) zeigt das Gleiche, aber oft visuell aufgelockerter oder kontextbezogen mit Icons, z. B. mit Fokus auf Sicherheitsverantwortung.
2. Unterschiedliche Schwerpunkte:
Diagramm 1 (gestapelte Blöcke):
Fokus liegt auf technischer Kontrolle – was du verwaltest und was der Anbieter übernimmt.
Diagramm 2 (Shared Responsibility Model):
Häufiger Fokus auf Sicherheitsaspekte und Risikoverteilung, z. B. bei Cloud-Sicherheit (besonders bei AWS, Azure etc.).
 3. Sinnvolle Verbindung beider Inhalte:
Du kannst beide kombinieren, um ganzheitlich zu verstehen:
•	Diagramm 1 zeigt, welche Komponenten du verwaltest.
•	Diagramm 2 ergänzt, welche Sicherheits- und Betriebsverantwortungen du trägst, selbst wenn z. B. der Anbieter den Server bereitstellt.
➡️ Beispiel:
Bei SaaS musst du dich nicht um das OS kümmern (Diagramm 1), aber du bist trotzdem verantwortlich für Passwortsicherheit oder Zugriffsrechte (Diagramm 2).

# Verantwortungsmodell: On-Premises, IaaS, PaaS, SaaS

| Komponente               | On-Premises | IaaS        | PaaS        | SaaS        |
|--------------------------|-------------|-------------|-------------|-------------|
| Applications             | SV          | SV          | SV          | Anbieter    |
| Data                     | SV          | SV          | SV          | Anbieter    |
| Runtime                  | SV          | SV          | Anbieter    | Anbieter    |
| Middleware               | SV          | SV          | Anbieter    | Anbieter    |
| Operating System (O/S)   | SV          | SV          | Anbieter    | Anbieter    |
| Virtualization           | SV          | Anbieter    | Anbieter    | Anbieter    |
| Servers                  | SV          | Anbieter    | Anbieter    | Anbieter    |
| Storage                  | SV          | Anbieter    | Anbieter    | Anbieter    |
| Networking               | SV          | Anbieter    | Anbieter    | Anbieter    |

**Legende:**
- **SV** = Selbst verwaltet
- **Anbieter** = Wird vom Cloud-Anbieter gemanagt

