# Bischoff Holzurnen – Projektstatus & Dokumentation

## 🎯 Projektübersicht
**Produkt:** Handgefertigte Holz-Tierurnen mit individueller Lasergravur  
**Zielmarkt:** Europa (primär DE/AT/CH)  
**Aktuelle Phase:** Landing Page ✓ | Nächste Phase: Etsy-Integration  
**Team:** Harald & Leon Bischoff (Handwerk) + Digitale Unterstützung

---

## 📊 Aktueller Status

### ✅ Abgeschlossen (Landing Page)
- **Datei:** `index.html` (Single-Page, vollständig self-contained)
- **Struktur:** Header + Hero + Pakete (3 Tier) + About + Details + Prozess + FAQ + Kontaktformular + Partner-Section + Footer
- **Mobile:** Responsive (375px–1280px+), Header neu gebaut, Formularfelder optimiert
- **Formular:** Echtversand über FormSubmit.co → trixer220@gmail.com
- **Deployment:** Lokal lauffähig, ReadyToHostAnywhereHTML

### 🔄 In Arbeit / Feedback
- Viewport-Meta-Tag ggf. noch anpassen (Pinch-Zoom deaktivieren, wenn gewünscht)
- Impressum-Platzhalter noch ausfüllen: `[Straße Nr.]`, `[PLZ]`, Etsy-Shop-Link

### ⏭️ Nächste Phase: Etsy-Integration
Siehe Roadmap unten.

---

## 🛠️ Technologie-Stack

| Layer | Tech | Notes |
|-------|------|-------|
| **Frontend** | HTML5 + inline CSS + Vanilla JS | Single file, no build step |
| **Formular-Backend** | FormSubmit.co (Free) | E-Mail-Relay, kein eigener Server nötig |
| **Bilder** | `/images/` (PNG/JPG) | Logo, Produktfotos |
| **Versionierung** | Git + GitHub | Commit-Message: Co-Authored-By |

---

## 📋 Kontakte & Ressourcen

| Was | Wer/Was | Status |
|-----|---------|--------|
| **E-Mail** | trixer220@gmail.com | ✓ Formulare gehen hier hin |
| **Etsy-Shop** | [Link in Footer] | ⏳ noch nicht erstellt |
| **GitHub** | github.com/trixer220/Tier-Holzurnen | ✓ Aktiv |
| **Fotos/Assets** | `/images/` im Repo | ✓ Logo, Produktfoto vorhanden |

---

## 🗺️ Roadmap: Etsy-Integration

### Phase 1: Etsy-Account & Shop-Setup (1–2 Tage)
- [ ] Etsy-Shop erstellen (falls noch nicht geschehen)
- [ ] Bischoff Holzurnen als Shop-Name
- [ ] Shoprichtlinien, Versandkosten EU-weit konfigurieren
- [ ] 3 Pakete als separate Listings anlegen
- [ ] Produktfotos hochladen (die bestehenden aus `/images/`)

**Deliverables:**
- Etsy-Shop-Link (für Impressum + Footer)
- Produktlisting-URLs

### Phase 2: Bestellmanagementen-Struktur (2–3 Tage)
**Ziel:** Bestellungen von Etsy + direkter Website erfassen, ohne Doppelarbeit

**Option A (Simpel):** 
- Etsy-Bestellungen manuell checken
- Konfirmations-Email an Kunde
- Auftrag ins Handwerk übergeben
- Foto + Versand manuell tracken

**Option B (Semi-Automatisiert):**
- Etsy-API-Integration (Bestellungen → Google Sheets / Airtable)
- Automatische Bestätigungsmails via Zapier/Make
- Dashboard für Harald/Leon (Status: Gravieren, Foto, Versand)

**Option C (Full-Stack):**
- Etsy-API + eigene Backend-DB (wenn später PostgreSQL aufgesetzt)
- Inventory sync (max. 30 Urnen/Monat)
- Automatische Lagererkennung

**Empfehlung:** **Option A starten** (manuell, aber robust), später zu B wechseln wenn Volumen steigt.

**Deliverables:**
- Prozess-Doku für Bestellabwicklung (Handover Harald → Leon → Versand)
- Template für Bestätigungsmails

