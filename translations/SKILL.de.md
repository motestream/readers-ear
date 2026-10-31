# readers-ear (deutsche Übersetzung zur Orientierung)

> Diese Übersetzung dient nur zur Orientierung. Agenten laden nur das englische Original [`plugin/skills/readers-ear/SKILL.md`](../plugin/skills/readers-ear/SKILL.md); bei Abweichungen gilt die englische Fassung. Übersetzt nach dem Stand der englischen Fassung vom 31. Oktober 2026.

## Name und Beschreibung

Dieser Abschnitt übersetzt die Angaben `name` und `description` am Anfang der englischen Datei. Die Beschreibung sagt dem Agenten, wann er den Skill verwenden soll.

- **Name:** `readers-ear`
- **Beschreibung:** Schreibt und überarbeitet Texte in jeder Sprache und jedem Genre so, dass sie sich für ihre Leser natürlich lesen. Der Skill ist in folgenden Fällen zu verwenden:
  - beim Schreiben von Texten, die andere Personen als der Nutzer lesen werden, etwa E-Mails, Artikel, Dokumente, Beiträge, Folien, Reden, Belletristik, Übersetzungen, UI-Texte, Commit-Nachrichten und PR-Beschreibungen
  - bei Berichten an den Nutzer: in der abschließenden Antwort nach der Arbeit an einer Anfrage des Nutzers oder in einem Dokument, das für den Nutzer erstellt wird, damit er es liest
  - wenn der Nutzer darum bittet, einen Text zu überarbeiten oder zu glätten oder ihn natürlicher oder weniger nach KI klingen zu lassen
  - für alle Texte, die der Agent schreibt, wenn die gespeicherten Anweisungen des Nutzers das vorsehen

  In den ersten beiden Fällen gilt das auch dann, wenn der Nutzer nicht um Hilfe bei der Formulierung gebeten hat.

Es folgt die Übersetzung der eigentlichen Anweisungen.

# Reader's Ear

Schreib und überarbeite Texte so, dass sie sich lesen, als hätte sie jemand, der ihre Sprache und ihr Genre sicher beherrscht, für die Leser geschrieben, für die sie bestimmt sind.

## Der Maßstab

Miss den Text an den Lesern, für die er bestimmt ist, nicht an Regeln. Frag dich, was diese Leser schon wissen, was sie dem Text entnehmen müssen, in welcher Beziehung sie zum Verfasser stehen und was sie von Genre und Sprache des Textes erwarten. Ob ein Wort, ein Satz oder ein Aufbau passt, hängt von diesen Antworten ab; dieselbe Entscheidung kann deshalb in einem Text richtig und in einem anderen falsch sein. Behalte die festen Formulierungen bei, die das Genre verlangt, auch wenn sie formelhaft wirken.

Um herauszufinden, was diese Leser schon wissen, trenne das, was sie gesehen haben, von dem, was nur du weißt. Ist der Nutzer selbst der Leser, hat er im Gespräch Folgendes gesehen: seine eigenen Nachrichten, deine abschließenden Antworten auf seine Anfragen und die Dokumente, die du für ihn erstellt hast. Geh bei allem anderen davon aus, dass er es nicht gesehen hat. Dazu gehören das, was du auf dem Weg zu einer Antwort im Gespräch geschrieben hast, deine Überlegungen, Tool-Ausgaben, Berichte von Subagenten und die Namen, die du Dingen bei der Arbeit gegeben hast. Außerhalb des Gesprächs bringt der Nutzer das Wissen aus seiner eigenen Arbeit und seinem Fachgebiet mit.

Beurteile den Text nach den Normen seiner eigenen Sprache, nicht nach denen des Englischen (der Sprache dieser Anweisungen) oder der Sprache, in der du denkst.

Textbeispiele und Styleguides, die der Nutzer bereitstellt, haben Vorrang vor diesem Skill. Hat der Nutzer nicht gesagt, wer den Text liest, erschließe es aus dem Text und der Anfrage.

## Neue Texte schreiben

So gehst du vor, wenn du selbst einen Text aus Informationen schreibst, die dir vorliegen, auch beim Übersetzen.

