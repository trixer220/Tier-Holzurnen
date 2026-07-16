# Etsy-Integration: Detaillierter Plan

## 📌 Ziel
Etsy als zweiter Verkaufskanal (neben direkter Website) mit minimalem Overhead für die Handwerker.

---

## 🏗️ Phase 1: Shop-Setup (1–2 Tage)

### 1.1 Etsy-Account & Shop erstellen
**Wenn noch nicht vorhanden:**
1. Auf etsy.com anmelden (mit privatem oder Business-Account)
2. Shop erstellen → Name: "Bischoff Holzurnen"
3. Shop-Einstellungen:
   - **Shop-Foto:** Bischoff Logo (aus `images/logo.png`)
   - **Kurzbeschreibung:** "Handgefertigte Holz-Tierurnen mit individueller Lasergravur — für ein würdevolles Gedenken."
   - **Shop-Richtlinie:** Versand EU-weit, 2–4 Wochen Lieferzeit, Rückgaberecht 14 Tage

### 1.2 Versandoptionen konfigurieren
**Länder:** Alle EU + Schweiz, Norwegen, UK  
**Kosten:** Pauschale pro Paket definieren (z.B. 12€ DE, 18€ EU, 25€ CH/NO/UK) oder Gewicht-basiert

**Lieferzeit:** 2–4 Wochen ab Auftragsbestätigung (deutlich kommunizieren!)

### 1.3 Drei Produktlistings erstellen

#### Listing 1: "Andenken – Basis-Paket"
```
Titel: Personalisierte Holz-Tierurne – Das stille Gedenken
Preis: 149 €
Beschreibung: [Aus Website kopieren]
Fotos: 
  - produktfoto.png (Hauptbild)
  - [Optional: Gravur-Detail-Foto]
  - [Optional: Verpackungs-Foto]

Varianten:
  - Holzart: Eiche / Kirsche
  - Größe: Standard (20×14×10 cm)

Shipping Profile: "EU Standard"
Processing time: 2 weeks
```

#### Listing 2: "Ewige Erinnerung – Mittleres Paket"
```
Titel: Personalisierte Holz-Tierurne mit Foto-Lasergravur – Ewige Erinnerung
Preis: 189 €
[Ähnlich wie Listing 1, aber mit Foto-Highlight in Beschreibung]
Processing time: 3 weeks
```

#### Listing 3: "Für immer bei Dir – Premium-Paket"
```
Titel: Premium Holz-Tierurne mit Gedenkkammer & Detailgravur
Preis: 229 €
Processing time: 4 weeks
```

**Alle Listings:**
- Tags: `holz-tierurne`, `personalisiert`, `lasergravur`, `haustier-gedenken`, `gedenkurne`, `urne-hund`, `urne-katze`
- Kategorie: "Pets" → "Pet Memorials" (oder ähnlich)
- Versandart: "Tracked" (mit Sendungsverfolgung)

---

## 📞 Phase 2: Bestellabwicklung (2–3 Tage)

### 2.1 Prozess-Flowchart

```
┌─────────────────┐
│  Kunde bestellt │  (Etsy oder Website)
│  über Etsy oder │
│  Website        │
└────────┬────────┘
         │
         ▼
┌─────────────────────────────────┐
│ Harald erhält Bestellung        │
│ - Email-Benachrichtigung        │
│ - Kundendaten (Name, Tier, etc) │
│ - Versandadresse                │
└────────┬────────────────────────┘
         │
         ▼
┌─────────────────────────────────┐
│ Harald prüft Kapazität (max 30) │
│ & Machbarkeit (Photo, Größe)    │
└────────┬────────────────────────┘
         │
         ├─── OK ───────────┐
         │                  │
         ▼                  ▼
    ┌─────────────┐    ┌──────────────┐
    │ Bestätigung │    │ Ablehnung    │
    │ senden      │    │ + Rückgeld   │
    │ + Handwerk  │    │              │
    │ übergeben   │    └──────────────┘
    └─────┬───────┘
         │
         ▼
┌─────────────────────────────────┐
│ Leon: Fertigung + Gravur        │
│ (2–4 Wochen, je nach Paket)     │
└────────┬────────────────────────┘
         │
         ▼
┌─────────────────────────────────┐
│ Harald: Foto vor Versand        │
│ - Foto an Kunde                 │
│ - Kundengenehmigung einholen    │
└────────┬────────────────────────┘
         │
         ├─── OK ────────────┐
         │                   │
         ▼                   ▼
    ┌──────────────┐    ┌──────────────┐
    │ Versand      │    │ Anpassung    │
    │ (mit Tracking)    │ neuanfertigen│
    └──────┬───────┘    └──────────────┘
         │
         ▼
┌─────────────────────────────────┐
│ Tracking-Nummer an Kunde        │
│ + Dankeschön-Nachricht          │
└─────────────────────────────────┘
```

