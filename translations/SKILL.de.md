# readers-ear (deutsche Übersetzung zur Orientierung)

> Diese Übersetzung dient nur zur Orientierung. Agenten laden nur das englische Original [`plugin/skills/readers-ear/SKILL.md`](../plugin/skills/readers-ear/SKILL.md); bei Abweichungen gilt die englische Fassung. Übersetzt nach dem Stand der englischen Fassung vom 25. Oktober 2026.

```yaml
---
name: readers-ear
description: Überarbeitet Texte vom Aufbau bis zur Wortwahl so, dass sie sich für die vorgesehenen Leser natürlich lesen – in jeder Sprache und jedem Genre. Immer verwenden, wenn du Texte schreibst, die andere Personen als der Nutzer lesen werden (E-Mails, Artikel, Dokumente, Beiträge, Folien, Reden, Belletristik, Übersetzungen, UI-Texte), auch wenn keine Überarbeitung verlangt wird; immer, wenn der Nutzer darum bittet, einen Text zu überarbeiten oder zu glätten oder ihn natürlicher oder weniger nach KI klingen zu lassen; und für alle Texte, wenn die gespeicherten Anweisungen des Nutzers das vorsehen.
---
```

# Reader's Ear

Ziel ist ein Text, der sich liest, als hätte ihn jemand, der die Sprache und das Genre des Textes sicher beherrscht, für die vorgesehenen Leser geschrieben. Maßstab sind diese Leser, nicht Regeln: Arbeite nicht mit Listen verbotener Wörter oder Muster, und behalte die festen Formulierungen bei, die das Genre oder die Konvention verlangt. Beurteile den Text nach den Normen seiner eigenen Sprache – nicht nach denen der Sprache dieser Anleitung (im Original Englisch) oder der Sprache, in der du denkst. Textbeispiele und Styleguides des Nutzers haben Vorrang vor allem, was in dieser Anleitung steht.

## Standardüberarbeitung

Lies den Text so, wie die vorgesehenen Leser ihn zum ersten Mal lesen würden. Prüfe dann das Ganze vor den Teilen: Kläre zuerst, was der Text diesen Lesern vermitteln muss, und ob sein Aufbau, gemessen an den Normen seines Genres, das leistet (was am Anfang steht, wie die Teile gruppiert und angeordnet sind, wozu jeder Teil da ist). Erst danach kommen Absätze, Sätze und Wörter. Ausgefeilte Sätze retten keinen Aufbau, der nicht trägt, und wer den Aufbau umbaut, ändert die Sätze ohnehin.

Ändere nur, was du als konkretes Problem benennen kannst: eine Stelle, an der die Leser stolpern oder den Faden verlieren würden; eine Information, die sie nicht dort finden, wo sie sie brauchen; oder eine Formulierung, die jemand, der diese Sprache und dieses Genre beherrscht, so nicht geschrieben hätte. Behebe jedes Problem auf der Ebene, auf der es liegt, vom einzelnen Wort bis zum ganzen Text; manchmal besteht die Lösung im Streichen. Einzelne Sätze umzuformulieren ändert am Aufbau nichts. Liegt das Problem im Aufbau, liste deshalb auf, was der Text vermitteln muss (seine Fakten, seine Aussagen, seinen Zweck), und baue den betroffenen Teil oder den ganzen Text von dieser Liste aus neu auf, in der Reihenfolge und Form, die diese Leser brauchen. Vergleiche das Ergebnis danach mit dem Original, um aufzuspüren, welche Fakten oder Aussagen beim Neuaufbau verloren gegangen, verändert worden oder neu hinzugekommen sind. Behalte eine Änderung nur, wenn sie den Text besser macht, und hör auf, wenn du kein weiteres Problem benennen kannst. Ein Text, der schon gut ist, sollte fast unverändert bleiben. Bemiss den Aufwand nach Länge und Tragweite des Textes.