Beantworte vor dem Entwurf die Fragen aus dem Abschnitt „Der Maßstab“ für die Leser dieses Textes. Lege fest, wozu sie den Text lesen, etwa um eine Entscheidung zu treffen, einen Befehl auszuführen, den Stand der Dinge zu erfahren oder eine Geschichte zu genießen, und leite aus diesem Zweck ab, was sie am Ende mitnehmen müssen und was sie zuerst brauchen. Wähle den Aufbau, den das Genre und diese Leser erwarten; bei einer Übersetzung behalte den Aufbau der Vorlage bei (die Reihenfolge ihrer Abschnitte und Punkte), es sei denn, der Nutzer bittet dich, ihn anzupassen. Schreib dann den Entwurf für diese Leser und folge dabei den Normen der Sprache und des Genres des Textes.

Lies den Entwurf danach einmal so, wie seine Leser ihn lesen würden, und behebe die konkreten Probleme, die du findest, nach den Kriterien und Methoden aus dem Abschnitt „Texte überarbeiten“. Liest sich der Entwurf schon gut, lass ihn, wie er ist.

## Texte überarbeiten

Nach diesem Verfahren überarbeitest du vorhandene Texte.

Lies den Text mit den Augen seiner Leser, die ihn zum ersten Mal sehen. Als Problem zählt nur, was du konkret benennen kannst:

- eine Stelle, an der diese Leser stolpern oder den Faden verlieren würden oder an der sie nicht finden, was sie in diesem Moment brauchen
- eine Stelle, die jemand, der diese Sprache und dieses Genre sicher beherrscht, so nicht geschrieben hätte, und bei der du sagen kannst, wie er sie geschrieben hätte
- eine Passage, die diesen Lesern nichts gibt, was sie brauchen

Um Letzteres zu beurteilen, frag dich, ob der Text ohne diese Passage dem Zweck dieser Leser schlechter dienen würde.

Probleme gibt es auf jeder Ebene: im einzelnen Wort, im Satz, in einer Passage oder im Aufbau des ganzen Textes. Prüfe jede Ebene.

Behebe jedes Problem auf seiner eigenen Ebene. Streiche eine Passage, die diesen Lesern nichts gibt, was sie brauchen; in Texten, die dir der Nutzer vorlegt, tu das nur bei einem allgemeinen Auftrag (siehe Abschnitt „Vom Nutzer vorgelegte Texte“), und sag, was du gestrichen hast. In einer Übersetzung behalte alles bei, was die Vorlage sagt, und auch ihren Aufbau, es sei denn, der Nutzer bittet dich, ihn anzupassen. Ein Problem im Aufbau behebst du durch Neuaufbau, nicht durch Umformulieren: Liste auf, was der Text vermitteln muss, baue den betroffenen Teil in der Reihenfolge neu auf, die die Leser brauchen, und prüfe im Vergleich mit dem Original, ob im neu aufgebauten Teil etwas verloren gegangen, verändert worden oder hinzugekommen ist.

Ändere den Text nur, um konkrete Probleme zu beheben, und behalte eine Korrektur nur, wenn der Text dadurch besser wird. Hör auf, wenn kein konkretes Problem mehr übrig ist; so bleibt ein guter Text fast unverändert. Bemiss den Aufwand nach Länge und Tragweite des Textes.

## Auf zwei Probleme achten

Wenn du einen Entwurf oder einen Text aus Sicht seiner Leser liest, achte gezielt auf diese beiden Probleme.

**Einflüsse aus anderen Sprachen.** Andere Sprachen als die des Textes hinterlassen Spuren, auch Sprachen, die weder in der Eingabe noch in deinen Überlegungen vorkommen. Achte auf die Anzeichen, statt die Ausgangssprache bestimmen zu wollen: aus einer anderen Sprache übernommene Wortstellung, Formulierungen, Kollokationen, Redewendungen, Zeichensetzung und Anführungszeichen, Zahlen- und Datumsformate oder Anredeformen. Achte auch auf Fremdwörter, die diese Leser nicht verwenden würden, und auf vermischte regionale Schreibweisen, Schriftsysteme oder Wortschätze.

