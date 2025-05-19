# Vergleich und Verbindung der Diagramme: IaaS, PaaS, SaaS & Shared

## 1. Gemeinsamkeiten und Unterschiede

**Gemeinsamkeiten:**
- Beide Diagramme zeigen das Prinzip der **Shared Responsibility** – also die Aufteilung der Verantwortlichkeiten zwischen dir und dem Anbieter.
- Die Modelle **IaaS, PaaS und SaaS** werden **stufenweise** dargestellt: Je weiter rechts, desto **mehr übernimmt der Anbieter**.

**Unterschiede:**
- **Diagramm 1**: Fokus auf **technische Komponenten** wie Betriebssystem, Middleware, etc., dargestellt als farbige Blöcke (du vs. Anbieter).
- **Diagramm 2**: Gleiche Grundidee, aber visuell oft **detaillierter oder mit Icons** gestaltet – betont besonders die **Sicherheitsverantwortung** (z. B. bei AWS, Azure).

---

## 2. Unterschiedliche Schwerpunkte

| Diagramm             | Schwerpunkt |
|----------------------|-------------|
| **Diagramm 1**       | Technische Kontrolle – wer verwaltet welche Schicht? |
| **Diagramm 2**       | Sicherheit und Risiko – wer ist wofür verantwortlich bei z. B. Datenschutz, Zugriff, Verschlüsselung? |

---

## 3. Sinnvolle Verbindung beider Inhalte

Die beiden Diagramme lassen sich gut **kombinieren**, um ein **vollständiges Verständnis** zu schaffen:

- **Diagramm 1** zeigt:  
  → Welche **technischen Komponenten** du selbst betreibst (z. B. OS, Runtime, App).

- **Diagramm 2** zeigt:  
  → Welche **Sicherheits- und Betriebsverantwortungen** du **trotzdem behalten musst**, auch wenn die Technik vom Anbieter kommt.

➡️ **Beispiel zur Verknüpfung:**

> Bei **SaaS** musst du dich nicht um das Betriebssystem kümmern (Diagramm 1),  
> **aber** du bleibst verantwortlich für Dinge wie **Passwortsicherheit, Benutzerverwaltung oder Datenschutz** (Diagramm 2).

---

## Fazit

Die Kombination beider Modelle hilft dir, **technische und sicherheitsrelevante Verantwortlichkeiten** klar zu unterscheiden und besser zu planen – besonders in Cloud-Umgebungen.

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

- **SV** = Selbst verwaltet
- **Anbieter** = Wird vom Cloud-Anbieter gemanagt

