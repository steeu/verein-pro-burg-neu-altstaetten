# CLAUDE.md — Website Burgverein Lüchingen

Kontext für Claude Code. Diese Datei beschreibt das Projekt, die Inhalte der
bestehenden Website und die bereits getroffenen Entscheidungen.

---

## 1. Projekt

Redesign der Website der **Vereinigung Pro Burg Neu-Altstätten** (Burgverein
Lüchinga), erreichbar unter `burgverein.ch`.

Die bestehende Seite läuft auf **Jimdo Creator**. Sie wird durch einen
Neuaufbau ersetzt. Ein technischer Import ist nicht vorgesehen — die
Inhaltsmenge ist klein genug, dass alle Texte in diesem Dokument stehen.

**Zweck des Vereins:** Erhaltung der Burg Neu-Altstätten durch finanzielle und
administrative Mithilfe. Non-Profit, keine kommerziellen Ziele. Sämtliche
Mittel fliessen in den Unterhalt der Burg.

**Wichtigste Funktion der Website:** ein Anmeldeformular für neue Mitglieder,
das die Eingaben per E-Mail an den Verein sendet. Alles andere ist
nachrangig.

---

## 2. Technischer Stand

> **Zwischenstand:** Der aktuelle Aufbau ist reines, handgeschriebenes HTML —
> eine einzige [`index.html`](index.html) mit Hash-Routing zwischen den
> Seiten, ohne Build-Schritt, deploybar direkt über GitHub Pages (siehe
> Abschnitt 11). Ob das so bleibt oder später auf Astro/Eleventy/ein
> Redaktions-Tool umgestellt wird, ist noch nicht endgültig entschieden — die
> Struktur unten bleibt bewusst stackneutral formuliert.

**Rahmenbedingungen:**

- Statische Seite, Deployment voraussichtlich Netlify oder GitHub Pages
- Sieben Inhaltsseiten, ohne separate Impressum-/Datenschutz-Seite
  (siehe Abschnitt 4)
- Gepflegt von Vorstandsmitgliedern im Milizsystem, nicht von Entwicklern.
  Wartungsarmut geht vor Raffinesse. Keine Build-Ketten, die in zwei Jahren
  niemand mehr zum Laufen bringt.
- Vorstände wechseln. Wenn ein Redaktions-Tool dazukommt (z. B. Decap CMS),
  muss die Bedienung ohne Git-Kenntnisse möglich sein.

---

## 3. Sprache und Schreibweise

- **Deutsch, Schweizer Rechtschreibung.** Kein «ß», immer «ss».
- **Beträge:** `CHF 40.–` oder `CHF 153'000.–`. Tausendertrennzeichen ist der
  Apostroph `'`.
  ⚠️ Die alte Seite verwendet durchgehend fälschlich den Backtick
  (`153\`000.- Sfr.`). Beim Übertragen korrigieren.
- **Währung:** «CHF», nicht «Sfr.» wie auf der alten Seite.
- **Ton:** freundlich, ein bisschen augenzwinkernd. Der bestehende Auftritt
  lebt davon («Wir Mitglieder des Burgvereins sind also eine Art moderne
  Ritter!»). Diesen Charakter beim Umschreiben erhalten — nicht in
  Behördendeutsch glätten.
- **Claim der Seite:** «Damit die Burg auch in 500 Jahren noch so gut
  aussieht.»
- **Leitspruch / H1 der Startseite:** «Alter schützt vor Liebe nicht, aber
  Liebe vor dem Altern.»

---

## 4. Seitenstruktur

Bestehende Navigation, in dieser Reihenfolge:

| Seite | Alte URL | Status |
|---|---|---|
| Home | `/` | übernehmen |
| Mitglied werden | `/mitglied-werden/` | übernehmen, wichtigste Seite |
| Projekte vom Verein | `/projekte-vom-verein/` | übernehmen, inhaltlich stärkste Seite |
| Wer wir sind – Ziele | `/wer-wir-sind-ziele/` | übernehmen |
| Geschichte der Burg | `/geschichte-der-burg/` | übernehmen |
| Impressionen | `/impressionen/` | übernehmen |
| Kontakt | `/kontakt/` | übernehmen |