**Kontext, den die Leser nicht gesehen haben.** Suche nach Stellen, die etwas voraussetzen, das die Leser nicht gesehen haben (siehe Abschnitt „Der Maßstab“), etwa dein Gespräch mit dem Nutzer, Notizen, die den Lesern nicht vorliegen, oder Namen, die du Dingen bei der Arbeit gegeben hast. Frag dich bei jedem Namen, jedem Begriff und jedem Verweis auf etwas Früheres, wo diese Leser davon erfahren hätten. Kannst du das nicht beantworten, sag dasselbe mit Worten, die diese Leser kennen, etwa mit denen, die sie selbst verwendet haben, oder erkläre den Begriff dort, wo er zum ersten Mal vorkommt, wenn sie ihn brauchen.

## Vom Nutzer vorgelegte Texte

Wenn du einen Text überarbeitest oder übersetzt, den dir der Nutzer vorlegt:

- Wahre die Fakten, die Aussagen und die Stimme des Verfassers und ändere nicht mehr, als der Auftrag verlangt.
- Fasse einen allgemeinen Auftrag (überarbeiten, glätten, natürlicher oder weniger nach KI klingen lassen) so auf, dass er alle Ebenen umfasst. Ein enger Auftrag, etwa Tippfehler zu korrigieren, umfasst keine größeren Probleme: Behebe sie nicht, sondern weise auf diejenigen hin, die die Leser in die Irre führen oder verwirren würden, etwa sachliche Fehler, und mach keine Vorschläge zum Stil.
- Behebe sachliche Fehler nicht selbst, sondern weise auf sie hin, ebenso auf jede Mehrdeutigkeit, die sich nur auflösen ließe, wenn du rätst, was der Verfasser meint. Eine Unstimmigkeit, die du anhand der Fakten des Textes selbst auflösen kannst, etwa eine Anweisung, die nicht zu einer Zeitangabe im Text passt, ist dagegen ein Problem, das du behebst, und keines, auf das du nur hinweist.

## Bei jeder Aufgabe

- Verwende nur die Fakten, Zahlen und Zitate, die dir vorliegen. Die einzige Ausnahme: Enthält ein Text, den dir der Nutzer vorlegt, nur allgemeine Aussagen und umfasst der Auftrag, ihn natürlicher oder weniger nach KI klingen zu lassen, darfst du zutreffendes, weithin bekanntes Allgemeinwissen ergänzen, etwa wie eine verbreitete Technik funktioniert. Füge nie Erfahrungen, Daten, Zitate oder Aussagen über den Nutzer oder seine Organisation hinzu, und liste alles auf, was du ergänzt hast.
- Fehlen Informationen, frag den Nutzer und schreib den betreffenden Satz mit einem Platzhalter in eckigen Klammern, damit der Text fertig ist, sobald der Nutzer den Platzhalter ausfüllt. Kannst du nicht fragen, etwa weil du unbeaufsichtigt arbeitest, markiere die Lücke im Text auf dieselbe Weise.
- Bist du dir in deinem Urteil über die Sprache oder das Thema unsicher, ändere weniger und sag das.
- Liefere den fertigen Text und dazu, was der Nutzer wissen muss. Dazu gehören die Punkte, auf die du hingewiesen hast, statt sie zu beheben, und, falls du den Aufbau seines Textes geändert hast, ein Satz zur Begründung. Lass Arbeitsnotizen und Entwürfe weg, es sei denn, der Nutzer bittet darum.

## Gründlicher Modus

Verwende den gründlichen Modus nur, wenn der Nutzer im Gespräch oder in seinen gespeicherten Anweisungen ausdrücklich um eine langsamere, gründlichere Arbeit bittet, denn dieser Modus kostet weit mehr Zeit und Tokens. Im gründlichen Modus holst du von zwei neuen Kontexten je eine Außensicht auf den Text ein, bevor du ihn selbst beurteilst. Neue Kontexte sind solche, die das Gespräch nicht gesehen haben, etwa neu gestartete Subagenten, aber keine Kopien oder Forks des aktuellen Kontexts. Gib jedem nur das, was unten aufgeführt ist, und keine deiner eigenen Beobachtungen oder Vermutungen zum Text.

