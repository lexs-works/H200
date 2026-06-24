![H200 · IN DEVELOPMENT](https://img.shields.io/badge/H200-WIP-c8a86b?style=for-the-badge&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyMCIgaGVpZ2h0PSIyMCIgdmlld0JveD0iMCAwIDI0IDI0IiBmaWxsPSJub25lIiBzdHJva2U9IiNjOGE4NmIiIHN0cm9rZS13aWR0aD0iMiIgc3Ryb2tlLWxpbmVjYXA9InJvdW5kIiBzdHJva2UtbGluZWpvaW49InJvdW5kIj48Y2lyY2xlIGN4PSIxMiIgY3k9IjEyIiByPSIxMCIvPjxwYXRoIGQ9Ik0xMiA4djRsMiAyIi8+PC9zdmc+)

[[EN](https://github.com/lexs-works/H200/blob/master/README.md) • [DE](https://github.com/lexs-works/H200/blob/master/README.de.md) • [RU](https://github.com/lexs-works/H200/blob/master/README.ru.md)]

# 🚀 H200 — Eine Lötstation im Marker-Format, gespeist über USB-C

> **H200 / Solderis OS Version:** 0.α.0626 (AEGIS VerSystem) <br/>
> **Primäres Repository:** [~ax-hack/H200](https://git.sr.ht/~ax-hack/H200)

**H200 (Hacked 200)** ist ein tiefgreifendes Hacker-Remaster des beliebten Lötkolbens PTS200 V2. Die ursprüngliche Ergonomie wurde beibehalten und durch eine proprietäre, griffige Beschichtung ergänzt. Die gesamte Billig-Elektronik wurde verworfen und durch eine fehlertolerante, industrietaugliche Komponentenbasis ersetzt.

Dies ist eine Lötstation in einem Gehäuse von der Größe eines Marker-Stifts — so zuverlässig wie Solaris, so einfach wie UNIX v6. Entwickelt für die professionelle Instandsetzung komplexer Elektronik und präzise R&D-Montagearbeiten.

Warum eine Lötstation und nicht einfach ein Lötkolben? Viele sind daran gewöhnt, dass eine Lötstation ein Kästchen mit Kabel ist, an dem man die Temperatur einstellt. Doch die Zeit schreitet voran, die Technik entwickelt sich weiter — heute können wir die Regelung und Temperaturhaltung in einem stiftförmigen Gehäuse unterbringen, und zwar mit einer Abweichung von nicht mehr als ±1 °C.

Ermöglicht wird dies durch einen robusten, industrietauglichen Controller, den Einsatz analoger Schaltungskomponenten und ein kompromissloses Betriebssystem, das speziell für diese Station geschrieben wurde — Solderis OS.

Dies ist ein Instrument des Premium-Segments, frei von geplanter Obsoleszenz. Die garantierte Lebensdauer beträgt 10 Jahre — gewährleistet in erster Linie durch die Komponentenbasis, die Schaltungsarchitektur und die Fertigungsqualität.

In der Lötstation wird die Hardwareschutzschaltung durch ein analoges Pendant abgesichert, das nahezu verzögerungsfrei eingreift:

- gegen Kurzschlüsse
- gegen Systemschock — selbst wenn die Spitze in einen Eisblock gesteckt wird, heizt die Station unbeirrt weiter
- gegen Netzteilwelligkeit

## 🔥 Unterstützung für Spitzen unterschiedlicher Polarität

Dies ist der Ausgangspunkt des Projekts. Ich wurde von Google AI in die Irre geführt, als ich einen Lötkolben für Präzisionsarbeiten unter dem Mikroskop auswählte. Dessen Halluzination teilte mir mit, der PTS200 V2 könne C210-Spitzen über einen externen Adapter und eine benutzerdefinierte Firmware aufnehmen.

Nach kurzem Verdruss studierte ich die Materie und dachte: Wenn es das nicht gibt — warum nicht selbst bauen? So entstand das Konzept eines Lötkolbens in einem ergonomischen Gehäuse, mit Unterstützung für zwei grundlegend verschiedene Spitzen-Familien.

### 🪓 Physik der Spitzen: Unterstützte Kartuschen

#### Familie 1: Zwei-Draht-Kartuschen (TS100 / TS101 / T12)

Physik: Heizelement und Thermoelement sind innerhalb der geschlossenen Kartusche in Reihe geschaltet. Die Spitze besitzt zwei Kontakte (Plus und Minus). Das Signal hat positive Polarität (+9 mV bei 350 °C).

#### Familie 2: Drei-Draht-Kartuschen (C210 / JBC-Stil)

Physik: Heizelement und Thermoelement sind entkoppelt und parallel geführt. Die Spitze besitzt drei Kontakte: Heizer-Plus, gemeinsame Masse und einen dedizierten Signal-Kontakt für das Thermoelement. Das Signal ist kontinuierlich, hat jedoch negative Polarität gegenüber Masse (-13 mV bei 350 °C). Eine direkte Einspeisung in den MCU-Eingang würde den Chip zerstören.

> **Ingenieurtechnisches Fazit:** Sie können ultra-kurze C210-Spitzen über ein Adapterkabel mit einem leichten, abgesetzten Handstück für juweliergleiches WLCSP-Löten unter dem Mikroskop verwenden — und nach einem Profilwechsel im Menü den H200 Pro auf eine schwere, wärmekapazitive T12-Spitze umstellen, um massive Masseflächen auf Multilayer-Platinen zu erwärmen.

## 💪 Probleme, die die Station löst

### Bestückung von Multilayer-Platinen mit hoher Wärmeableitung

Ehrliche 100 W Leistung an niederohmigen Kartuschen und vollständige Hardware-Unterstützung für schwere Spitzen der T12-Serie über einen Wechseladapter. Die physikalische Masse des Metalls gewährleistet Temperaturstabilität auf durchgehenden Masseflächen.

### Mikrochirurgie und Leiterbahnreparatur unter BGA-Komponenten

Anschluss eines abgesetzten JBC-C210-Handstücks über ein flexibles Schnittstellenkabel. Das Umschalten von Solderis OS in den differentiellen, invertierenden Erfassungsmodus erlaubt die präzise Regelung der negativen Spannung des JBC-Thermoelements.

Und der sorgfältig abgestimmte Assembler-PID-Code liefert eine Regelungslatenz des Thermoelements im Nanosekundenbereich.

### Unterbrechungsfreier kommerzieller 24/7-Betrieb

Ein analoger Komparator kappt einen Kurzschlussstrom 15 Nanosekunden, bevor die CPU reagieren kann. Der Eingang ist durch einen TVS-Suppressor gegen netzseitige Welligkeit geschützt, und das transflektive LCD ist hardwaremäßig gegen Einbrennen und elektrostatische Entladung (ESD) gesichert.

## 💣 Technologische Kernentscheidungen

1. **Analoge Panzerung — Hardware-Kurzschlussschutz**
2. **Immunität gegen Netzteilwelligkeit**
3. **Allesfresser: Zwei polare Spitzen-Familien:**
    * *TS100/TS101/T12*
    * *C210 (JBC-Stil)*
4. **Transflektives LCD anstelle von OLED**
5. **Hybrider Schlafmodus ohne Kernabfrage**

## ⚙️ Betriebssystem

Für die Lötstation H200 wurde ein eigenes, ereignisbasiertes Betriebssystem entworfen und wird derzeit entwickelt: Solderis OS.

Systemphilosophie: Solaris-artige Zuverlässigkeit bei UNIX v6-artiger Einfachheit.

Das Betriebssystem wird in ARM Thumb-2 Assembler und C89 geschrieben. Keine Kompromisse — nur Zuverlässigkeit, Einfachheit und Leistung.

Das Betriebssystem ist um einen nicht-blockierenden Ringpuffer herum aufgebaut.

## 💯 200% Open Source

Das gesamte Projekt wird offengelegt — vom Herstellungsprozess des Gehäuses bis zum Quellcode der Assembler-Bestückung.

Der Quellcode wird im offiziellen Repository auf SourceHut bereitgestellt: [~ax-hack/h200](https://git.sr.ht/~ax-hack/H200). Der vollständige Code aller Komponenten wird nach Abschluss der Crowdfunding-Kampagne veröffentlicht.

### In der Entwicklung von H200 verwendete Werkzeuge

Bei der Arbeit an der Lötstation nutze ich meine bevorzugten Open-Source-Werkzeuge:

- BRL-CAD
- NGSPICE
- KiCAD
- etc.

## 🔏 Schutz vor Fälschungen

Offenheit schafft ein hundertprozentiges Fälschungsrisiko. Wie man so schön sagt: Nimm es und bau es nach. Das Originalgerät, vom Entwickler, mit 10-jähriger Garantie, wird mit einem nicht fälschbaren kryptografischen Schlüssel auf Basis von PUF-Kryptografie signiert sein.

Alle offiziellen Geräte werden in der Datenbank der Entwickler-Website registriert. Zur Identifikation wird das Gerät per USB an einen Computer angeschlossen und die Identifikation in einem speziellen Bereich der Website durchgeführt — Originalgeräte erhalten die Möglichkeit zu einfachen Updates sowie Zugang zur Autorenbibliothek der Kalibrierungsdaten für Spitzen.

Der Autor versteht die Unvermeidbarkeit des Klonens, selbst bei geschlossenem Quellcode. Der Autor liebt und respektiert die Open-Source-Kultur gleichermaßen — daher die Entscheidung, die Plattform vollständig zu öffnen.

Der Preis eines Originalgeräts beim Kauf im Crowdfunding repräsentiert nicht nur die Kosten für die Gehirnarbeit des Autors, sondern auch die Kosten für eine ehrliche 10-Jahres-Garantie und Service.

## 🚚 Wie erwirbt man die portable Lötstation H200?

Zum gegenwärtigen Zeitpunkt: gar nicht. Der Autor arbeitet am Forschungsprototyp und an der Implementierung des Betriebssystems. Sie können das Voranschreiten der nächsten Phase jedoch auf folgenden Wegen beschleunigen:

- Eine Spende für Kaffee und Kolophonium über den GitHub-Button
- Ein Stern auf GitHub.

### Phasen des Markteintritts und Produktversionen:

* **H200 Pro** Founders Edition — eine Auflage von 97 Stück. Die Standardversion der Lötstation, basierend auf einer Leiterplatte, wobei die Bestückung der Komponenten persönlich vom Autor unter dem Mikroskop vorgenommen wird.
* **H200 Medusa** Creator's Edition — eine Auflage von 3 Stück. 3 Sammlerstücke; Ingenieurskunst — gelötet in freier Verdrahtung, mit einem Saphir-Sichtfenster im Gehäuse — zur Betrachtung der inneren Schönheit.
* **H200 Pro** — eine Kleinserie, wird nach Bedarf produziert, vollständig industriell bestückt.

Die Produkteinführung ist per Crowdfunding geplant.

### ✅️ Crowdfunding und Founders Edition

Die Vorbestellerkampagne wird für ein strikt limitiertes Kontingent gestartet — **100 Exemplare**, vollständig gelötet, geflasht und getestet persönlich vom Autor unter dem Mikroskop. Keine externen Fertigungsbetriebe. Nur vollständige Qualitätskontrolle und eine ehrliche **10-Jahres-Garantie**.

🥇 **The Ultimate Tier (nur 3 Exemplare):**
Die drei Unterstützer mit der höchsten Spende erhalten eine exklusive Version, **H200 Medusa (Creator's Edition)**: ein Lötkolben mit einem Sichtfenster aus Saphirglas. Im Inneren sichtbar: die Prozessor-Peripherie, von Hand vom Autor in der „Medusa"-Freiverdrahtungstechnik montiert, mit feinen, lackierten Mikrodrähten. Für diese drei Geräte wird ein einzigartiges kryptografisches Zertifikat generiert.

### 🔄 Versionierung (AEGIS)

Das Projekt folgt dem **AEGIS**-Versionierungssystem (siehe [AEGIS-Spezifikation](https://github.com/lexs-works/AEGIS)).
* Aktueller Meilenstein: **`0.α.0626`**
* Status: Die theoretische Architektur der Hardware-Software-Plattform ist abgeschlossen. Die manuelle Montage des Forschungs-R&D-Aufbaus **„Medusa Proto"** in freier Verdrahtung auf einer Kupfer-Grundplatte läuft — zur Validierung des analogen Schutzes und zum Debuggen des Assembler-PID-Codes.

## 🌌 Zukünftiger Meilenstein (GEN2): H200 Rad-Hard Edition

> **Aktueller Status:** R&D-Konzeptentwurf. Ein Übergang von der Silizium-Mikroelektronik zur Vakuum-Nanoelektronik und zu mikroelektromechanischen Systemen (MEMS).

Die nächste fundamentale Iteration des H200-Projekts wird für den Betrieb unter Bedingungen entworfen, die jeden Menschen zuverlässig töten — nicht jedoch dieses Werkzeug: offener Weltraum, Zonen harter Sonneneinstrahlung und die innere Eindämmung zerstörter Kernreaktoren.

### Technologisches Manifest der Rad-Hard-Version:

1. **Spindt-Kathoden anstelle von Silizium (Mikro-Vakuum-Trioden):**
   Sämtliche Silizium-Halbleiter (einschließlich MOSFETs und Logikgatter), anfällig für Strahlungsdegradation und thermisches Durchgehen, werden vollständig durch Arrays von Spindt-Feldemissionskathoden ersetzt. Logik- und Leistungsschaltung werden von mikroskopischen Vakuum-Trioden übernommen, die direkt ins Substrat integriert sind. Elektronen fliegen durch Vakuum; daher sind Gammastrahlung und Neutronenfluss physikalisch nicht in der Lage, einen irreversiblen Strukturdurchbruch zu verursachen.
2. **MEMS-Schaltung und analoge Logik:**
   Für das physische Schalten von Messpfaden und die Leistungssteuerung kommen mikroelektromechanische Systeme (MEMS) zum Einsatz. Mechanische Mikro-Relais auf Silizium-/Metallträgern gewährleisten eine physische Trennung der Stromkreise, absolute Immunität gegen elektromagnetische Impulse (EMP) und strahlungsinduzierte Störspannungen.
3. **Überlebensphilosophie:**
   Dieser Lötkolben ist so konstruiert, dass er stabile 350 °C an der Spitze einer C210-Nadel hält, selbst wenn die Umgebung von Hintergrundstrahlung glüht. Er wird als Monument menschlicher Ingenieurskunst weiterarbeiten, wenn der Ingenieur selbst bereits zu Staub zerfallen ist.

---

## ⚖️ Rechtlicher Hinweis / Disclaimer

> **WICHTIGER HINWEIS:** Sämtliche Erwähnungen von Kernreaktoren, Weltraum, Spindt-Kathoden, Strahlungshärte und Systemen zum Überleben unter apokalyptischen Bedingungen sind ausschließlich künstlerische Fiktion des Autors, konzeptioneller wissenschaftlich-phantastischer Unsinn (Cyberpunk-Fanfiction) und ein Marketinginstrument, um Aufmerksamkeit auf die Open-Source-Kultur zu lenken. <br/> Der Autor ist ein gewöhnlicher, enthusiastischer Schwätzer, der einfach 100 gute Lötkolben für die iPhone-Reparatur bauen möchte. Das Gerät ist nicht für den Betrieb im Weltraum oder den Einsatz im Inneren des Kernkraftwerks Tschernobyl vorgesehen. Ehrlich.

> Solaris ist eine eingetragene Marke der Oracle Corporation. UNIX ist eine eingetragene Marke von The Open Group. Die Erwähnung von Marken erfolgt ausschließlich im Kontext des qualitativen Produktvergleichs.

## 📬 Kontakte

Wenn Sie kommerzielle Anfragen, B2B-Kooperationsangebote haben oder die Architektur von Solderis OS außerhalb von Mailing-Listen diskutieren möchten:

* **⚡ Threema:** [9FM22ZUC](https://threema.id/9FM22ZUC) (Hauptkanal für schnelle Kommunikation; ***bitte beginnen Sie Ihre Nachricht mit [H200]***)
* **🌐 SourceHut-Profil:** [~ax-hack](https://git.sr.ht/~ax-hack/)
* **🌐 SourceHut PROJEKT-REPO:** [~ax-hack/h200](https://git.sr.ht/~ax-hack/H200)
* **📧 E-Mail:** `h200@lexs.work` (Für formelle Anfragen und git-mail-Patches)

> **Hinweis:** Die Korrespondenz via E-Mail und Threema erfolgt derzeit ausschließlich auf Englisch.

### 🔬 Ingenieur-Community

Ich betreibe zudem einen geschlossenen Signal-Kreis — eine Gruppe, in der ich Arbeitsnotizen zu Ingenieurswesen, Architekturentwurf, Softwareentwicklung und die verborgene Seite der kommerziellen Welt veröffentliche.

Der Beitritt zur Gruppe erfolgt auf Anfrage via Threema oder über den Telegram-Bot: [@lexs_gatekeeper_bot](https://t.me/lexs_gatekeeper_bot).

**Die Gruppensprache ist Englisch.**

## ☕ Kaffee & Kolophonium

| Coin / Netzwerk | Wallet-Adresse | Guthaben prüfen |
| :--- | :--- | :--- |
| **Bitcoin (BTC)** | `bc1q3flezaz48a6a445yf5ncxyfkmkdr9u830kzqgv` | [🔍 Explorer](https://blockchair.com) |
| **Litecoin (LTC)** | `ltc1qqa0zd6p5aevp4wv0fxdvzujn9yykl6f8zudpj9` | [🔍 Explorer](https://blockchair.com) |
| **USDT** (Polygon / Arbitrum) | `0x1A645b36D41C38732cdB696dB8AAf2bCB38CB2E8` | [🔍 Explorer](https://blockchair.com) |

> ⚠️ Wichtig bei USDT: bitte nur über Polygon oder Arbitrum senden — so vermeidet ihr die horrenden Gebühren des Ethereum-Hauptnetzes. Die Adresse ist für beide Netzwerke dieselbe.