> **Entscheid:** Impressum (`/about/`) und Datenschutz (`/j/privacy`) sind im
> Neuaufbau bewusst **nicht** übernommen — auf Wunsch entfernt. Die alte
> Impressum-Seite war ohnehin inhaltlich leer (nur Jimdo-Boilerplate), die
> Datenschutzerklärung war Jimdo-generiert und nicht übertragbar.
>
> ⚠️ Zu bedenken, falls das nochmals aufkommt: Das Anmeldeformular auf
> «Mitglied werden» erhebt weiterhin Name, Adresse und E-Mail-Adresse. Für
> eine Schweizer Vereinswebsite, die aktiv Personendaten sammelt, ist eine
> Datenschutzerklärung fachlich üblich, auch ohne dass eine feste Impressumspflicht
> im gleichen Mass wie bei kommerziellen Anbietern besteht. Das ist eine
> bewusste Entscheidung des Vorstands, keine versehentliche Lücke.

**Redirects:** Wenn URLs sich ändern, 301 einrichten. Alte Pfade wie
`/about/` oder `/j/privacy` haben im Neuaufbau kein Ziel mehr und sollten auf
die Startseite umgeleitet werden, sobald die Domain umgestellt wird.

**Meta-Beschreibungen:** Auf der alten Seite sind sie durchgehend leer, Jimdo
nimmt ersatzweise den ersten Absatz. Das führt bei «Wer wir sind» zu einem
absurd langen Google-Snippet. Beim Neuaufbau **für jede Seite eine eigene
Description schreiben**, ca. 120–155 Zeichen.

---

## 5. Inhalte

Die folgenden Texte sind wörtlich von der bestehenden Seite übernommen.
Sprachlich überarbeiten ist erwünscht (die Vorlage hat viele
Ein-Satz-Absätze, die zusammengezogen gehören), inhaltlich nichts erfinden.

### 5.1 Home

H1: «Alter schützt vor Liebe nicht, aber Liebe vor dem Altern.»

> Wir lieben unsere Burg, darum schützen wir sie, auch vor dem Altern!
> Willkommen beim Burgverein Lüchinga.

Call-to-Action: «Ich möchte auch Mitglied werden» → `/mitglied-werden/`

Terminhinweis (aktuell auf der Seite):

> Vormerken: nächste Burgversammlung, Freitag 13. August 2027, 19.30 Uhr,
> Torkel auf der Burg

⚠️ Dieser Termin wird jährlich aktualisiert. Die Regel lautet: **jeweils
2. Freitag im August**. Im neuen Aufbau so umsetzen, dass ein Vorstandsmitglied
das Datum an genau einer Stelle ändern kann.

### 5.2 Mitglied werden

Formularfelder (bestehend):

- Vorname
- Name
- Strasse/Nr.
- PLZ/Ort
- E-Mail
- Mitgliedschaft (Auswahl: Einzelmitglied / Familie / Unternehmen-Verein)

Pflichtfelder waren mit `*` gekennzeichnet. Datenschutzerklärung ist verlinkt.

**Beiträge:**

| Mitgliedschaft | Jahresbeitrag |
|---|---|
| Einzelmitglied | CHF 40.– |
| Familie | CHF 70.– |
| Unternehmen / Verein | CHF 100.– |

Begleittext:

> Die Einladung mit Einzahlungsschein erfolgt per Post nach Anmeldung.
>
> Die Mitglieder bezahlen einen Jahresbeitrag von CHF 40.– bis 70.–. Darin
> enthalten ist ein Gutschein für eine 75cl-Flasche Burgwein, welcher
> ausschliesslich an der Jahresversammlung eingelöst werden kann.
>
> Diese findet alljährlich am 2. Freitag im August im Torkel der Burg statt
> und setzt die Tradition des Burgfestes im kleinen Rahmen fort. Gemütlich,
> gesellig und unserer Burg zuliebe. Neumitglieder sind herzlich willkommen.

⚠️ Kleine Inkonsistenz in der Vorlage: Der Gutschein-Satz nennt nur «40.– bis
70.–» und lässt die Firmenmitgliedschaft aus. Beim Umschreiben klären, ob
Firmen ebenfalls einen Gutschein erhalten.

