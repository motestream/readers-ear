# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · [Español](README.es.md) · [Français](README.fr.md) · **Deutsch** · [Português (Brasil)](README.pt-BR.md)

Reader's Ear ist ein [Agent Skill](https://agentskills.io), mit dem ein KI-Agent Texte in jeder Sprache und jedem Genre so schreibt und überarbeitet, dass sie sich für ihre Leser natürlich lesen. Statt Listen zu vermeidender Wörter gibt der Skill dem Agenten eine Arbeitsweise. Du kannst ihn in Claude (Claude Code, claude.ai, Claude Desktop und Cowork) und in anderen Agenten wie Codex, Cursor, Gemini CLI und GitHub Copilot installieren.

## Warum eine Methode statt Regeln?

Viele „Humanizer“-Skills arbeiten mit Regeln: Listen von Wörtern und Mustern, die nach KI klingen. Regeln haben Nachteile:

- Sie sind meist für eine einzige Sprache geschrieben und lassen sich nicht auf andere übertragen.
- Sie erzwingen Entscheidungen, die für manche Zwecke falsch sind, etwa das Verbot einer Formulierung, die ein Vertrag oder eine geschäftliche E-Mail braucht.
- Sie begrenzen die Ergebnisse: So sehr sich die Modelle auch verbessern, die Ausgabe kann nie besser sein als die Regeln.

Reader's Ear geht davon aus, dass das Modell in jeder Sprache bereits gute von schlechten Texten unterscheiden kann und dass ihm keine Regeln fehlen, sondern eine Arbeitsweise. Deshalb gibt der Skill nur eine Methode vor, die in jeder Sprache funktioniert, und überlässt das Urteil dem Modell. Ein besseres Modell liefert damit bessere Ergebnisse.

## Was der Skill tut

Die vollständigen Anweisungen stehen in [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md) (deutsche Übersetzung: [`SKILL.de.md`](SKILL.de.md)). Kurz gesagt:

- **Schreiben.** Wenn der Agent einen neuen Text schreibt, klärt er zuerst, wer ihn lesen wird, was diese Leser schon wissen und wozu sie ihn lesen, und richtet schon den ersten Entwurf auf sie aus. Dann liest er den Entwurf einmal aus ihrer Sicht und behebt, was ihm dabei auffällt.
- **Überarbeiten.** Er liest den Text so, wie seine Leser ihn lesen würden, und behebt nur konkrete Probleme, wo immer sie liegen, vom einzelnen Wort bis zum Aufbau des ganzen Textes. Deine Fakten, deine Kernaussagen und deine Stimme bleiben erhalten, und ein guter Text kommt fast unverändert zurück. Auf sachliche Fehler und auf Probleme, die über deinen Auftrag hinausgehen, weist er hin, statt sie zu beheben.
- **Leicht übersehene Probleme.** Beim Schreiben wie beim Überarbeiten achtet er besonders auf Spuren anderer Sprachen, etwa übernommene Wortstellung oder Datumsformate, und auf Stellen, die Kontext voraussetzen, den die Leser nicht gesehen haben, etwa das Gespräch des Agenten mit dir oder Namen, die er Dingen bei der Arbeit gegeben hat.
- **Gründlicher Modus.** Eine langsamere, gründlichere Arbeitsweise, die Außensichten einbezieht. Weil sie weit mehr Zeit und Tokens kostet, kommt sie nur auf Wunsch zum Einsatz. Bevor der Agent den Text selbst beurteilt, helfen ihm zwei neue KI-Instanzen (etwa Subagenten): Die eine sammelt Referenztexte desselben Genres, ohne deinen Text zu sehen, die andere liest den Text unvoreingenommen. Danach prüft der Agent wichtige Formulierungen und Fakten anhand von Quellen, die ursprünglich in der Sprache des Textes verfasst sind (keine Übersetzungen), und überarbeitet den Text. Er sagt dir, was er herangezogen hat und welche Schritte er ausgelassen hat.
- **Geltungsbereich.** Standardmäßig wird der Skill ungefragt bei Texten aktiv, die der Agent für andere schreibt, und bei seinen Berichten an dich: der abschließenden Antwort auf eine Anfrage, an der er gearbeitet hat, und Dokumenten, die er für dich verfasst. Du kannst ihn auf alles ausweiten, was der Agent schreibt, oder auf Texte für andere beschränken (siehe Abschnitt „Verwendung“).