### Phase 3: Website ↔ Etsy Synchronisation (1–2 Tage)
- Landing-Page zeigt Links zu Etsy (Footer + "Auf Etsy ansehen" Buttons)
- Etsy-Listings verlinken zurück auf Website (im Listing-Text)
- Beide kanäle haben identische Produktinfo (Copy-Paste oder CMS später)

**Deliverables:**
- Etsy-Links in Impressum + Footer
- Produkttext-Versionskontrolle (Keep-in-sync Checkliste)

### Phase 4: Monitoring & Optimierung (Laufend)
- Etsy-Analytics anschauen (Views, Conversions, Feedback)
- Kundenbewertungen sammeln
- Website basierend auf Etsy-Feedback iterieren
- Saisonalität tracken (Dez = Weihnachten, Hochkonjunktur?)

---

## 💾 Dateistruktur

```
.
├── index.html                 # Landing Page (Single File)
├── README.md                  # Kurzbeschreibung
├── CLAUDE.md                  # Diese Datei
├── .claude/
│   ├── settings.json          # (Zukünftig: Claude-Code Config)
│   └── launch.json            # (Zukünftig: Dev-Server Config)
├── images/
│   ├── logo.png               # Bischoff Logo
│   ├── produktfoto.png        # Produktfoto (Urne mit Gravur)
│   └── ...                    # Weitere Assets
├── .git/                      # Git History
└── .gitignore                 # (Zukünftig: .env, node_modules, etc.)
```

---

## 🎨 Design & Brand

- **Farben:** Warm-White, Charcoal, Wood-Gold (#8B6334), Sage-Green
- **Font:** Serif (Georgia) für Headlines, Sans (System) für Body
- **Ton:** Würdevoll, persönlich, handwerklich (kein Maschinelles)
- **Logo:** 100px Desktop, 72px Mobile

---

## 🔐 Wichtige Beschlüsse & Feedback

### Header/Navigation (Abgeschlossen)
- **Problem:** Desktop-Menü verschwand nach Mobile-Fix wegen `backdrop-filter` Containing-Block-Bug
- **Lösung:** Mobile-Menü als separates Overlay-Panel außerhalb `<header>`, Desktop-Nav bleibt fest im Header
- **Grund:** Saubere Trennung, kein DOM-Verschiebe-Hack

### Formularfelder (Abgeschlossen)
- **Problem:** Overflow auf Mobile wegen `<strong>` + Text als separate Flex-Items
- **Lösung:** Alle Listentexte konsequent in `<span>` wrappen, `min-width: 0` auf Grid/Flex
- **Grund:** Text kann jetzt korrekt umbrechen

### Pinch-Zoom (Offen)
- Aktuell: Aktiviert (Accessibility)
- Option: Mit `user-scalable=no` deaktivieren (wenn User Experience dringend nötig)
- Status: Nach Feedback entscheiden

---

## 📝 Nächste Schritte (Priorisiert)

1. **[Morgen/Diese Woche]** Etsy-Shop erstellen, 3 Produktlistings anlegen
2. **[Diese Woche]** Bestellabwicklungs-Prozess dokumentieren (mit Harald klären)
3. **[Diese Woche]** Impressum-Platzhalter ausfüllen, Etsy-Link hinzufügen
4. **[Später]** Bei Bedarf: Inventory-Management System (Airtable/Sheets)
5. **[Später]** Bei Bedarf: Etsy-API für automatische Bestell-Benachrichtigungen

---

## 🚀 Wie man dieses Projekt fortführt

### In neuen Claude-Code Sessions:
1. Lies diese `CLAUDE.md` zuerst (gibt dir alle Kontexte)
2. Schau ins `.claude/memory/` Verzeichnis für projektspezifische Notes
3. Sieh dir letzte Git-Commits an (`git log --oneline`)

### Für Änderungen am Code:
- Arbeite direkt auf `index.html` (Single File, keine Build-Steps)
- Teste im Browser mit `python -m http.server 8811`
- Commit mit aussagekräftiger Message + `Co-Authored-By`

### Bei Fragen zum Status:
- Check `CLAUDE.md` (diese Datei)
- Check `.claude/memory/` für Context
- Check GitHub Issues (falls später genutzt)

---

**Zuletzt aktualisiert:** 12. Juli 2026  
**Von:** Claude (Sonnet 5)  
**Status:** ✓ Landing Page fertig, ⏳ Etsy-Integration in Planung