### 5.3 Projekte vom Verein

Einleitung:

> Von 1976 bis jetzt hat die Vereinigung Pro Burg über CHF 153'000.–
> zusammengebracht und damit den Unterhalt des grossartigen Bauwerks aus der
> Ritterzeit unterstützt. Wir Mitglieder des Burgvereins sind also eine Art
> moderne Ritter!

| Jahr | Projekt | Betrag |
|---|---|---|
| 2024 | Wiederherstellung des Erkers zur Sanierung des Badezimmers | CHF 15'000.– |
| 2016 | Aussenbeleuchtung, neue LED-Beleuchtung | CHF 6'000.– |
| 2014 | Mauersanierung | CHF 25'000.– |
| 2011 | Mauer bei Torkel | CHF 11'000.– |
| 2007 | Heizung | CHF 10'000.– |
| 1996 | Umbau Torkel | CHF 13'000.– |
| 1993 | Umfassungsmauer | CHF 16'000.– |
| 1985 | Renovation Burg | CHF 60'000.– |
| 1976 | Beleuchtung | CHF 12'000.– |

Summe der gelisteten Posten: CHF 168'000.–. Die Einleitung spricht von «über
CHF 153'000.–» — vermutlich ein nicht nachgeführter Wert aus der Zeit vor
2024. **Vor Veröffentlichung mit dem Kassier abgleichen.**

**Gestaltungshinweis:** Diese Seite ist inhaltlich das Stärkste, was der
Verein hat — fast fünfzig Jahre nachvollziehbare Arbeit. Auf der alten Seite
steht sie als schlichte Bilderreihe da. Als Zeitstrahl oder Tabelle mit
Bildern käme sie deutlich besser zur Geltung. Jeder Eintrag hat ein Foto
(siehe Abschnitt 6).

### 5.4 Wer wir sind – Ziele

> Im Jahre 1975 wurde es in Lüchingen (wieder mal) laut und fröhlich: Die Burg
> feierte Geburtstag und wurde 600 Jahre alt! Die Besucher des Festes feierten
> über drei Tage durch und fühlten sich bald ähnlich alt wie die Burg selber.
>
> Das Resultat dieser Party war ein unheimlich stolzer Reingewinn! Aus diesem
> Geld wurde die erste Aussenbeleuchtung der Burg erstellt. Der immer noch
> immense Restbetrag wurde als Beitrag an die Erhaltung der Burg geleistet.
>
> Damit wurde das **Bewusstsein geweckt**, dass die Erhaltung eines Denkmals
> nicht einfach der Besitzerfamilie zugemutet werden kann.
>
> So wurde am 8. Mai 1976 die Vereinigung «Pro Burg Neu-Altstätten» gegründet,
> mit dem primären Ziel, die **Erhaltung der Burg und deren Bewohnbarkeit
> durch finanzielle und administrative Mithilfe zu sichern**.
>
> Der runde Geburtstag unserer Burg Neu-Altstätten wurde also zur
> Geburtsstunde des Burgvereins.

**Aktueller Vorstand:**

| Funktion | Name |
|---|---|
| Präsident | Mario Sonderegger |
| Kassier | Philippe Langenegger |
| Aktuar | Stefan Eugster |
| Beisitzer | Bruno Baumgartner |
| Burgherr | Josef Enk |
| (Funktion nicht angegeben) | Monika Enk |

⚠️ Bei Monika Enk fehlt auf der alten Seite die Funktionsbezeichnung.
Nachfragen und ergänzen.

Alle Vorstandsmitglieder haben ein Porträtfoto (siehe Abschnitt 6).

### 5.5 Geschichte der Burg