Zwei Arten von Problemen übersieht man leicht. Zum einen sind das Einflüsse aus anderen Sprachen als der des Textes, auch aus solchen, die weder in der Eingabe noch in deinen Überlegungen vorkommen. Dazu gehören übernommene Wortstellung, Formulierungen, Kollokationen, Redewendungen, Zeichensetzung und Anführungszeichen, Zahlen- und Datumsformate oder Anredeformen; Fremdwörter, die diese Leser nicht verwenden würden; vermischte regionale Schreibweisen, Schriftsysteme oder Wortschätze. Zum anderen kann der Text auf Kontext bauen, den die Leser nicht kennen, etwa auf dein Gespräch mit dem Nutzer.

Für alles, was du überarbeitest, gilt:

- Wahre in Texten, die dir der Nutzer gibt, die Fakten, die Aussagen und die Stimme ihres Verfassers, und ändere nicht mehr, als der Auftrag verlangt. Weise auf Fehler oder Mehrdeutigkeiten hin, die den Sinn betreffen, statt sie zu beseitigen. Ein allgemeiner Auftrag, etwa einen Text zu überarbeiten, zu glätten oder natürlicher klingen zu lassen, schließt den Aufbau ein; ein engerer, etwa nur Tippfehler oder Grammatik zu korrigieren, schließt ihn nicht ein – weise dann auf Probleme im Aufbau hin, statt sie zu beheben. Eine Übersetzung folgt dem Aufbau ihrer Vorlage, es sei denn, der Nutzer bittet dich, diesen Aufbau anzupassen.
- Erfinde keine Fakten, Zahlen oder Zitate, um einen Text konkreter zu machen; benenne die Lücke oder frage nach.
- Bist du unsicher, ob du die Sprache oder das Thema gut genug beurteilen kannst, ändere weniger und sag das.
- Liefere den fertigen Text und alles, was der Nutzer wissen muss, etwa Stellen, die du nur angemerkt statt geändert hast. Hast du den Aufbau eines Textes geändert, den dir der Nutzer gegeben hat, erkläre in ein, zwei Sätzen, was du geändert hast und warum. Deine Arbeitsnotizen und Entwürfe gehören nicht dazu, es sei denn, der Nutzer bittet darum.

## Gründliche Überarbeitung

Mach das nur, wenn der Nutzer ausdrücklich um eine langsamere, gründlichere Überarbeitung als üblich bittet, denn sie kostet weit mehr Zeit und Tokens. Die gründliche Überarbeitung ergänzt die Standardüberarbeitung um Einschätzungen von außen. Hol sie ein, bevor du dir selbst ein Urteil über den Text bildest, damit dein Urteil sie nicht beeinflusst. Geh in dieser Reihenfolge vor:

1. Bevor du selbst nach Problemen suchst, starte zwei neue Kontexte, die dein Gespräch nicht kennen, etwa neu angelegte Subagenten (keine Kopien dieses Kontexts); sie können gleichzeitig arbeiten. Teile keinem der beiden deine eigenen Beobachtungen oder Vermutungen zum Text mit.
   - Referenzsuche: Nenne diesem Kontext die Sprache des Textes, die vorgesehenen Leser, das Genre, den Zweck in groben Zügen und die Quellenregeln unten, aber gib ihm nicht den Text. Lass ihn einige Texte desselben Genres und Zwecks suchen, die diese Regeln erfüllen. Er soll die gefundenen Seiten vollständig lesen, nicht nur die Ausschnitte in den Suchergebnissen, die verwendeten Seiten auflisten und zusammenfassen, wie diese Texte geschrieben sind: Aufbau, feste Formulierungen, Länge, Register und alles andere, was in diesem Genre üblich ist.
   - Unvoreingenommenes Lesen: Gib diesem Kontext nur den Text und eine Notiz zu dessen Lesern und Zweck. Er soll den Text so lesen, wie diese Leser es täten, und berichten, wo er stolpert oder den Faden verliert und was er für die Hauptaussage hält.
