# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · [Español](README.es.md) · [Français](README.fr.md) · **Deutsch** · [Português (Brasil)](README.pt-BR.md)

Reader's Ear (`readers-ear`) ist ein [Agent Skill](https://agentskills.io), mit dem ein KI-Agent Texte in jeder Sprache und jedem Genre so lange überarbeitet, bis sie sich für die vorgesehenen Leser natürlich lesen.

## Warum

Die meisten „Humanizer“-Skills arbeiten mit Regeln: Listen von Wörtern und Mustern, die nach KI klingen. Das hat drei Nachteile:

- Die Regeln sind meist für eine einzige Sprache geschrieben und taugen in anderen nicht.
- Starre Regeln zwingen zu Entscheidungen, die für manche Zwecke falsch sind.
- Je besser die Modelle werden, desto mehr werden die Regeln zum begrenzenden Faktor.

Dieser Skill geht den umgekehrten Weg. Er setzt voraus, dass die KI bereits klug genug ist, um in jeder Sprache gute von schlechten Texten zu unterscheiden, und dass ihr keine Regeln fehlen, sondern eine Arbeitsweise. Deshalb enthält er nur Grundsätze, die in jeder Sprache gelten: den Text aus Sicht seiner Leser beurteilen, beim erneuten Lesen konkrete Probleme finden und dabei mit dem Aufbau beginnen, jedes Problem auf der passenden Ebene beheben (vom einzelnen Wort bis zum ganzen Text) und aufhören, wenn kein konkretes Problem mehr übrig ist. Alles andere ist Sache des Modells; ein besseres Modell liefert also bessere Ergebnisse.

## Was er tut

- **Standardüberarbeitung**: liest den Text noch einmal so, wie seine Leser ihn lesen würden, prüft dabei zuerst den Aufbau, dann die Sätze, und behebt die Probleme, die er konkret benennen kann. Liegt ein Problem im Aufbau, glättet er nicht einzelne Sätze, sondern listet auf, was der Text vermitteln muss, baut ihn von dieser Liste aus neu auf und stellt sicher, dass keine Tatsache und keine Aussage verloren gegangen ist. Er hört auf, wenn er kein Problem mehr benennen kann; ein Text, der schon gut ist, bleibt deshalb fast unverändert. Der Aufwand richtet sich nach Länge und Tragweite des Textes. Du bekommst den fertigen Text, dazu die Punkte, die er nur angemerkt statt behoben hat, und eine kurze Erklärung, falls er den Aufbau geändert hat.
- **Gründliche Überarbeitung** (nur auf Wunsch, weil sie weit mehr Zeit und Tokens kostet): Bevor sich der Agent ein eigenes Urteil über den Text bildet, arbeiten zwei neue KI-Instanzen parallel, die dein Gespräch nicht kennen, etwa Subagenten. Die eine sucht im Web nach Texten desselben Genres und Zwecks, ohne deinen Text zu sehen, und fasst zusammen, wie diese geschrieben sind. Die andere liest nur deinen Text und eine Notiz zu seinen Lesern und seinem Zweck und berichtet, wo sie stolpert. Danach sucht der Agent mit beiden Berichten vor Augen nach Problemen, prüft wichtige Formulierungen und Fakten, überarbeitet den Text und sagt dir, was er herangezogen hat und welche Schritte er nicht ausführen konnte. Als Referenz dienen nur Texte, die ursprünglich in der Sprache deines Textes verfasst sind und deren Wortlaut eine Person oder Organisation geprüft hat und verantwortet, etwa Wörterbücher, Korpora und Dokumente öffentlicher Einrichtungen und großer Unternehmen; bei Formulierungen bevorzugt der Agent Texte aus der Zeit vor der Verbreitung generativer KI. Übersetzungen nimmt er nie als Referenz, weil sie Muster ihrer Ausgangssprache mitbringen können.
- **Geltungsbereich**: Ungefragt überarbeitet er nur Texte, die der Agent für andere schreibt. Wo er die Einstellung speichern kann, fragt er dich einmal, ob er stattdessen alles abdecken soll, was der Agent schreibt, und speichert deine Antwort dort, wo künftige Sitzungen sie laden.