> Unter unseren Burg-Fans gibt es auch geschichtlich Interessierte. Darum hier
> eine ultrakurze Version der letzten rund 650 Jahre.
>
> In Altstätten standen einstmals vier Burgen. Während drei davon seit
> Jahrhunderten in Trümmern liegen, ist «Neu Altstätten» erhalten geblieben und
> wird heute noch bewohnt.
>
> Die Burg wurde in den Jahren 1370–1375 von drei Edlen von Altstätten erbaut.
> Namentlich waren dies Vater, Sohn und Enkel Eglolf.
>
> Im Jahre 1402 findet man den Ritter Rudolf als Besitzer der Burg. Er war der
> letzte aus der Linie Meier von Altstätten. Nach seinem Tode kam die Burg in
> die Hände seiner Tochter Kunigunde.
>
> Als Erbauerin eines Hauses an der westlichen Ringmauer des Städtchens, das
> nach ihr der «gnädigen Frowen Hof» (Frauenhof) genannt wurde, ging sie in die
> Altstätter Geschichte ein.
>
> Als sie 1476 starb, kam der Besitz als Heiratsgut in die Hand ihres
> Schwiegersohnes Sigmund von Freiberg.
>
> In den Jahren 1566/70 waltete Graf Gabriel von Hohenems, der mit Helena von
> Freiberg verheiratet war, als Burgherr. Ihm folgten die Edlen von Schönau im
> Schwarzwald.
>
> 1639 verkaufte Hans Kaspar seinen gesamten Altstätter Besitz, darunter auch
> die Burg, mit Bewilligung des Abtes von St. Gallen, an elf Bürger von
> Altstätten. Einer war der Stadtschreiber Gilg Enk.
>
> Diese Bürger teilten den Altstätter Besitz auf und Enk übernahm die Burg mit
> den umliegenden Wiesen und Äckern. In der Folge vererbte sich die Burg bis
> auf den heutigen Tag innerhalb der Familie Enk. Sie steht heute in der
> 12. Generation im Eigentum von Josef Enk.

### 5.6 Impressionen

Reine Bildergalerie, kein Fliesstext. Auf der alten Seite 31 Fotos rund um
die Burg, ohne Bildunterschriften. Alle 31 sind heruntergeladen, siehe
Abschnitt 6, und in [`index.html`](index.html) bereits eingebunden.

### 5.7 Kontakt

Auf der alten Seite besteht die Kontaktseite aus drei Teilen: einem
Kontaktformular (Name, E-Mail, Nachricht), der E-Mail-Adresse
**info@burgverein.ch** und einer Standort-Karte (Google Maps), zentriert auf
«Burg Neu-Altstätten, Burgfeld, Lüchingen, Schweiz».

Im neuen Aufbau bewusst **ohne eigenes Kontaktformular** — E-Mail-Adresse und
Standort genügen. Wer schreiben will, tut das direkt per E-Mail; ein
zusätzliches Formular auf derselben Seite wie das Anmeldeformular wäre
redundant gewesen.

Die Postadresse der Burg ist vom Vorstand nachgeliefert und im Neuaufbau unter
«Standort» als Adressblock eingetragen:

> Burg Neu-Altstätten
> Burgfeld 2
> 9450 Lüchingen

Eine eigene Telefonnummer ist nach wie vor nirgends hinterlegt — vermutlich
bewusst, da die Korrespondenz über den Kassier läuft (siehe Abschnitt 8).
Falls das nicht stimmt, bitte melden.

⚠️ Die eingebettete Google-Maps-Karte der alten Seite nutzt einen API-Schlüssel,
der zum Jimdo-Konto gehört und sich nicht übernehmen lässt. Im Entwurf ist der
Standort deshalb nur als Text plus Link zu Google Maps gelöst. Für eine echte
Karteneinbettung braucht es einen eigenen Schlüssel im Google-Cloud-Konto des
Vereins.

---

## 6. Bilder

> **Erledigt:** Alle 49 Bilder unten sind heruntergeladen und liegen in
> Originalauflösung unter [`bilder/`](bilder/) — Logo, Hintergrundbild,
> Geschichte, 6× Vorstand, 9× Projekte, 31× Impressionen. Die Jimdo-Quell-URLs
> bleiben unten dokumentiert, sind aber ab Abschaltung der alten Seite
> wertlos; massgeblich ist ab jetzt der Ordner im Repo.

Alle Bilder lagen auf Jimdos CDN (`image.jimcdn.com`) und mussten **einmalig
heruntergeladen und ins Repository übernommen** werden, bevor die alte Seite
abgeschaltet wird. Danach sind die Quell-URLs wertlos.