## Vertrauenswürdigkeit

Reader's Ear besteht nur aus Anweisungen, ohne Skripte, Hooks oder MCP-Server. Abgesehen vom bearbeiteten Text speichert der Skill nur einen einzigen Satz, der deine Wahl des Geltungsbereichs festhält. Wenn du den Geltungsbereich wählst oder änderst oder die Frage des Agenten nach dem Geltungsbereich unbeantwortet lässt, speichert er diesen Satz in deiner persönlichen Anweisungsdatei (etwa einer `CLAUDE.md` auf Nutzerebene) oder im Gedächtnis deines Kontos und sagt dir, wo.

Im gründlichen Modus startet der Agent außerdem neue KI-Instanzen, etwa Subagenten, und sucht und liest Referenztexte und andere Quellen, etwa Webseiten. Gesucht wird mit Begriffen, Namen und kurzen Wendungen, nicht mit Passagen aus deinem Text.

## Installation

Wenn du sowohl claude.ai als auch Claude Code nutzt, beachte zuerst Folgendes: Claude Code lädt die Skills deines claude.ai-Kontos in Cloud-Sitzungen und ab Version 2.1.273 auch in Terminal-Sitzungen, in denen du dich mit `/login` bei diesem Konto angemeldet hast. Nutzt du Claude Code so, genügt der ZIP-Upload allein; installierst du zusätzlich das Plugin, lädt Claude Code den Skill doppelt.

Andernfalls wähle die Methode danach, wo du den Agenten nutzt:

| Wo du ihn nutzt | Empfohlene Methode |
| --- | --- |
| Claude Code auf deinem eigenen Rechner | [Claude-Code-Plugin](#claude-code-plugin) |
| claude.ai, Claude Desktop, Cowork oder Claude Code im Web | [ZIP-Upload in dein claude.ai-Konto](#claudeai-claude-desktop-und-cowork) |
| Codex, Cursor, Gemini CLI, GitHub Copilot und andere Agenten | [`npx skills`](#andere-agenten) |

### Claude-Code-Plugin

Führe in einer Claude-Code-Sitzung diese Befehle aus:

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

Der erste Befehl fügt dieses Repository als Plugin-Marketplace hinzu. Der zweite installiert daraus das Plugin `readers-ear`; Marketplace und Plugin tragen denselben Namen.

Ab Claude Code 2.1.275 erledigt ein einziger Befehl beides:

```
/plugin install readers-ear --marketplace motestream/readers-ear
```

**Zum Aktualisieren** führst du `/plugin marketplace update readers-ear` aus oder schaltest unter **Marketplaces** in `/plugin` die automatische Aktualisierung für diesen Marketplace ein.

**Um den Skill mit einem Team zu teilen**, öffnest du ein Terminal im Stammverzeichnis des Repositorys deines Projekts und führst diesen Befehl aus:

```sh
claude plugin marketplace add motestream/readers-ear --scope project
```

Anschließend committest du die `.claude/settings.json`, die der Befehl anlegt. Teammitglieder, die in Claude Code bestätigen, dass sie dem Projektordner vertrauen, erhalten den Marketplace und können das Plugin daraus installieren.

**Cloud-Sitzungen** (Claude Code im Web) laden keine Plugins, die auf deinem eigenen Rechner installiert sind. Lade den Skill für sie stattdessen auf claude.ai hoch, oder kopiere den Ordner `plugin/skills/readers-ear/` aus einer geklonten oder als ZIP heruntergeladenen Kopie dieses Repositorys in das Verzeichnis `.claude/skills/` des Projekts und committe ihn.

### claude.ai, Claude Desktop und Cowork

1. Stelle sicher, dass die Code-Ausführung eingeschaltet ist, denn Skills brauchen sie. In den Plänen Free, Pro und Max findest du sie unter **Settings > Capabilities**. In Team-Plänen sind Code-Ausführung und Skills für die Organisation standardmäßig eingeschaltet. In Enterprise-Plänen stellt ein Inhaber unter **Organization settings > Plugins & skills** auf dem Tab **Policy** sicher, dass beides eingeschaltet ist.
2. Lade dieses Repository als ZIP-Datei herunter (auf GitHub über **Code** > **Download ZIP**) und entpacke sie.
3. Packe den Ordner `plugin/skills/readers-ear` in eine neue ZIP-Datei, sodass sie einen Ordner `readers-ear` mit der Datei `SKILL.md` darin enthält. Der Ordner muss weiterhin `readers-ear` heißen.
4. Öffne auf claude.ai **Customize > Skills**, klicke auf **+** und dann auf **Create skill** > **Upload a skill**, und wähle anschließend die ZIP-Datei aus.

Der Skill gehört dann zu deinem Konto. Deshalb nutzen ihn auch Claude Desktop und Cowork, ebenso Claude Code unter den Bedingungen, die am Anfang des Abschnitts [Installation](#installation) beschrieben sind. Inhaber von Enterprise-Organisationen können den Skill außerdem hochladen, um ihn allen Mitgliedern bereitzustellen.

**Zum Aktualisieren** löschst du die alte Version unter **Customize > Skills** und lädst die neue ZIP-Datei hoch.

### Andere Agenten

Für diese Methode brauchst du Node.js. Führe diesen Befehl aus:

```sh
npx skills add motestream/readers-ear -g
```

`-g` installiert den Skill global für alle deine Projekte; ohne die Option landet er nur im aktuellen Projekt. Der Befehl erkennt die Agenten, die auf deinem Rechner installiert sind, und fragt, für welche er den Skill installieren soll. Um vorab einen festzulegen, ergänze `-a`, etwa `-a codex`.

**Zum Aktualisieren** führst du `npx skills update` aus.

**Ab GitHub CLI 2.90** kannst du stattdessen den Befehl `gh skill` verwenden, der sich noch in der Vorschauphase befindet:

```sh
gh skill install motestream/readers-ear readers-ear --scope user
```

Der Befehl fragt, für welchen Agenten er installieren soll; du kannst den Agenten aber auch mit `--agent` angeben. Zum Aktualisieren führst du `gh skill update` aus.

**Für eine Installation von Hand** kopierst du den Ordner `plugin/skills/readers-ear/` aus einer geklonten oder als ZIP heruntergeladenen Kopie dieses Repositorys in das Skill-Verzeichnis des Agenten, etwa `~/.claude/skills/` bei Claude Code.

## Verwendung

Reader's Ear startet von selbst, wenn der Agent Texte für andere schreibt oder dir berichtet. Du kannst den Skill auch mit eigenen Worten anfordern, etwa mit „Lass das natürlicher klingen“, oder ihn mit `/readers-ear` beim Namen aufrufen (mit `/readers-ear:readers-ear`, wenn du ihn als Claude-Code-Plugin installiert hast).

**Gründlicher Modus.** Der Agent nutzt ihn nur, wenn du ausdrücklich darum bittest, zum Beispiel: „Nimm dir Zeit und überarbeite das sorgfältig“ oder „Nimm dir Zeit und schreib das sorgfältig“. Soll er ihn jedes Mal nutzen, halte das in deinen gespeicherten Anweisungen fest, etwa in einer `CLAUDE.md`.

**Änderungen begrenzen.** Sag dem Agenten, worauf er sich beschränken soll, zum Beispiel: „Korrigiere nur die Tippfehler.“ Auf andere Probleme weist er dann hin, statt sie zu beheben.

**Geltungsbereich.** Der Standard umfasst Texte für andere und die Berichte des Agenten an dich: seine abschließende Antwort auf eine Anfrage, für die er etwas tun musste, etwa Dateien lesen oder Befehle ausführen, und die Dokumente, die er für dich verfasst. Nicht dazu gehören die Texte, die der Agent auf dem Weg zur abschließenden Antwort schreibt, und kurze Antworten, die er allein aus dem Gespräch heraus geben kann. In einer interaktiven Sitzung, in der sich Einstellungen speichern lassen, fragt der Agent ein einziges Mal, und zwar nachdem er zum ersten Mal einen Text im Standard-Geltungsbereich geliefert hat: Soll er beim Standard bleiben, den Skill auf alles anwenden, was er schreibt, oder ihn auf Texte für andere beschränken? Antwortest du nicht, bleibt er beim Standard und speichert das, sodass er nicht noch einmal fragt. Um den Geltungsbereich später zu ändern, sag es dem Agenten. Wo sich keine Einstellungen speichern lassen, fragt der Agent nicht; bittest du ihn dort, den Geltungsbereich zu ändern, gilt die Änderung nur für das aktuelle Gespräch, und der Agent gibt dir einen Satz, den du in deine eigenen Anweisungen aufnehmen kannst, damit spätere Sitzungen ihn übernehmen.

## Ausprobieren

Bevor du dich auf den Skill verlässt, probiere Folgendes aus:

- Vergleiche bei demselben Modell die Ausgabe mit und ohne Skill, am besten in mehreren Sprachen und in Genres mit festen Formulierungen, etwa geschäftlichen E-Mails, Vertragsklauseln und UI-Texten.
- Bitte den Agenten, aus deinen Notizen einen Text für andere zu schreiben. Was er liefert, sollte sich ohne weitere Überarbeitungsrunde für seine Leser gut lesen.
- Gib ihm einen Text, der schon gut ist, und bitte um eine Überarbeitung. Der Text sollte fast unverändert zurückkommen.
- Gib ihm einen inhaltlich korrekten Text, dessen Reihenfolge schwer nachzuvollziehen ist, und bitte um eine Überarbeitung. Er sollte den Text neu ordnen und dabei alle Fakten behalten.
- Prüfe beim Programmieren, ob der Skill die Commit-Nachrichten, PR-Beschreibungen und Dokumentation verbessert, die der Agent schreibt, und ob er vorhandene Texte anderer Personen unangetastet lässt.
- Prüfe nach einer Aufgabe mit mehreren Schritten, ob die abschließende Antwort des Agenten Wörter verwendet, die du kennst, statt Namen, die er sich bei der Arbeit ausgedacht hat, und ob sie nicht länger ist als für dich nötig.

## Übersetzungen

Der Agent lädt nur die englische [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md). Die Übersetzungen sind für Menschen gedacht. Weicht eine Übersetzung vom Englischen ab, ist die englische Fassung maßgeblich.

| Sprache | README | Skill-Anweisungen |
| --- | --- | --- |
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## Mitwirken

- Wenn sich `SKILL.md` oder die englische README ändert, aktualisiere im selben Commit die zugehörigen Übersetzungen, einschließlich des Datums am Anfang jeder Skill-Übersetzung.
- Teste Änderungen an `SKILL.md` in mindestens drei Sprachen, darunter eine mit wenig Trainingsdaten, und mit jedem Modell, das das Projekt unterstützt. Prüfe außerdem, wie sich die Frage nach dem Geltungsbereich und das Speichern der Antwort in einem nicht interaktiven Lauf (`claude -p`) und in einer Cloud-Sitzung verhalten.

## Lizenz

Reader's Ear wird unter der [MIT-Lizenz](../LICENSE) veröffentlicht.
