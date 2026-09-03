# Formatierungsregeln für das Literaturverzeichnis

## 1. Kategorien (Abschnitte)

Das Verzeichnis ist in **5 Abschnitte** gegliedert, jeweils mit kurzer Einleitung:

1. **Wissenschaftliche Publikationen** — Einleitung: „Folgend werden referenzierte wissenschaftliche Publikationen aufgeführt."
2. **Normen und Richtlinien** — Einleitung: „Im Folgenden werden referenzierte Normen und Richtlinien aufgeführt."
3. **Publikationen der Autorin** — Einleitung: „Im Folgenden werden referenzierte Publikationen der Autorin aufgeführt."
4. **Studentische Arbeiten** — Einleitung: „Im Folgenden werden studentische Arbeiten aufgeführt. Diese sind mit % am Ende des Kurzbelegs kenntlich gemacht."
5. **Internetquellen und Software** — Einleitung: „Im Folgenden werden referenzierte Internetquellen und Software aufgeführt. Diese sind mit @ kenntlich gemacht."

## 2. Zitierschlüssel-Schema `[Kurzbeleg]`

### 2.1 Wissenschaftliche Publikationen

- **1 Autor:** Erste 3 Buchstaben Nachname + 2-stelliges Jahr
  - Beispiel: Henry **Blo**ch, 20**24** → `[Blo24]`
  - Beispiel: Thomas **Hol**m, 20**16** → `[Hol16]`
  - Beispiel: Stephan H. **May**er, 20**09** → `[May09]`
- **2 Autoren:** Erste 2 Buchstaben Nachname Autor 1 + Erste 2 Buchstaben Nachname Autor 2 + 2-stelliges Jahr
  - Beispiel: Johannes **Al**enius + Mats **Mi**llnert, 20**08** → `[AlMi08]`
  - Beispiel: Geoff **Bl**ack + Valeriy **Vy**atkin, 20**07** → `[BlVy07]`
- **3+ Autoren:** Erste Buchstaben der Nachnamen der ersten Autoren + `+` + 2-stelliges Jahr
  - Beispiel: **B**ossut, **D**e Gracia, **I**yer + weitere, 20**25** → `[BDI+25]`
  - Beispiel: **B**loch, **F**ay, **K**lose + weitere, 20**17** → `[BFK+17]`
  - Die Anzahl der explizit genannten Initialen variiert (typisch 3, manchmal 2), der Rest wird durch `+` abgedeckt
- **Herausgeber-Werke / Bücher ohne typischen Autorenbeleg:** Erste 3 Buchstaben Nachname + 2-stelliges Jahr
  - Beispiel: Rainer **Dra**th, 20**21** → `[Dra21]`
  - Beispiel: Thomas **Tau**chnitz, 20**22** → `[Tau22]`

### 2.2 Sondermarkierungen

- **`*` (Stern)** am Ende des Schlüssels: Kennzeichnet **Publikationen der Autorin** (eigene Veröffentlichungen)
  - Beispiel: `[BFG+21*]`, `[Blu26*]`
- **`%` (Prozent)** am Ende des Schlüssels: Kennzeichnet **studentische Arbeiten**
  - Beispiel: `[Hen22%]`, `[Jan23%]`
- **`@` (At)** am Ende des Schlüssels: Kennzeichnet **Internetquellen und Software**
  - Beispiel: `[Aut25@]`, `[Fra25@]`

### 2.3 Normen und Richtlinien

- Verwenden die **offizielle Normenbezeichnung** als Schlüssel (keine Abkürzung aus Autorennamen)
  - Beispiel: `[VDI 2510]`, `[IEC 61131-3]`, `[NE 171]`, `[OPC 10000-3]`, `[MTP Specification Part 1]`

## 3. Eintragsformate nach Publikationstyp

### 3.1 Zeitschriftenartikel (In: Zeitschrift)

```
[Key] Autor1, Autor2 und Autor3: „Titel". In: Zeitschriftenname Band.Heft (Jahr), S. Seiten.
```

- Bei 3+ Autoren: „Autor1 u. a." (= und andere / et al.)
- Optionaler `url:`-Zusatz am Ende
- Beispiel:
  ```
  [BDI+25] Mathilde Bossut u. a.: „Globale Krisen bewältigen...". In: Wirtschaftsdienst 105.3 (2025), S. 205–211. url: https://...
  ```

