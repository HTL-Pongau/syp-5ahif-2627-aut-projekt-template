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
  - ansible
  - raspberry-pi
---

# 📄 Projektauftrag — Raspberry Pi per Ansible deployen

> [!abstract] Merksatz
> Du bekommst einen **Raspberry Pi**, überlegst dir ein Projekt (Webserver, Werbeblocker, Dashboard, Backup …) und setzt es **vollständig per Ansible** auf — von der frischen SD-Karte bis zum laufenden Dienst. Abgabe: dieser git push + Doku + **Live-Demo mit Erklärung**. KI ist erlaubt, muss aber deklariert und erklärbar sein (Tracks, Abschnitt 5). **Sicherheit (SD)** ist Pflichtbestandteil des deployten Projekts (Abschnitt 3).

## 1. Idee & Proposal (Pflicht vor Start)

**1 Seite:** Idee, Zielzustand, Dienste, geplante Ansible-Features (Role, Vault, …), Risiken — inkl. kurzer Risiko-Einschätzung zu Sicherheit (was ist exponiert?). Ich genehmige — dann startest du.
Ideen: persönlicher Webserver (nginx) · Werbeblocker (Pi-hole) · Dashboard (Homer) · Backup-Ziel (rsync) · Mediabox (Kodi) · Pi-Monitoring — oder eigene Idee.

## 2. Setup

- **Managed Node:** dein Pi (Raspberry Pi OS Lite; Image von mir vorbereitet: SSH an, eigener User, kein Passwort-Login)
- **Control Node:** EDV-Raum-PC oder Laptop (wie im Docker-Lab, AUT#1)
- **Zugriff:** Ed25519-Key aus AUT#1 per `ssh-copy-id`, `~/.ssh/config`; **kein root-Login** — `become` (wie Ubuntu im Lab)

```ini
# inventory/hosts.ini
[pis]
pi-<name> ansible_host=192.168.x.x
[pis:vars]
ansible_user=pi
ansible_become=true

# ansible.cfg
[defaults]
inventory = inventory/hosts.ini
host_key_checking = False   # nur im Schulnetz!
```

## 3. Pflichten

> [!success] Checkliste
> - [ ] Ansible-Projekt in diesem Repo mit Zielstruktur (Baum unten)
> - [ ] `site.yml` deployt alles; **mindestens eine Role**
> - [ ] **Vault** für mind. ein Secret — im Repo nur verschlüsselt
> - [ ] Idempotenz-Nachweis: zweiter Lauf `changed=0`
> - [ ] **Sicherheit (SD)** umgesetzt und erklärbar (Kasten unten)
> - [ ] README (Struktur, Setup, Troubleshooting)
> - [ ] Track-Artefakt ausgefüllt: [[02_KI_Nutzungsprotokoll]]
> - [ ] Live-Demo 10 Min. + Erklärungsgespräch

```
mein-projekt/            # z. B. als Ordner ansible/ in diesem Repo
├── ansible.cfg
├── inventory/hosts.ini
├── group_vars/all.yml
├── secrets.yml              # nur verschlüsselt! (ansible-vault)
├── site.yml                 # deployt alles, bindet Role(s) ein
├── roles/<deine-role>/
│   ├── tasks/main.yml
│   ├── handlers/main.yml
│   ├── templates/  files/  defaults/
└── README.md
```

> [!info] Sicherheit (SD) — im deployten Projekt mitdenken
> - **SSH härten:** Key-only (`PasswordAuthentication no`, `PermitRootLogin no`), Rechte per `become` — nie root-Login
> - **Firewall (ufw):** nur die Ports, die dein Dienst wirklich braucht
> - **Secrets nur im Vault** — nie Klartext im Repo
> - **Least Privilege:** Dienst läuft unter eigenem User, keine `777`-Rechte
> - **Updates:** Sicherheits-Updates automatisiert (z. B. `unattended-upgrades`)

## 4. Erklären können (Demo-Gespräch)

| Feature | Konkret an deinem Projekt |
|---|---|
| **Role** | Aufbau `roles/`, Einbindung in `site.yml` |
| **Vault** | Verschlüsselung, `--ask-vault-pass`, warum kein Klartext im Repo |
| **+1 Wahl:** Handler/`notify` · Template (Jinja2) · `when`/Facts · `--tags` · Loops | eigenes Beispiel |
| **Sicherheit (SD)** | 1–2 Maßnahmen aus dem Kasten oben — warum genau diese? |

## 5. KI: zwei Tracks (wähle einen)

| | Track A — ohne KI | Track B — mit KI |
|---|---|---|
| Artefakt | Entscheidungs-/Troubleshooting-Log | KI-Protokoll (Prompts archiviert, Übernahme/Prüfung) — [[02_KI_Nutzungsprotokoll]] |

Kernanforderungen identisch. Regeln (immer): **keine Secrets, personenbezogenen Daten oder Schulzugänge in Prompts** (→ ITR: DSGVO/AI Act); KI-Code muss geprüft in **deinem** Setup laufen; alles muss im Gespräch erklärbar sein.

## 6. Meilensteine, Demo & Abgabe

| Wann (Vorschlag) | Meilenstein |
|---|---|
| KW49 Di 01.12. | M1 Proposal genehmigt |
| KW49 Do 03.12. | M2 Pi im Inventory, erster Playbook-Lauf grün |
| KW50 Di 08.12. | M3 Role + Vault + erste Sicherheitsmaßnahmen stehen, Playbook läuft durch |
| KW51 Di 15.12. | M4 fertig (Idempotenz-Nachweis, README, Artefakt); **Abgabe: letzter `git push`** auf dieses Repo bis 23:59 Uhr |
| KW51 Do 17.12. (+ KW52) | M5 **Live-Demo** 10 Min.: frischer Pi → `ansible-playbook site.yml --ask-vault-pass` → Dienst läuft → 2. Lauf `changed=0` → Fragen (Katalog: [[01_Beurteilungskriterien]]) |

Do-Blöcke sind Projektzeit — komm mit konkretem Stand, nicht mit „geht nicht".

## 🔗 Verweise

Vorwissen: AUT#1 (Arbeitsblatt *AB Ansible Module*) · Bewertung: [[01_Beurteilungskriterien]] · [docs.ansible.com](https://docs.ansible.com/)