- **Referenzleser.** Nenne ihm die Sprache des Textes, die Leser, für die er bestimmt ist, sein Genre, seinen Zweck in groben Zügen und die Quellenregeln unten, aber gib ihm nicht den Text. Bitte ihn, einige Texte desselben Genres und Zwecks zu suchen, die diese Regeln erfüllen, und sie vollständig zu lesen, statt sich auf Ausschnitte aus den Suchergebnissen zu verlassen. Er berichtet, welche Quellen er verwendet hat und wie diese Texte geschrieben sind: Aufbau, feste Formulierungen, Länge, Register und alles andere, was das Genre erwartet.
- **Unvoreingenommener Leser.** Gib ihm nur den Text und eine Notiz zu dessen Lesern und Zweck; bei einer Übersetzung gib ihm die Übersetzung, nicht die Vorlage. Bitte ihn, den Text so zu lesen, wie diese Leser es täten. Er berichtet, wo er stolpert oder den Faden verliert und was er für die Hauptaussage hält.

Arbeite dann diese Schritte ab:

1. **Beide Berichte einholen.** Beim Überarbeiten startest du beide Leser gleichzeitig. Schreibst du einen neuen Text, auch eine Übersetzung, lass zuerst den Referenzleser arbeiten und schreib den Entwurf mit seinem Bericht vor Augen. Gib den fertigen Entwurf dann direkt an den unvoreingenommenen Leser weiter, ohne das Durchlesen aus dem Abschnitt „Neue Texte schreiben“; du liest ihn selbst in Schritt 2. Stehen keine neuen Kontexte zur Verfügung, verzichte auf das unvoreingenommene Lesen und such und lies die Referenzen selbst: beim Überarbeiten, bevor du nach Problemen suchst, oder beim Schreiben eines neuen Textes, bevor du den Entwurf schreibst.
2. **Den Text selbst lesen.** Lies den Text mit den Berichten vor Augen und liste seine Probleme auf. Behandle die Berichte als Anhaltspunkte, die du gegen deinen eigenen Leseeindruck abwägst, nicht als Liste von Änderungen, die du umsetzen musst.
3. **Mit Quellen abgleichen.** Gleiche die Begriffe, Namen, Zahlen und Schreibweisen, auf die es im Text ankommt, und jeden Punkt, bei dem du unsicher bist, mit aktuellen, maßgeblichen Quellen ab, etwa mit Wörterbüchern, Sprachratgebern und offiziellen Websites. Da der Text des Nutzers vertraulich sein kann, suche mit Begriffen, Namen und kurzen Wendungen, nicht mit Passagen daraus.
4. **Überarbeiten.** Geh vor wie im Abschnitt „Texte überarbeiten“. Nutze die Referenzen als Maßstab für den Text, nicht als Vorlage zum Abschreiben. In Texten, die dir der Nutzer vorlegt, haben die Fakten, die Aussagen und die Stimme des Verfassers Vorrang vor den Referenzen.
5. **Berichten.** Sag dem Nutzer kurz, was du herangezogen hast und was sich dadurch geändert hat, und nenne jeden Schritt, den du ausgelassen hast oder nicht ausführen konntest.

**Quellenregeln** (für die Schritte 1 und 3). Verwende Quellen, die ursprünglich in der Sprache des Textes verfasst sind und deren Wortlaut eine Person oder Organisation geprüft hat und verantwortet. Übersetzungen, auch die übersetzten Seiten mehrsprachiger Websites, kommen nicht infrage, weil sie Muster ihrer Ausgangssprache mitbringen können. Eine Ausnahme davon gibt es nur in Schritt 3: Um zu prüfen, wie eine Organisation ihre eigenen Namen und Begriffe schreibt, darfst du ihre offiziellen Seiten in der Sprache des Textes verwenden. Für Formulierungen und Genrekonventionen verwende Texte desselben Genres und Zwecks, etwa:

- Seiten öffentlicher Einrichtungen, großer Unternehmen, bedeutender Nachrichtenmedien und etablierter Verlage
- Werke anerkannter Autoren des Genres
- Texte aus kuratierten Korpora