### 2.2 Bestellformular-Template (Airtable/Google Sheets)

**Spalten:**
- Order-ID (Etsy oder Website #)
- Quelle (Etsy / Website)
- Datum eingegangen
- Kunde (Name, Email, Telefon)
- Tier (Art, Name, Geb/Tod)
- Paket (Andenken / Ewige Erinnerung / Premium)
- Holzart (Eiche / Kirsche)
- Gravur-Spruch
- Versandland
- Status (Eingegangen → Gravieren → Foto → Genehmigt → Versand → Abgeschlossen)
- Fermigungstart-Datum
- Foto-Datum
- Versanddatum
- Tracking-Nummer
- Notizen

**Automation (Optional mit Zapier/Make):**
- Etsy-Bestellung → Automatisch neue Zeile in Sheets
- Status-Änderung → Email-Benachrichtigung an Harald

### 2.3 Email-Templates

#### Bestätigungsmail (Harald verfassen, dann Copy für zukünftige)
```
Betreff: Deine Tierurnen-Anfrage – Wir machen es wirklich

Hallo [Kundenname],

herzlichen Dank für deine Bestellung! 🐾

Wir haben deine Anfrage für [Tiername]'s [Paket-Name] Urne erhalten.

📝 Deine Bestellung im Überblick:
- Tier: [Tiername] ([Art], [Geb-Tod])
- Paket: [Paket-Name]
- Holzart: [Eiche/Kirsche]
- Gravur: [Spruch]
- Versand nach: [Land]

🛠️ So geht es weiter:
Wir beginnen mit der Fertigung sofort. In [2–4] Wochen machen wir ein Foto der fertigen Urne und schicken es dir zur Bestätigung. Dann versenden wir sie mit Tracking zu dir.

Falls es noch Fragen gibt, antworte einfach auf diese Mail. Wir sind hier! 

Mit warmem Herzen,
Harald & Leon Bischoff
```

#### Foto vor Versand (mit Anleitung)
```
Betreff: Deine Tierurne ist fertig – Sieh sie dir an! 📸

Hallo [Kundenname],

[FOTO ANHÄNGIG]

Deine Tierurne für [Tiername] ist fertig. Das ist sie oben! 

Wenn alles aussieht wie gewünscht: Einfach antworten mit "OK" und wir versenden sie sofort.
Falls etwas angepasst werden soll, gib uns Bescheid – wir machen das gerne.

Versand dann innerhalb von 2–3 Tagen.

Lieben Gruß,
Harald & Leon
```

---

## 🔗 Phase 3: Website ↔ Etsy Synchronisation (1–2 Tage)

### 3.1 Landing-Page Updates

**Footer anpassen:**
```html
<a href="https://www.etsy.com/shop/DEIN-SHOP-NAME" target="_blank" rel="noopener noreferrer">
  Auf Etsy ansehen & kaufen
</a>
```

**Paket-Card "Paket wählen" Buttons:**
Option A: Bleibt auf Website (direktes Formular)  
Option B: Für Etsy-Käufer → Button zu Etsy-Listing

**Empfehlung:** A + B kombiniert:
- "Jetzt anfragen" → Website-Formular (direkter Kontakt)
- "Auf Etsy kaufen" → Etsy-Listing (mit Käuferschutz)

### 3.2 Produkttext-Synchronisation
**Problem:** Infos stehen überall (Website + 3 Etsy-Listings) — Änderungen sind Mehrarbeit

**Lösung (einfach):** 
- Definitive Quelle: `CLAUDE.md` unter "Paket-Beschreibungen"
- Jede Änderung: 1x in `CLAUDE.md` updaten, dann in Website + Etsy per Copy-Paste

**Lösung (professionell später):**
- Airtable-Base mit Produkttabelle
- Google Sheets add-on oder Zapier synct zu Etsy + Website

---

## 📊 Phase 4: Monitoring & Optimierung (Laufend)

### 4.1 Metriken zum Tracken
- Etsy-Views & Klicks (Shop-Admin)
- Conversion-Rate (Besucher → Bestellung)
- Kundenbewertungen (Etsy & Website)
- Durchschnittliche Lieferzeit vs. versprochene
- Rücksendungen / Reklamationen

### 4.2 Quartals-Review
Jeden 3 Monate:
- [ ] Etsy-Analytics anschauen
- [ ] Top-Seller vs. Flops identifizieren
- [ ] Kundenfeedback zusammenfassen
- [ ] Website + Etsy-Listings entsprechend updaten

### 4.3 Saisonalität planen
- **Dezember:** +300% (Weihnachtsgedenk-Trend)
- **Jan/Feb:** Spike nach Neujahrs-Trauer
- **Mai/Juni:** Sommerferien, weniger Nachfragen
- **Sept:** Zurück-zur-Routine, Nachfrage steigt

**Handlung:** Capacity-Planning (extra 4 Wochen Vorlauf vor Dezember)

---

## 💰 Kosten-Übersicht (Etsy)

| Was | Kosten | Notizen |
|-----|--------|---------|
| Etsy Shop (monatlich) | $20 | Shopgebühr |
| Listing-Gebühr pro Artikel | $0,20 | 1x beim Anlegen |
| Verkaufsgebühr | 6,5% | Vom Verkaufspreis |
| Payment Processing | 3% + $0,20 | PayPal/Stripe |
| **Total pro 149€-Verkauf** | ~15–18€ | ~10–12% Margin |

→ Bei 30 Urnen/Monat (à ~180€ Ø): ~€90–150 Etsy-Kosten → akzeptabel

---

## ⚠️ Häufige Fallstricke

1. **Lieferzeit zu optimistisch** → Verspätete Lieferung → Negative Bewertung
   - Lösung: 2–4 Wochen promise, 1,5–2,5 real liefern

2. **Produktfotos schlecht** → Niedrige Klickrate
   - Lösung: Professionelle Foto vor Versand machen, beste bei Etsy nutzen

3. **Doppelte Bestellungen** (Etsy + Website gleichzeitig)
   - Lösung: Kapazitäts-Counter im Airtable, sofort updaten

4. **Keine Erwartungs-Management** → "Warum dauert es so lange?"
   - Lösung: In jede Bestätigungsmail: "2–4 Wochen ist normal, ihr Tier ist nicht vergessen"

5. **Etsy-Bewertungen ignorieren** → Reputation sinkt
   - Lösung: Weekly Check-in, auf jede Review antworten (positiv & negativ)

---

## 📋 Checkliste: Go-Live Etsy

- [ ] Etsy-Account erstellt
- [ ] Shop mit Logo & Beschreibung aufgebaut
- [ ] 3 Produktlistings live (mit Fotos & Tags)
- [ ] Versandprofile konfiguriert
- [ ] Email-Templates fertig (Bestätigung, Foto vor Versand)
- [ ] Airtable/Sheets-Template für Bestellungen aufgesetzt
- [ ] Bestellabwicklungs-Prozess mit Harald durchgesprochen
- [ ] Website mit Etsy-Links aktualisiert
- [ ] Erste Test-Bestellung durchführen (selbst kaufen, prüfen)
- [ ] Bewertung hinterlassen (als echtes Feedback)

---

## 🚀 Roadmap nach Etsy-Launch

### Monat 1–3: Stabilisierung
- Prozesse einfahren
- Kundenfeedback sammeln
- Bewertungen aufbauen (Ziel: 20+ mit 4.8⭐)

### Monat 3–6: Optimierung
- Best-Seller ermitteln
- Etsy Ads testen (optionalale Paid Traffic)
- Website-SEO verbessern (Google-Rankings)

### Monat 6–12: Skalierung
- Ggf. Inventory-System (API-Sync Etsy ↔ Sheets)
- Automatische Bestätigungsmails
- Etsy-TikTok/Instagram Integration

### Jahr 2: Expansion
- Weitere Nischen erkunden (z.B. Vogel-, Fische-Urnen)
- Evtl. eigener Online-Shop (Shopify/WooCommerce) für bessere Margins
- Kooperationen mit Tierkrematorien

---

**Erstellt:** 12. Juli 2026  
**Status:** Planung  
**Nächster Review:** Nach Etsy-Launch