## Installation

Wähle die Methode danach, wo du den Skill nutzt.

| Wo du ihn nutzt | Empfohlene Methode |
|---|---|
| Claude Code auf deinem eigenen Rechner | [Plugin](#claude-code) aus diesem Repository |
| claude.ai, Claude Desktop, Cowork oder Claude Code im Web | [ZIP-Upload](#claudeai-claude-desktop-und-cowork) in dein claude.ai-Konto |
| Codex, Cursor, Gemini CLI, GitHub Copilot und andere Agenten | [`npx skills`](#andere-agenten) |

Wenn du sowohl claude.ai als auch Claude Code nutzt, deckt der ZIP-Upload beides ab, denn Claude Code lädt die Skills aus deinem claude.ai-Konto, wenn du dich damit anmeldest. Installiere dann nicht zusätzlich das Plugin, sonst lädt Claude Code ihn doppelt.

### Claude Code

Führe in einer Claude-Code-Sitzung aus:

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

Der erste Befehl fügt dieses Repository als Plugin-Marketplace hinzu; der zweite installiert das Plugin `readers-ear` aus dem gleichnamigen Marketplace. Ab Claude Code 2.1.275 erledigt ein einziger Befehl beides: `/plugin install readers-ear --marketplace motestream/readers-ear`.

- **Aktualisieren**: Führe `/plugin marketplace update readers-ear` aus, oder schalte unter **Marketplaces** in `/plugin` die automatische Aktualisierung für diesen Marketplace ein.
- **Mit einem Team teilen**: Führe im Repository deines Projekts `claude plugin marketplace add motestream/readers-ear --scope project` aus und committe die dabei angelegte `.claude/settings.json`. Sobald Teammitglieder in Claude Code bestätigen, dass sie dem Projektordner vertrauen, steht ihnen der Marketplace zur Verfügung, und sie können das Plugin daraus installieren.
- **Cloud-Sitzungen** (Claude Code im Web) laden keine Plugins, die du auf deinem eigenen Rechner installiert hast. Lade den Skill stattdessen auf claude.ai hoch (nächster Abschnitt), oder kopiere `plugin/skills/readers-ear/` in das Verzeichnis `.claude/skills/` deines Projekts und committe die Kopie.

### claude.ai, Claude Desktop und Cowork

Menüs und Schaltflächen sind hier so benannt wie in der englischen Oberfläche.

1. Stelle sicher, dass die Codeausführung eingeschaltet ist. In den Tarifen Free, Pro und Max findest du sie unter **Settings > Capabilities**; in den Tarifen Team und Enterprise schaltet ein Inhaber sie zusammen mit der Skills-Funktion unter **Organization settings > Plugins & skills** ein.
2. Lade dieses Repository herunter und packe den Ordner `plugin/skills/readers-ear` so in eine ZIP-Datei, dass sie `readers-ear/SKILL.md` enthält. Der Ordner muss weiterhin `readers-ear` heißen.
3. Öffne auf claude.ai **Customize > Skills**, klicke auf **+** und dann auf **Create skill** > **Upload a skill**, und wähle die ZIP-Datei aus.

Der Skill gehört dann zu deinem Konto, also nutzen ihn auch Claude Desktop und Cowork. Claude Code (2.1.273 oder neuer) lädt ihn ebenfalls, auch in Cloud-Sitzungen, wenn du dich mit demselben Konto anmeldest. Zum Aktualisieren löschst du unter **Customize > Skills** die alte Version und lädst die neue ZIP-Datei hoch. Inhaber von Team- und Enterprise-Organisationen können den Skill für alle Mitglieder bereitstellen.

### Andere Agenten

```
npx skills add motestream/readers-ear -g
```

`-g` installiert ihn für dein Benutzerkonto; ohne die Option landet er im aktuellen Projekt. Der Befehl erkennt deine Agenten und fragt, für welche er installieren soll; um einen anzugeben, ergänze `-a`, etwa `-a codex`. Aktualisiert wird mit `npx skills update`.

Mit GitHub CLI 2.90 oder neuer (`gh skill` ist noch in der Vorschau) kannst du stattdessen `gh skill install motestream/readers-ear readers-ear --scope user` ausführen. Der Befehl fragt, für welchen Agenten er installieren soll; du kannst ihn aber auch mit `--agent` angeben. Aktualisiert wird mit `gh skill update`.

Für eine Installation von Hand kopierst du `plugin/skills/readers-ear/` in das Skill-Verzeichnis deines Agenten, etwa `~/.claude/skills/` bei Claude Code.

## Verwendung

- Der Skill startet von selbst, wenn der Agent Texte für andere schreibt. Du kannst auch direkt um eine Überarbeitung bitten („lass das natürlicher klingen“) oder den Skill beim Namen aufrufen: `/readers-ear` oder, wenn er als Claude-Code-Plugin installiert ist, `/readers-ear:readers-ear`.
- Wenn du eine gründliche Überarbeitung möchtest, fordere sie ausdrücklich an („nimm dir Zeit und überarbeite das sorgfältig“).
- Bittest du den Agenten, deinen Text zu überarbeiten, kann er auch den Aufbau ändern, falls dort das Problem liegt. Willst du den Aufbau behalten und nur Details ändern lassen, sag das („korrigiere nur die Tippfehler“); dann weist er auf Probleme im Aufbau hin, statt sie zu beheben.
- Beim ersten Lauf an einem Ort, an dem er deine Antwort speichern kann, fragt er einmal, ob er alles, was der Agent schreibt, oder nur Texte für andere überarbeiten soll. Um den Geltungsbereich später zu ändern, sag es einfach. Änderst du den Geltungsbereich an einem Ort, an dem sich die Einstellung nicht speichern lässt, wendet der Skill sie nur im aktuellen Gespräch an und gibt dir einen Satz, den du in deine eigenen Anweisungen aufnehmen kannst, damit spätere Sitzungen ihn übernehmen.
- **Was er außerhalb des Gesprächs schreibt**: Nur wenn du den Geltungsbereich wählst oder änderst, speichert der Skill einen Satz in deinen persönlichen Anweisungen oder im Gedächtnis deines Kontos (etwa in deiner `CLAUDE.md` auf Nutzerebene) und sagt dir, wo. Ansonsten schreibt er nur in den Text, an dem du arbeitest.

## Übersetzungen

Der Agent lädt nur die englische [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md). Die Übersetzungen sind für menschliche Leser gedacht; weicht eine vom englischen Original ab, gilt das Original.

| Sprache | README | Skill-Anweisungen |
|---|---|---|
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## Ausprobieren

Bevor du dich auf den Skill verlässt, probiere ihn mit deinen eigenen Texten aus:

- Vergleiche bei demselben Modell die Ausgabe mit und ohne den Skill, am besten in mehreren Sprachen und in Genres mit festen Formulierungen, etwa geschäftlichen E-Mails, Vertragsklauseln und UI-Texten.
- Gib ihm einen Text, der schon gut ist. Er sollte ihn fast unverändert lassen.
- Gib ihm einen inhaltlich korrekten, aber schlecht aufgebauten Text, etwa einen Bericht mit einem Fazit irgendwo in der Mitte, und bitte um eine Überarbeitung. Er sollte den Aufbau ändern und alle Fakten beibehalten.
- Prüfe beim Programmieren, ob er die Commit-Nachrichten, PR-Beschreibungen und Dokumentation, die der Agent schreibt, glättet und vorhandene Texte anderer Personen unangetastet lässt.

## Mitwirken

- Wenn du `SKILL.md` oder die englische README-Datei änderst, aktualisiere im selben Commit die zugehörigen Übersetzungen, einschließlich des Datums am Anfang jeder Skill-Übersetzung.
- Teste Änderungen an `SKILL.md` in mindestens drei Sprachen, davon eine mit wenig Trainingsdaten, und mit jedem Modell, das du unterstützen willst. Prüfe außerdem, wie sich die Frage nach dem Geltungsbereich und das Speichern in einem nicht interaktiven Lauf (`claude -p`) und in einer Cloud-Sitzung verhalten.

## Lizenz

Veröffentlicht unter der [MIT-Lizenz](../LICENSE).
