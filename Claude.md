# Claude.md — Projektanweisung

**Projekt:** US CLOUD Act & Deutsche Datensouveränität  
**Organisation:** 4K Analytics GmbH / HIGL – Health Innovators Group Leipzig  
**Autor:** Björn Degenkolbe, Geschäftsführer

---

## 1. Projektbeschreibung

Dieses Projekt pflegt ein umfassendes Analysedokument zur CLOUD-Act-Exposition des deutschen Gesundheitswesens. Das Dokument dient als Wissensgrundlage für GKV/KV/Klinik-IT-Beratung und interne Architekturentscheidungen. Es wird regelmäßig aktualisiert, validiert und als PDF/Word/Wiki exportiert.

**Aktueller Stand:** Version 22.0, April 2026, 214 Quellen, 19 Kapitel.

---

## 2. Dateien

| Datei | Zweck |
|---|---|
| `Wolkenfrei.md` | Hauptdokument (Single Source of Truth) |
| `Validierung.md` | Prüfprozess — regelt Ablauf, Prüfschritte und Versionierung |
| `Validierung-Ergebnisse.md` | Historisches Protokoll aller Validierungen |
| `Formatvorlage.md` | Gestaltungsrichtlinie für PDF- und Word-Export |
| `Claude.md` | Dieses Dokument — Projektanweisung für Claude |
| `validate.py` | Automatisierte Strukturprüfung (Gliederung, Nummerierung, Querverweise, Quellen, Formatierung, Version) |
| `red_thread.py` | Automatisierte Roter-Faden-Prüfung (Kapitelinhalt, Querverweisstruktur, Fazit-Abdeckung, Redundanz) |
| `build_pdf.py` | PDF-Export (reportlab) |
| `build_wiki.py` | Wiki-Export: splittet Wolkenfrei.md in MkDocs-Seiten unter `docs/` |
| `build_github_wiki.py` | GitHub-Wiki-Export: Seiten + Home.md + _Sidebar.md unter `wiki/` |
| `build_docx.js` | Word-Export-Skript (Legacy — aktuell wird pandoc verwendet) |
| `mkdocs.yml` | MkDocs-Konfiguration (Material-Theme, Navigation, Plugins) |
| `docs/` | MkDocs-Wiki-Seiten (generiert aus Wolkenfrei.md via `build_wiki.py`) |
| `docs/stylesheets/extra.css` | Custom CSS für MkDocs Material Theme |
| `Wolkenfrei.pdf` | PDF-Export (generiert via `build_pdf.py`) |
| `Wolkenfrei.docx` | Word-Export (generiert via `pandoc`) |

---

## 3. Dokumentstruktur (19 Kapitel)

| § | Kapitel | Kernthema |
|---|---|---|
| 1 | Das Kernproblem | Regelungslücke IT-Sicherheit vs. Jurisdiktion; 7 Realitätsgründe |
| 2 | Rechtliche Grundlagen | CLOUD Act im Wortlaut |
| 3 | US-Zugriffsebenen | CLOUD Act, FISA § 702, NSL, Sanktionen (OFAC) |
| 4 | EU-Behördenzugriff | e-Evidence-VO, Five Eyes, rechtsstaatlicher Vergleich |
| 5 | Anbieterbewertung | CLOUD-Act-Risikokategorien A–E; Anbieter-Tabelle |
| 6 | Operator-Modell | Delos Cloud, S3NS PREMI3NS |
| 7 | Hyperscaling-Problem | Service-Tiefe, KI-Anbieter, Integrationsplattformen, Vibecoding |
| 8 | EU-Plattformstack | Vollständiger Ersatz-Stack |
| 9 | EU-US-Abkommen | DPF, Schrems III, Executive Agreement |
| 10 | Lobbyarbeit | 151 Mio. EUR, 890 Lobbyisten, 7 Lobby-Narrative |
| 11 | Berater-Falle | McKinsey, Accenture, Deloitte als Cloud-Multiplikatoren |
| 12 | Marktbeispiele | KVNO, Kubus IT, CGM, Doctolib, Telematikinfrastruktur |
| 13 | Verschlüsselung | HYOK/BYOK/SSE; warum Verschlüsselung KI nicht schützt |
| 14 | Bewertungsschema | Länderranking nach Souveränitätskriterien |
| 15 | Globaler Vergleich | Wie andere Regionen dem CLOUD Act entkommen |
| **16** | **Aufsichts- und Regulierungslandschaft** | **14 Institutionen (BfDI, BAS, BMG, gematik, G-BA, BSI, KBV, DKG u.a.); DPA-Flickenteppich; DSK-Beschlüsse; Synthese "warum niemand das Problem besitzt"** |
| 17 | DSGVO-Handlungsempfehlungen | Sofortmaßnahmen, 4-Stufen-Modell, TIA, AVV, Exit-Strategie, Haftungskette |
| 18 | Regulatorischer Ausblick | TI 2.0, GeDIG, EHDS |
| 19 | Quellenverzeichnis | 214 Quellen |
| — | Fazit | 12 Kernaussagen (zwischen §18 und §19) |

---

## 4. Regeln

### 4.1 Stil und Tonalität

