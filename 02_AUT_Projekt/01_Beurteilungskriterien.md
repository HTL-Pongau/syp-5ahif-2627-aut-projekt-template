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
> Bewertet wird, **ob du es erklären und begründen kannst** — plus Doku und Demo. KI ist erlaubt, muss aber deklariert (Track-Artefakt) und im Gespräch erklärbar sein.

| # | Kriterium | Gewicht | „Sehr gut" heißt |
|---|---|---|---|
| K1 | Idee & Proposal (Scope, Anforderungen, Risiken) | 10 % | präzise, realistisch |
| K2 | Struktur: Inventory, Playbook, Role(s) | 20 % | Zielstruktur, wiederverwendbare Role |
| K3 | Features erklärt: Vault, Role + 1 Wahl | 20 % | eigene Worte, Beispiele aus dem eigenen Projekt |
| K4 | Live-Demo: frischer Pi, fehlerfrei, 2. Lauf `changed=0` | 20 % | Dienst danach erreichbar |
| K5 | Track-Artefakt + Workflow erklärt | 15 % | Prompts/Entscheidungen archiviert, Prüfschritte genannt |
| K6 | README/Doku (Setup, Troubleshooting) | 15 % | Fremde Person deployt allein |

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

## Verweise

- [[00_Projektauftrag]] · [[02_KI_Nutzungsprotokoll]]
