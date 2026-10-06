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

   **Letzter Lauf (6. Oktober 2026, Version 0.1.0):** 6 von 6 Testfällen bestanden, jeder Fall dreimal ausgeführt. Mit Skill liegt die Quote bei 100 %, ohne Skill bei 44 %. Ohne Skill findet Claude zwar oft die gleichen Probleme, liefert aber weder einheitliche Ampel-Bewertungen noch den Hinweis auf die Rechtsprüfung. Genau diese Einheitlichkeit braucht ein Team.
2. **Review.** Änderungen am Skill kommen als Pull Request. Eine zweite Person schaut drauf, bevor sie live gehen.
3. **Versionierung.** Jede Version hat eine Nummer ([`plugin.json`](.claude-plugin/plugin.json)) und einen Eintrag im [`CHANGELOG.md`](CHANGELOG.md). Geht etwas schief, lässt sich die vorige Version zurückholen.