- Sachlich, faktenbasiert, nicht polemisch
- Neutral, aber mit Haltung — das Thema ist dem Autor wichtig
- Fließtext bevorzugt, keine unnötigen Aufzählungen
- Fachbegriffe beim ersten Auftreten erklären
- Abkürzungen beim ersten Auftreten ausschreiben
- Kein Marketing-Sprech
- Knapp formulieren — keine Redundanzen zu anderen Kapiteln aufbauen. Wenn ein Thema anderswo vertieft wird: ein Satz + Querverweis, nicht nochmal ausführen.

### 4.2 Rechtliche Sorgfalt

- Das Dokument stellt keine Rechtsberatung dar — dieser Hinweis steht im Dokument und muss erhalten bleiben
- Konjunktiv verwenden, wenn auf Gesetzentwürfe Bezug genommen wird, die noch nicht in Kraft sind
- § 393 SGB V und DSGVO Art. 48 ergänzen sich — sie widersprechen sich nicht. Niemals als "Normwiderspruch" formulieren
- Haftungswege (DSGVO-Bußgeld, Organhaftung, NIS2-Lieferkette) sauber trennen und nicht vermischen

### 4.3 Inhaltliche Regeln

- US-Hyperscaler gleichgewichtig behandeln — Azure nicht als Stellvertreter für alle verwenden, außer bei konkreten Einzelfällen
- Alle Fakten müssen belegbar sein — keine Behauptungen ohne Quelle
- Bei Personen: Nur behaupten, was dokumentiert ist (z.B. nicht annehmen, dass jemand GKV-versichert ist)
- Das Dokument wurde mit Claude (Anthropic) erstellt — dieser Hinweis muss im Dokument stehen
- **Keine Redundanzen:** Jeder Sachverhalt hat genau einen Ort im Dokument. Andere Stellen verweisen darauf per §-Querverweis. Ausnahme: bewusste Kurzfassungen mit explizitem Querverweis ("Ausführlich dokumentiert in §X").

### 4.4 Änderungen am Hauptdokument

- Jede Änderung löst eine Validierung gemäß `Validierung.md` aus
- Ergebnisse werden in `Validierung-Ergebnisse.md` protokolliert
- Nach jeder abgeschlossenen Validierung: PDF, Word und Wiki neu erstellen
- Versionsnummer wird hochgezählt
- Exports: `python3 build_wiki.py` → `python3 build_pdf.py` → `pandoc Wolkenfrei.md -o Wolkenfrei.docx --from markdown --to docx --toc --toc-depth=3`

### 4.5 Was nicht ohne Rückfrage geändert werden darf

- Kapitelstruktur (Reihenfolge, Anzahl, Nummerierung)
- Zentrale Argumentationslinien (Regelungslücke, Haftungskette, Souveränitätsstufen)
- Autorenname und Organisationszuordnung
- Quellenverzeichnis (keine Quellen löschen, nur ergänzen)

---

## 5. Build-Pipeline

```bash
# 1. Validierung
python3 validate.py          # Struktur: Gliederung, Nummerierung, Querverweise, Quellen, Formatierung, Version
python3 red_thread.py        # Roter Faden: Kapitelinhalt, Querverweisstruktur, Fazit, Redundanz

# 2. Wiki (MkDocs)
python3 build_wiki.py        # Splittet Wolkenfrei.md → docs/*.md, konvertiert §-Querverweise in Links

# 3. PDF
python3 build_pdf.py         # Erzeugt Wolkenfrei.pdf (reportlab, A4, Corporate Design)

# 4. Word
pandoc Wolkenfrei.md -o Wolkenfrei.docx --from markdown --to docx --toc --toc-depth=3 \
  --metadata title="US CLOUD Act & Deutsche Datensouveränität" \
  --metadata author="Björn Degenkolbe, 4K Analytics GmbH / HIGL"

# 5. GitHub Wiki (optional)
python3 build_github_wiki.py  # Erzeugt wiki/*.md + Home.md + _Sidebar.md
```

---

## 6. Typischer Arbeitsablauf

1. Autor bringt inhaltliche Änderung oder neue Information ein
2. Claude setzt die Änderung in `Wolkenfrei.md` um
3. Claude führt die Validierung gemäß `Validierung.md` durch (`validate.py` + `red_thread.py`)
4. Ergebnisse werden in `Validierung-Ergebnisse.md` protokolliert
5. Fehler werden behoben, Nachprüfung durchgeführt
6. Neue Version wird vergeben (Header + Footer + Validierung-Ergebnisse.md)
7. Exports: Wiki, PDF, Word neu erstellt
8. Commit und Push

---

## 7. Querverweiskonventionen

- `§X.Y` — Verweis auf Unterabschnitt (z.B. §16.4 = Aufsichtslandschaft, Das Gesamtbild)
- `Kapitel X` — Verweis auf ganzes Kapitel (z.B. Kapitel 7 = Hyperscaling-Problem)
- `→ §X.Y` oder `(→ §X.Y)` — Weiterleitungsverweis in Tabellen und Kurztexten
- `vgl. §X.Y` — Vergleichsverweis
- `Ausführlich dokumentiert in §X / Kapitel X` — Redundanzvermeidung

Bei Kapitelverschiebungen/-umnummerierungen: **alle** §-Querverweise im gesamten Dokument aktualisieren. `validate.py` prüft dies automatisch.
