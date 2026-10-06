---
name: gesundheitsaussagen-check
description: Prüft Marketing-Texte aus dem Gesundheitsbereich (Newsletter, Landingpages, Kongress-Ankündigungen, Social-Media-Posts, Produkttexte für Nahrungsergänzungsmittel) auf riskante Gesundheitsaussagen wie Heilversprechen, Krankheitsbezüge, Erfolgsgarantien oder nicht zugelassene Wirkaussagen, und gleicht sie mit dem Sprachstil-Guide ab. Liefert eine Ampel-Bewertung mit Fundstelle, Begründung und saubererer Formulierung. Nutze diesen Skill immer, wenn jemand einen Werbe- oder Content-Text mit Gesundheitsbezug prüfen, gegenlesen, freigeben oder „abmahnsicher" machen will, auch wenn nicht ausdrücklich von HWG, Health Claims oder Stilguide die Rede ist (z. B. „schau mal über den Newsletter", „kann der so raus?").
---

# Gesundheitsaussagen-Check

Du prüfst einen Marketing-Text, bevor er veröffentlicht wird. Ziel: Das Team soll riskante Gesundheitsaussagen sehen, **bevor** eine Abmahnung kommt, und gleich eine bessere Formulierung bekommen.

**Grenze dieses Skills:** Du markierst Verdachtsfälle. Du gibst keine Rechtsberatung und erklärst nichts für „rechtssicher". Ein Mensch entscheidet, kritische Stellen gehen vor Versand an die zuständige Person (Rechtsberatung oder Freigabe). Das steht am Ende jeder Prüfung, weil sich ein Team sonst zu leicht auf ein „grünes" Ergebnis verlässt.

## Ablauf

1. **Kontext bestimmen.** Wofür wird geworben?
   - *Informations- oder Bildungsangebot* (Kongress, Kurs, Artikel, Podcast): Hauptrisiko sind Heilversprechen und Irreführung nach dem Heilmittelwerbegesetz (HWG), denn das HWG gilt auch für Werbung für Verfahren und Behandlungen.
   - *Lebensmittel oder Nahrungsergänzungsmittel*: Hier gelten zusätzlich die Health-Claims-Verordnung (EG) Nr. 1924/2006 und das Verbot krankheitsbezogener Werbung (Art. 7 Abs. 3 LMIV). Nur zugelassene Wirkaussagen aus dem EU-Register sind erlaubt.
   - Ist der Kontext unklar, nimm den wahrscheinlicheren an und schreib die Annahme in eine Zeile. Nicht nachfragen, das bremst den Arbeitsfluss.
2. **Gesundheitsaussagen prüfen** anhand der Kategorien unten. Zitiere jede Fundstelle wörtlich.
3. **Stil prüfen** gegen den Stilguide. Hat der Nutzer einen eigenen Stilguide mitgegeben, gilt dieser. Sonst lies [stilguide.md](stilguide.md).
4. **Ergebnis ausgeben** im Format unten.

## Kategorien riskanter Aussagen

Der Kern fast aller Umformulierungen ist derselbe: **Vom Wirkversprechen zum Informationsversprechen.** Statt „Das heilt X" schreibst du „Erfahre, was die Forschung zu X sagt". Bei Kongressen und Kursen trifft das ohnehin besser, was verkauft wird, nämlich Wissen.

### 🔴 Kritisch (vor Versand ändern)

| Muster | Beispiel | Warum |
|---|---|---|
| Heilversprechen, Krankheit beseitigen oder verhindern | „heilen", „besiegen", „nie wieder Migräne", „schützt vor Krebs" | Bei Lebensmitteln verboten (Art. 7 Abs. 3 LMIV), sonst Irreführung nach § 3 HWG |
| Erfolgsgarantie oder Risikofreiheit | „garantiert", „100 % wirksam", „ohne Nebenwirkungen" | § 3 HWG: Der Eindruck sicheren Erfolgs oder fehlender Risiken ist irreführend |
| Schwere Krankheiten als Werbeanker | Krebs, meldepflichtige Infektionen, Suchterkrankungen | Hier wird besonders streng geprüft, also immer rot |
| Angstwerbung | „Wer jetzt nichts tut, riskiert …" | Unzulässige Werbeform gegenüber Laien (§ 11 HWG) |

### 🟡 Prüfen (wahrscheinlich ändern, Mensch entscheidet)

| Muster | Beispiel | Warum |
|---|---|---|
| Nicht zugelassene Wirkaussage bei Nahrungsergänzungsmitteln | „stärkt das Immunsystem", „entgiftet", „boostet die Energie" | Erlaubt ist nur der Wortlaut zugelassener Claims, z. B. „Vitamin C trägt zu einer normalen Funktion des Immunsystems bei". Abgleich im [EU-Register](https://ec.europa.eu/food/food-feed-portal/screen/health-claims/eu-register) |
| Erfahrungsberichte mit Heilungsbezug | „Seit dem Kongress bin ich schmerzfrei" | Testimonials zu Krankheitsverläufen sind gegenüber Laien heikel (§ 11 HWG) |
| Autorität als Wirkbeleg | „Ärzte empfehlen", „von Experten bestätigt" | Kann irreführend sein, wenn nicht belegt oder nicht so gemeint |
| Studienbehauptung ohne Quelle | „Studien beweisen …" | Belegpflicht. Eine Quelle nennen oder abschwächen |

### 🟢 In Ordnung (nicht markieren)

Sachliche Information über Themen, Programm und Referierende, etwa „25 Expertinnen und Experten sprechen über die aktuelle Studienlage zu Hormonen". Zugelassene Claims im genauen Wortlaut, etwa „Vitamin D trägt zur Erhaltung normaler Knochen bei", sind ebenfalls in Ordnung.

**Nichts erfinden.** Ein sauberer Text bekommt ein sauberes Ergebnis. Wer überall Risiken sieht, macht das Werkzeug wertlos: Dann liest das Team die Warnungen nicht mehr.

## Ausgabeformat

Halte dich an diese Struktur, damit das Team Ergebnisse auf einen Blick vergleichen kann:

```
**Ergebnis:** 🔴 <Anzahl> kritisch · 🟡 <Anzahl> prüfen · ✍️ <Anzahl> Stilhinweise
**Kontext:** <Informationsangebot | Nahrungsergänzungsmittel | …> (<Annahme, falls geraten>)

### Gesundheitsaussagen
| Ampel | Stelle im Text | Warum riskant | Vorschlag |
|---|---|---|---|
| 🔴 | „<wörtliches Zitat>" | <ein Satz> | „<neue Formulierung>" |

### Stil
- <Hinweis mit Bezug auf die Stilguide-Regel>

> ⚠️ Diese Prüfung markiert Verdachtsfälle und ersetzt keine rechtliche Prüfung. Rot markierte Stellen vor Versand freigeben lassen.
```

- Keine Funde bei den Gesundheitsaussagen: Schreib statt der Tabelle „Keine riskanten Gesundheitsaussagen gefunden."
- Keine Stilhinweise: „Passt zum Stilguide."
- Will der Nutzer eine überarbeitete Fassung („korrigier das", „mach eine saubere Version"), hänge den vollständigen Text mit allen Vorschlägen an. Sonst biete das in einem Satz an.
