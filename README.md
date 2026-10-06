# Content-Team-Skills für Claude Code

Ein **Skill** ist eine Arbeitsanleitung für Claude. Sie beschreibt eine wiederkehrende Aufgabe so genau, dass Claude sie jedes Mal gleich gut erledigt, egal wer im Team fragt. Du musst dafür nichts programmieren und keinen Befehl kennen. Du schreibst einfach wie immer, und Claude erkennt selbst, wann der Skill passt.

---

## Gesundheitsaussagen-Check

**Was macht er?**
Er liest deinen Newsletter, deine Landingpage oder deinen Social-Post und markiert Sätze, die eine Abmahnung riskieren könnten, zum Beispiel Heilversprechen („heilt Hashimoto"), Garantien („ohne Nebenwirkungen") oder nicht zugelassene Wirkaussagen bei Nahrungsergänzungsmitteln. Zu jeder Stelle bekommst du einen Formulierungsvorschlag. Außerdem prüft er den Text gegen euren Sprachstil-Guide.

**Wann nutzt du ihn?**
Vor jedem Versand und jeder Veröffentlichung. Schreib zum Beispiel:
- „Schau mal über den Newsletter, kann der so raus?" und füge den Text ein
- „Prüf die Landingpage für den Hormon-Kongress"
- „Mach mir eine saubere Version von diesem Produkttext"

**Was kommt raus?**

> **Ergebnis:** 🔴 2 kritisch · 🟡 1 prüfen · ✍️ 2 Stilhinweise
>
> | Ampel | Stelle im Text | Warum riskant | Vorschlag |
> |---|---|---|---|
> | 🔴 | „wie du Hashimoto endlich heilst" | Heilversprechen | „was die Forschung heute über Hashimoto weiß" |
> | 🔴 | „Garantiert ohne Nebenwirkungen" | Erfolgsgarantie | streichen |
> | 🟡 | „Ärzte empfehlen …" | unbelegte Autorität | konkrete Person mit Zitat nennen oder streichen |

- 🔴 **Kritisch:** vor Versand ändern
- 🟡 **Prüfen:** wahrscheinlich ändern, du entscheidest
- 🟢 **In Ordnung:** wird nicht extra aufgeführt

**Was er nicht kann:** Er ersetzt keine Rechtsprüfung. Er findet Verdachtsfälle, damit sie ein Mensch prüft. Rot markierte Stellen gehen vor Versand an die zuständige Person.

**Euren Stilguide einbauen:** Ersetzt den Inhalt von [`skills/gesundheitsaussagen-check/stilguide.md`](skills/gesundheitsaussagen-check/stilguide.md) durch euren Stilguide. Mehr ist nicht nötig.

---

## Installation (einmalig, ca. 2 Minuten)

In Claude Code eingeben:

```
/plugin marketplace add ahmetyg/content-team-skills
/plugin install content-team-skills@content-team-skills
```

Updates kommen mit `/plugin update content-team-skills`.

---

## Wie wir sicherstellen, dass der Skill gut bleibt

Sprachmodelle ändern sich, und Skills werden angepasst. Damit dabei nichts unbemerkt schlechter wird („Drift"), gibt es drei Sicherungen:

1. **Testfälle (Evals).** Im Ordner [`evals/`](evals/) liegen Texte mit absichtlich eingebauten Fehlern, deren richtiges Ergebnis bekannt ist. Dazu gehören ein fehlerfreier Text, der *nicht* markiert werden darf, und eine Anfrage, bei der der Skill gar nicht anspringen soll. Nach jeder Änderung läuft:
   ```
   claude plugin eval .
   ```
   Der Lauf vergleicht automatisch mit und ohne Skill und zeigt, ob alle Fälle noch bestehen.

   **So wird bewertet:** Jeder Testfall hat 2 bis 3 Prüfungen. Es gibt zwei Arten:
   - **Feste Textprüfungen**, zum Beispiel „Steht der Rechtshinweis drin?" oder „Meldet der Skill beim sauberen Text 0 kritische Funde?".
   - **Inhaltliche Prüfungen** durch ein zweites Modell (Claude Haiku) als Gutachter. Es prüft jede Antwort gegen eine Liste konkreter Punkte und stimmt dreimal ab. Die Mehrheit entscheidet.

   Ein Testfall gilt als bestanden, wenn in allen drei Durchläufen alle Prüfungen bestehen.

   **Letzter Lauf:** am 6. Oktober 2026 mit Version 0.1.0, Claude Code 2.1.291 und Claude Opus. Er dauerte 91 Sekunden und kostete 3,44 USD.

   | | mit Skill | ohne Skill |
   |---|---|---|
   | Inhalt: Probleme richtig erkannt (Gutachter) | 12 von 12 | 10 von 12 |
   | Ampel-Format und Rechtshinweis (feste Prüfung) | 21 von 21 | 0 von 21 |
   | Darf-nicht-anspringen-Fall | 3 von 3 | 3 von 3 |
   | **Gesamtquote** (Durchschnitt der Testfälle) | **100 %** | **44 %** |

   **Ehrlich gelesen:** Die 44 % kommen vor allem daher, dass Claude ohne Skill weder das Ampel-Format noch den Rechtshinweis liefert. Inhaltlich ist Claude auch ohne Skill gut. Der Skill macht die Ergebnisse vor allem einheitlich, vergleichbar und vorsichtig. Einen klaren inhaltlichen Unterschied gab es beim Kongress-Text: Ohne Skill hat Claude dort in 2 von 3 Durchläufen Punkte übersehen.
2. **Review.** Änderungen am Skill kommen als Pull Request. Eine zweite Person schaut drauf, bevor sie live gehen.
3. **Versionierung.** Jede Version hat eine Nummer ([`plugin.json`](.claude-plugin/plugin.json)) und einen Eintrag im [`CHANGELOG.md`](CHANGELOG.md). Geht etwas schief, lässt sich die vorige Version zurückholen.