Die URLs enthalten Transformationsparameter (`dimension=370x1024:format=jpg`).
Für die Originalauflösung `transf/none/` statt `transf/dimension=…/` einsetzen.

**Vereinslogo**
`https://image.jimcdn.com/app/cms/image/transf/none/path/s4e9a2fd3ee5d78b9/image/i7c488228ee697ba9/version/1526791918/image.png`

**Hintergrund- / Open-Graph-Bild (2000×1500)**
`https://image.jimcdn.com/app/cms/image/transf/none/path/s4e9a2fd3ee5d78b9/backgroundarea/i22f8af0d1e2ba8ad/version/1629723787/image.jpg`

**Geschichte der Burg**
`.../image/ic2a84db2bcb86593/version/1523599825/image.jpg`

**Vorstand** (Basis-Pfad `path/s4e9a2fd3ee5d78b9/image/`)

| Person | Bild-ID / Version |
|---|---|
| Mario Sonderegger | `ia9c4c3ddefa8f09d/version/1526731646` |
| Philippe Langenegger | `id0b7706a2f67e239/version/1756928972` (PNG) |
| Stefan Eugster | `i8fec6e6d468dedee/version/1526730222` |
| Bruno Baumgartner | `i9980157e08d1f74c/version/1526730513` |
| Josef Enk | `i3c06f506a31320e7/version/1526730259` |
| Monika Enk | `i563e2fe34367fbaa/version/1526731936` |

**Projekte** (gleicher Basis-Pfad)

| Jahr | Bild-ID / Version |
|---|---|
| 2024 | `i28e2e6a1ff8b8bb0/version/1757440685` |
| 2016 | `i98d69749d684c9f4/version/1756927982` |
| 2014 | `i65f97fed8d9f5936/version/1526405860` |
| 2011 | `i3044b1087d7584e5/version/1524633640` |
| 2007 | `i389ff56c79142a1c/version/1526405894` |
| 1996 | `i5ad83a57a49abb43/version/1526405919` |
| 1993 | `ifc034d6a75d2faa6/version/1526405952` |
| 1985 | `id53dbdd4b94fdf8f/version/1526405990` |
| 1976 | `i1f90be61162a4296/version/1526406103` |

Vollständige URL nach dem Muster:
`https://image.jimcdn.com/app/cms/image/transf/none/path/s4e9a2fd3ee5d78b9/image/<BILD-ID>/version/<VERSION>/image.jpg`

**Impressionen** (31 Bilder, gleicher Basis-Pfad, alle `version/1526405525`,
Dateien liegen als `bilder/impressionen/01.jpg` bis `31.jpg`, in
dieser Reihenfolge von der alten Seite übernommen):

`idc74fe15cbba40ce`, `ib1ea2d1ef8e4944f`, `i1182fe833ad37f00`,
`ie1dad2fafcba583a`, `ib85948b1f052ce6c`, `i9f8827848a83c0e0`,
`i119d0a309aef6c8a`, `ie9a5659a124df4f0`, `i2b465d00fc1cbaca`,
`id0338f1b7c4e92f5`, `if46767b82eda0d16`, `i1a459467fb5789fe`,
`i949cb8ab16b773cc`, `i357d7d9ea5beeafc`, `i452272c8743798a2`,
`i66d377667998f765`, `ieabe61873007133f`, `ia32eee6710545107`,
`i1fd2b0a331cd08b7`, `i417769ba7dd618ff`, `ib6ecebc8295cbd7e`,
`id9aeb9c010396714`, `iaad9f3b1f7bea67f`, `i9013256424c747f4`,
`i53ac9465d9a1505e`, `i15bbf49a317e0b0b`, `ib27063e1ace4a951`,
`i3961a5fc70e8927a`, `id8fd75650ebf7105`, `i2ed8aeb8b89dff07`,
`i5e9cd715dff6f96f`

---

## 7. Anmeldeformular

Die Kernfunktion der Website. Anforderung: **Formulareingaben gehen per E-Mail
an eine Vereinsadresse.** Zusätzlich, seit dieser Entwurfsrunde: Mitglieder
können den Jahresbeitrag optional direkt im Anschluss online bezahlen, per
Payrexx-Paylink (siehe Abschnitt 8 — nicht mehr «später», sondern Teil des
ersten Wurfs).