Verwende keine Texte, deren Wortlaut offenbar niemand geprüft hat, etwa anonyme Seiten, Websites, die massenhaft Artikel produzieren, und automatisch erstellte Zusammenfassungen.

## Geltungsbereich

Der Geltungsbereich spielt nur eine Rolle, wenn dich niemand gebeten hat, diesen Skill zu verwenden: Er legt fest, auf welche Texte du den Skill von dir aus anwendest. Überarbeite unabhängig vom Geltungsbereich immer, was der Nutzer überarbeitet haben möchte. Es gibt drei Geltungsbereiche:

- **Texte für andere und Berichte an den Nutzer** (Standard): Texte für andere, wie unten definiert, und deine Berichte an den Nutzer. Ein Bericht ist entweder deine abschließende Antwort auf eine Anfrage, die der Nutzer direkt an dich richtet, sofern du dafür etwas tun musstest (etwa Dateien lesen, Befehle ausführen oder Aufgaben an Subagenten übergeben), oder ein Dokument oder anderes Material, das du erstellst, damit der Nutzer es liest. Was du im Gespräch auf dem Weg zur abschließenden Antwort schreibst, ist kein Bericht, ebenso wenig eine kurze Antwort, die du allein aus dem Gespräch heraus geben kannst.
- **Texte für andere**: Texte, die du schreibst und die letztlich andere Personen als der Nutzer lesen.
- **Alle Texte**: alle Texte, die du schreibst.

Ist in deinen Anweisungen oder deinem Gedächtnis kein Geltungsbereich festgelegt, verwende den Standard. Wenn du den ersten Text im Standard-Geltungsbereich geliefert hast, frag den Nutzer, ob er diesen Geltungsbereich behalten möchte, ob du den Skill auf alle Texte anwenden sollst, die du schreibst, oder nur auf Texte für andere. Frag nur, wenn alle folgenden Bedingungen erfüllt sind:

- Du arbeitest interaktiv mit dem Nutzer, nicht als Subagent oder unbeaufsichtigt.
- Der Nutzer kann diese Wahl treffen. Wer etwa als Endnutzer das Produkt eines Dritten verwendet, kann das nicht.
- Es gibt einen geeigneten Ort, um die Antwort zu speichern.

Stell diese Frage nur ein einziges Mal, über alle Sitzungen hinweg. Geht der Nutzer ohne Antwort zu etwas anderem über, werte das als Entscheidung für den Standard und speichere sie wie unten beschrieben, damit keine spätere Sitzung erneut fragt.

Wenn der Nutzer antwortet oder den Geltungsbereich später ändert, speichere seine Wahl als einen Satz in seiner Sprache, der den Skill und den Geltungsbereich nennt. Auf Englisch zum Beispiel: „Use the readers-ear skill on text you write for other people to read and on your final answers and documents for me“, „Use the readers-ear skill on all prose you write“ oder „Use the readers-ear skill only on text you write for other people to read.“

Speichere den Satz an einem persönlichen Ort, aus dem ihn jede künftige Sitzung lädt, etwa in einer Anweisungsdatei auf Nutzerebene oder im Gedächtnis des Kontos. Nutze dafür keine Datei, die ein Team gemeinsam verwendet, kein auf ein Projekt beschränktes Gedächtnis und keinen Ort, der beim nächsten Mal nicht geladen wird, etwa eine Cloud-Umgebung, die nach Gebrauch verworfen wird. Sag dem Nutzer, wo du den Satz gespeichert hast. Ändert der Nutzer den Geltungsbereich dort, wo es keinen solchen Ort gibt, wende seine Wahl nur im aktuellen Gespräch an, sag das und gib ihm den Satz, damit er ihn in seine eigenen Anweisungen einfügen kann.

Wendest du den Skill unaufgefordert an, bearbeite nur die Texte, die du selbst schreibst, und lass Texte anderer Personen, wie sie sind, auch in derselben Datei. Wendest du ihn im Rahmen einer anderen Aufgabe an, etwa beim Schreiben einer Commit-Nachricht oder eines Berichts an den Nutzer, liefere den Text so, wie es diese Aufgabe verlangt, und erwähne nur, was der Nutzer wissen muss.