2. Lies den Text dann selbst, mit beiden Berichten vor Augen, und liste seine Probleme auf.
3. Gleiche die Punkte, auf die es den Lesern am meisten ankommt oder bei denen du am unsichersten bist (Rechtschreibung, Zeichensetzung, Begriffe, Fakten usw.), mit aktuellen, maßgeblichen Quellen ab, etwa mit Wörterbüchern, Sprachratgebern und offiziellen Seiten.
4. Überarbeite wie bei der Standardüberarbeitung. Nutze die Referenzen als Maßstab für den Text, nicht als Vorlage zum Abschreiben; in Texten, die dir der Nutzer gegeben hat, haben die Fakten, die Aussagen und die Stimme ihres Verfassers weiterhin Vorrang.

Quellenregeln für die Schritte 1 und 3: Nimm Quellen in der Sprache des Textes, deren Wortlaut eine Person oder Organisation geprüft hat und verantwortet.

- Nimm keine Übersetzungen, auch keine guten, denn sie können Muster ihrer Ausgangssprache mitbringen. Das gilt auch für übersetzte Fassungen von Seiten mehrsprachiger Websites.
- Für Formulierungen und Genrekonventionen nimm Texte desselben Genres und Zwecks, etwa die originalsprachigen Seiten öffentlicher Einrichtungen, großer Unternehmen und etablierter Verlage, Werke anerkannter Autoren dieses Genres sowie Texte aus Korpora. Unter diesen Quellen sind Texte aus der Zeit vor der Verbreitung generativer KI (etwa bis 2022) am sichersten; spätere Texte taugen ebenfalls, wenn erkennbar eine Redaktion oder Institution für sie einsteht.

Kannst du keine neuen Kontexte starten, verzichte auf das unvoreingenommene Lesen, such und lies die Referenzen selbst, bevor du nach Problemen suchst, und mach dann mit Schritt 2 weiter.

Sag dem Nutzer kurz, was du herangezogen hast und was sich dadurch geändert hat, und nenne jeden Schritt, den du nicht ausführen konntest, etwa das Lesen in neuen Kontexten oder die Websuche. Gib nie einen Schritt als erledigt aus, den du ausgelassen hast.

## Geltungsbereich

Der Geltungsbereich legt nur fest, was du unaufgefordert überarbeitest; was der Nutzer überarbeitet haben möchte, überarbeitest du immer. Es gibt zwei Geltungsbereiche:

- A (Standard): Texte, die du schreibst und die letztlich von anderen Personen als dem Nutzer gelesen werden.
- B: alle Texte, die du schreibst.

Ist in deinen Anweisungen oder deinem Gedächtnis kein Geltungsbereich festgelegt, nimm A und frage den Nutzer, nachdem du den Text geliefert hast, nur einmal, ob er B möchte. Frage nicht, wenn der Nutzer diese Wahl nicht treffen kann (etwa als Endnutzer des Produkts eines Drittanbieters), wenn du als Subagent oder unbeaufsichtigt arbeitest oder wenn es keinen geeigneten Ort gibt, an dem sich die Antwort speichern lässt (siehe unten).

Antwortet der Nutzer oder ändert er den Geltungsbereich später, halte seine Wahl in einem Satz fest, der in der Sprache des Nutzers verfasst ist und diesen Skill und den Geltungsbereich nennt, zum Beispiel: „Verwende den Skill readers-ear für alle Texte, die du schreibst“ oder „Verwende den Skill readers-ear für Texte, die du schreibst und die andere lesen sollen.“ Speichere den Satz an einem persönlichen Ort, aus dem ihn jede künftige Sitzung lädt, etwa in einer Anweisungsdatei auf Nutzerebene oder im Gedächtnis des Nutzerkontos. Nutze keine Dateien, die ein Team gemeinsam verwendet, kein auf ein Projekt beschränktes Gedächtnis und keine Orte, an denen sich der Satz zwar speichern lässt, beim nächsten Mal aber nicht geladen wird, etwa eine Cloud-Umgebung, die nach Gebrauch gelöscht wird. Sag dem Nutzer, wo du den Satz gespeichert hast. Gibt es keinen solchen Ort, lass die Wahl nur für dieses Gespräch gelten, sag das und gib dem Nutzer den Satz, damit er ihn in seine eigenen Anweisungen einfügen kann.
