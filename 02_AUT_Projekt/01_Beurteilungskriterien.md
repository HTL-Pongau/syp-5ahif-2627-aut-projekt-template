---
klasse: 5AHIF
fach: SYP
typ: handout
bereich: AUT
nr: AUT-Projekt
datum: 2026-11-24
tags:
  - handout
  - projekt
  - AUT
  - bewertung
---

# 📊 Beurteilungskriterien — AUT-Projekt

> [!abstract] Merksatz
> Bewertet wird, **ob du es erklären und begründen kannst** — plus Doku, Demo und Sicherheit (SD). KI ist erlaubt, muss aber deklariert (Track-Artefakt) und im Gespräch erklärbar sein.

| # | Kriterium | Gewicht | „Sehr gut“ heißt |
|---|---|---|---|
| K1 | Idee & Proposal (Scope, Anforderungen, Risiken) | 5 % | präzise, realistisch |
| K2 | Struktur: Inventory, Playbook, Role(s) | 15 % | Zielstruktur, wiederverwendbare Role |
| K3 | Features erklärt: Vault, Role + 1 Wahl | 20 % | eigene Worte, Beispiele aus dem eigenen Projekt |
| K4 | Live-Demo: frischer Pi, fehlerfrei, 2. Lauf `changed=0` | 20 % | Dienst danach erreichbar |
| K5 | Track-Artefakt + Workflow erklärt | 10 % | Prompts/Entscheidungen archiviert, Prüfschritte genannt |
| K6 | README/Doku (Setup, Troubleshooting) | 10 % | Fremde Person deployt allein |
| K7 | **Sicherheit (SD):** SSH key-only + kein root-Login, Firewall nur nötige Ports, Vault statt Klartext, least privilege | 20 % | Maßnahmen im Playbook sichtbar, im Gespräch begründet |

**Skala je Kriterium:** 4 sehr gut · 3 gut · 2 befriedigend · 1 genügend · 0 nicht gezeigt. Note = gewichtetes Mittel.

> [!warning] KI-Hinweis
> Deklarierte KI-Nutzung mit sauberem Protokoll ist ausdrücklich erwünscht — nicht erklärbarer Code zählt nicht als eigene Leistung.

## Fragen fürs Demo-Gespräch (Auszug)

- Warum steht das Passwort im Vault und nicht in `group_vars`?
- Was passiert beim 2. Lauf — woran erkennst du es?
- Was leistet die Role — warum nicht alles in `site.yml`?
- Wo entscheidet das Playbook, welcher Task wo läuft (`when`/Facts)?
- Was macht der Handler — wann läuft er?
- Wie kommt das Vault-Passwort zum Playbook?
- Welche Ports lässt deine Firewall zu — und warum nur diese?
- Warum kein root-Login per SSH — was ist der Unterschied zu `become`?

## Verweise

- [[00_Projektauftrag]] · [[02_KI_Nutzungsprotokoll]]