Auf einer statischen Seite braucht es für den E-Mail-Versand einen externen
Dienst, weil kein Server zur Verfügung steht. Netlify Forms ist naheliegend,
wenn dort deployed wird; sonst ein Dienst wie Formspree oder Tally.

**Datenschutz:** Es werden Name, Adresse und E-Mail erhoben. Schweizer DSG.
Der Formular-Dienst sollte in der Schweiz oder der EU hosten. Wer online
bezahlt, wird zusätzlich an Payrexx weitergeleitet. Eine eigene
Datenschutzseite gibt es auf Wunsch aktuell nicht (siehe Abschnitt 4) — das
Einverständnis wird nur noch über die Checkbox im Formular eingeholt, ohne
Verlinkung auf einen Erklärungstext.

**Spamschutz:** Honeypot-Feld reicht für einen Verein dieser Grösse. Kein
Captcha, das schreckt ältere Mitglieder ab.

---

## 8. Zahlungen — jetzt Teil der Anmeldung

> Ursprünglich als späterer Ausbau vorgesehen (siehe Versionsgeschichte);
> seit dieser Entwurfsrunde direkt in die Anmeldeseite integriert.

Mitglieder können den Jahresbeitrag bei der Anmeldung optional sofort online
bezahlen, per Karte oder TWINT, über einen Payrexx-Paylink. **Bewusst
entkoppelt von der übrigen Website** — der Paylink ist nur ein verlinkter
Button, keine Integration in den Code. Das lässt den Stack weiterhin frei
wählbar.

**Ist-Zustand parallel dazu:** Nach der Anmeldung verschickt der Kassier wie
bisher eine QR-Rechnung per Post. Wer nicht online bezahlen möchte, wartet
einfach darauf. «Auf Rechnung» ist damit weiterhin abgedeckt.

**Umsetzung:** Payrexx (Thun) ist bei Schweizer Vereinen verbreitet. Pro
Mitgliedschaftsstufe (Einzelmitglied CHF 40.–, Familie CHF 70.–, Unternehmen/
Verein CHF 100.–) braucht es im Payrexx-Konto einen eigenen Paylink — eine
vorbefüllte Zahlseite mit fixem Betrag —, dessen URL als Button auf der
Anmeldeseite (und optional in der Bestätigungsmail) verlinkt wird. Der
Free-Plan hat keine monatlichen Fixkosten, gemeinnützige Organisationen
erhalten 50 % Rabatt auf die kostenpflichtigen Abos.

TWINT ist in der Schweiz wichtiger als die Kreditkarte. Gebühren im Free-Plan
rund 1.30 % + CHF 0.30 (TWINT) bzw. 2.50 % + CHF 0.30 (Visa/Mastercard) — bei
CHF 40 Jahresbeitrag also etwa 80 Rappen bzw. CHF 1.30 pro Mitglied.

In [`index.html`](index.html) ist der Bereich «Beitrag direkt online
bezahlen» auf der Seite «Mitglied werden» als deaktivierte «Bald verfügbar»-
Buttons angelegt, ohne Ziel-URL, damit auf der veröffentlichten Seite nichts
kaputt oder wie ein Platzhalter wirkt. Sobald die drei Paylinks im
Payrexx-Konto erstellt sind: im Quellcode den Kommentar direkt über dem
`pay-grid`-Block suchen und die drei `<span class="btn ...">` durch
`<a class="btn btn-ghost btn-block" href="[Paylink-URL]">Bezahlen mit
Payrexx</a>` ersetzen.

---

## 9. Offene Punkte

> ⚠️ **Vor dem Umbiegen von `burgverein.ch` auf diese Seite:** Es gibt aktuell
> keine Impressum- oder Datenschutzseite (bewusster Entscheid, siehe
> Abschnitt 4). Das Anmeldeformular sammelt aber weiterhin Personendaten —
> falls das für den Live-Betrieb nochmals überdacht werden soll, hier
> nachfragen. Bis zur Domain-Umstellung eignet sich die `github.io`-Adresse
> für Vorschau und Vorstandsreview.