### 3.2 Konferenzbeitrag (In: "Konferenzname")

```
[Key] Autor(en): „Titel". In: "Konferenzname". [Hrsg. von ...] [Bd. X. Reihe.] [Ort: Verlag,] Jahr[, S. Seiten].
```

- Konferenzname steht in doppelten Anführungszeichen
- Beispiel:
  ```
  [BFK+17] Henry Bloch u. a.: „A microservice-based architecture...". In: "22nd IEEE International Conference on Emerging Technologies and Factory Automation (ETFA)". 2017.
  ```

### 3.3 Buch / Monografie

```
[Key] Autor(en): "Buchtitel". [Auflage.] [Reihe.] Ort: Verlag, Jahr. [url: ...]
```

- Buchtitel in doppelten Anführungszeichen (englisch-typografisch)
- Beispiel:
  ```
  [Dra21] Rainer Drath, Hrsg.: "AutomationML: A practical guide". De Gruyter graduate. Berlin und Boston: De Gruyter Oldenbourg, 2021.
  ```

### 3.4 Buchkapitel (In: "Buchtitel")

```
[Key] Autor(en): „Kapiteltitel". In: "Buchtitel". Hrsg. von Editor(en). [Bd. X. Reihe.] Ort: Verlag, Jahr, S. Seiten.
```

### 3.5 Dissertation

```
[Key] Autor: „Titel". Dissertation. Ort: Universität, Jahr. [url: ...]
```

- Beispiel:
  ```
  [Blo24] Henry Bloch: „Verifikationsmethode für...". Dissertation. Hamburg: Helmut-Schmidt-Universität Hamburg, 2024.
  ```

### 3.6 Master-/Bachelorthesis (Studentische Arbeiten)

```
[Key%] Autor: „Titel". Masterthesis/Bachelorthesis. Ort: Universität, Jahr. [url: ...]
```

### 3.7 Patent

```
[Key] Autor(en): „Titel: World Patent/European Patent". Patentnummer. Jahr. url: ...
```

### 3.8 Norm / Richtlinie

```
[Normbezeichnung] Herausgebende Organisation: "Normbezeichnung: Titel". Ort, Jahr. url: ...
```

### 3.9 Internetquelle / Software

```
[Key@] Autor/Organisation: "Titel". [Hrsg. von ...] Jahr. url: ...
```

- oder bei Artikeln:
  ```
  [Key@] Autor: „Titel". Jahr. url: ...
  ```

## 4. Typografische Konventionen

- **Anführungszeichen für Titel:**
  - Deutsche Anführungszeichen „..." für Aufsatz-/Artikeltitel
  - Englische/typografische Anführungszeichen "..." für Buch-/Konferenztitel
- **Seitenangaben:** `S. 205–211` (mit Gedankenstrich `–`, nicht Bindestrich `-`)
- **Mehrere Autoren:** `Autor1, Autor2 und Autor3` (letzter mit „und")
- **Viele Autoren (≥4):** `Erstautor u. a.` (= et al.)
- **Herausgeber:** `Hrsg. von Vorname Nachname`
- **Band/Reihe:** `Bd. X. Reihenname.`
- **Ort + Verlag:** `Ort: Verlag, Jahr`
- **Mehrere Orte:** `Berlin und Boston` oder `Berlin, Heidelberg`
- **URL:** `url: https://...` (Kleinbuchstabe „url", gefolgt von Doppelpunkt und Leerzeichen)

## 5. Sortierung

- Innerhalb jeder Kategorie: **alphabetisch nach Zitierschlüssel** sortiert
- Zitierschlüssel mit Sonderzeichen (`*`, `%`, `@`) werden für die Sortierung ohne das Sonderzeichen betrachtet

## 6. Sprache

- Gemischt deutsch/englisch: Deutsche und englische Titel verwenden dieselben Anführungszeichen
- Strukturwörter immer deutsch: „In:", „Hrsg. von", „u. a.", „S.", „Bd.", „url:"
- Umlaute in Autorennamen werden korrekt dargestellt (ä, ö, ü, é, etc.)