- [ ] Technischer Stack endgültig festlegen (Abschnitt 2) — aktuell reines
      HTML, funktioniert bereits per GitHub Pages
- [x] Inhalte «Kontakt» und «Impressionen» erfassen (Abschnitt 5.6/5.7)
- [ ] Gesamtsumme der Projekte mit dem Kassier abgleichen (153'000 vs. 168'000)
- [ ] Funktion von Monika Enk im Vorstand klären (aktuell nur «Vorstand»
      ausgewiesen, ohne Detail-Funktion)
- [ ] Gutschein-Regelung für Firmenmitglieder klären
- [x] Bilder von Jimdo herunterladen, bevor die alte Seite abgeschaltet wird
      (Abschnitt 6, `bilder/`)
- [ ] Meta-Beschreibungen für alle Seiten schreiben (aktuell nur eine
      generische Beschreibung für die ganze Seite, da Hash-Routing)
- [ ] Entscheiden, ob ein Redaktions-Tool (z. B. Decap CMS) dazukommt
- [ ] Drei Payrexx-Paylinks erstellen (Einzelmitglied/Familie/Unternehmen)
      und in `index.html` verlinken (Abschnitt 8)
- [ ] Eigenen Google-Maps-API-Schlüssel besorgen, falls die Kontakt-Seite
      eine eingebettete Karte statt nur einen Link erhalten soll
- [ ] Custom Domain (`burgverein.ch`) auf GitHub Pages einrichten, sobald
      obige Punkte erledigt sind (Abschnitt 11)

---

## 10. Arbeitsweise

- Vor grösseren Umbauten kurz den Plan skizzieren, nicht sofort drauflos.
- Keine Inhalte erfinden. Wo Angaben fehlen, `TODO` setzen und nachfragen.
- Beim Umschreiben der Texte den augenzwinkernden Ton behalten.
- Barrierefreiheit mitdenken: Die Zielgruppe ist im Schnitt älter.
  Ausreichende Schriftgrössen, guter Kontrast, `alt`-Texte auf allen Bildern.
- Diese Datei aktuell halten. Wenn eine offene Frage geklärt wird, hier
  nachführen — nicht nur im Code.

---

## 11. Website und GitHub Pages

Die Website liegt als eine einzige, navigierbare [`index.html`](index.html)
im Repo-Root, mit Hash-Routing zwischen den Seiten (`#/mitglied-werden` usw.)
und allen Bildern unter [`bilder/`](bilder/). Kein Build-Schritt nötig — die
Datei lässt sich direkt im Browser öffnen und genauso direkt über GitHub
Pages ausliefern, weil Hash-Routing ohne Server-Konfiguration funktioniert.

**Veröffentlichen:** Im Repo unter *Settings → Pages* als Quelle *Deploy from
a branch*, Branch `main`, Ordner `/ (root)` wählen. GitHub liefert danach
unter `https://<benutzername>.github.io/<repo-name>/` aus. Für die eigene
Domain `burgverein.ch` zusätzlich eine `CNAME`-Datei mit dem Domainnamen ins
Repo-Root legen und beim Domain-Provider einen `CNAME`-Eintrag auf
`<benutzername>.github.io` setzen (siehe GitHub-Doku zu *Custom domains*) —
das ist bewusst noch nicht eingerichtet, da es die aktuelle Jimdo-Seite unter
derselben Domain ablösen würde. Erst umstellen, wenn die Punkte in
Abschnitt 9 erledigt sind.

Die Seite deckt alle sieben Seiten aus Abschnitt 4 ab, inklusive automatisch
berechnetem Versammlungsdatum (Abschnitt 5.1), allen 49 Bildern aus
Abschnitt 6 und einem vorbereiteten, aber noch deaktivierten Bereich für die
Payrexx-Online-Zahlung (Abschnitt 8). Interne Arbeitsnotizen («Für den
Vorstand») sind nicht mehr auf der Seite selbst, sondern ausschliesslich hier
in dieser Datei festgehalten (Abschnitt 9) — die Seite zeigt nur noch
Inhalte, die auch wirklich für Besucherinnen und Besucher bestimmt sind.
