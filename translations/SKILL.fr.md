# readers-ear (traduction française)

> Cette traduction est fournie à titre indicatif. Les agents ne chargent que l'original anglais, [`plugin/skills/readers-ear/SKILL.md`](../plugin/skills/readers-ear/SKILL.md) ; en cas de divergence, la version anglaise fait foi. Traduction établie d'après la version anglaise du 31 octobre 2026.

## Nom et description

Cette section traduit le nom (`name`) et la description (`description`) qui figurent en tête du fichier anglais. La description indique à l'agent quand utiliser la compétence.

- **Nom** : `readers-ear`
- **Description** : Rédige et révise des textes, dans toutes les langues et tous les genres, pour qu'ils paraissent naturels au lecteur auquel ils sont destinés. À utiliser :
  - quand l'agent rédige un texte que liront d'autres personnes que l'utilisateur, comme des e-mails, des articles, des documents, des publications, des diapositives, des discours, des textes de fiction, des traductions, des textes d'interface, des messages de commit et des descriptions de pull request ;
  - quand l'agent rend compte à l'utilisateur, dans la réponse finale qui suit le traitement de sa demande ou dans un document préparé à son intention ;
  - quand l'utilisateur demande de réviser ou de peaufiner un texte, ou de le rendre plus naturel ou moins semblable à un texte d'IA ;
  - pour tous les textes que rédige l'agent, quand les instructions enregistrées par l'utilisateur le prévoient.

  Dans les deux premiers cas, la compétence est à utiliser même si l'utilisateur n'a pas demandé d'aide pour la formulation.

Ce qui suit est la traduction du corps des instructions.

# Reader's Ear

Faites en sorte que le texte que vous rédigez ou révisez se lise comme si une plume expérimentée, rompue à la langue et au genre de ce texte, l'avait écrit pour le lecteur auquel il est destiné.

## Le critère

Mesurez le texte à l'aune du lecteur auquel il est destiné, et non à l'aune de règles. Demandez-vous ce que ce lecteur sait déjà, ce que le texte doit lui apporter, quelle relation il entretient avec l'auteur et ce qu'il attend du genre et de la langue du texte. C'est de ces réponses que dépend la justesse d'un mot, d'une phrase ou d'une structure : un même choix peut donc convenir dans un texte et non dans un autre. Conservez les formules consacrées qu'exige le genre, même quand elles paraissent convenues.

Pour déterminer ce que ce lecteur sait déjà, distinguez ce qu'il a vu de ce que vous êtes seul à savoir. Quand le lecteur est l'utilisateur, ce qu'il a vu dans la conversation, ce sont ses propres messages, vos réponses finales à ses demandes et les documents que vous avez préparés à son intention. Considérez qu'il n'a pas vu le reste, notamment ce que vous avez écrit dans la conversation en travaillant à une réponse, votre raisonnement, les sorties des outils, les rapports des sous-agents et les noms que vous avez donnés à certains éléments en cours de travail. En dehors de la conversation, l'utilisateur sait ce qu'il tient de son propre travail et de son domaine.

Jugez le texte selon les normes de sa propre langue, et non selon celles de l'anglais (la langue originale de ces instructions) ni selon celles de la langue dans laquelle vous pensez.

Les exemples de textes et les guides de style fournis par l'utilisateur priment sur cette compétence. Si l'utilisateur n'a pas précisé qui est le lecteur, déduisez-le du texte et de la demande.

## Rédiger un nouveau texte

Cette section s'applique quand vous rédigez vous-même un texte à partir des informations dont vous disposez, y compris quand vous traduisez.

Avant de rédiger, répondez pour ce lecteur aux questions de la section « Le critère ». Déterminez dans quel but ce lecteur lit le texte, par exemple pour prendre une décision, exécuter une commande informatique, faire le point sur une situation ou prendre plaisir à une histoire, puis, à partir de ce but, ce qu'il doit en retirer et ce dont il a besoin en premier. Choisissez la structure qu'attendent le genre et ce lecteur ; pour une traduction, conservez celle du texte source (l'ordre de ses sections et de ses points), sauf si l'utilisateur vous demande de l'adapter. Rédigez ensuite votre brouillon pour ce lecteur, en suivant les normes de la langue et du genre du texte.

Le brouillon terminé, lisez-le une fois comme le ferait son lecteur, et corrigez les problèmes concrets que vous y trouvez en appliquant les critères et les méthodes de la section « Réviser un texte ». Si le brouillon se lit déjà bien, laissez-le tel quel.

## Réviser un texte

Suivez cette procédure pour réviser un texte existant.

Lisez le texte comme le ferait le lecteur auquel il est destiné, qui le découvre. Un problème ne compte que si vous pouvez le désigner :

- un endroit où ce lecteur buterait, perdrait le fil ou ne trouverait pas ce dont il a besoin au moment où il en a besoin ;
- un endroit où une plume expérimentée, rompue à cette langue et à ce genre, n'aurait pas écrit ainsi, à condition que vous puissiez dire comment elle aurait écrit ;
- un passage qui n'apporte à ce lecteur rien dont il ait besoin.

Pour juger de ce dernier cas, demandez-vous si, sans ce passage, le texte servirait moins bien le but de ce lecteur.

Les problèmes se situent à tous les niveaux : un mot, une phrase, un passage ou la structure du texte entier. Examinez chacun de ces niveaux.

Corrigez chaque problème au niveau où il se pose. Supprimez un passage qui n'apporte à ce lecteur rien dont il ait besoin ; dans un texte fourni par l'utilisateur, ne le faites que sur une demande générale (voir « Textes fournis par l'utilisateur »), et indiquez ce que vous avez supprimé. Dans une traduction, conservez tout ce que dit le texte source, et conservez sa structure, sauf si l'utilisateur vous demande de l'adapter. Corrigez un problème de structure en reconstruisant, et non en reformulant : dressez la liste de ce que le texte doit transmettre, reconstruisez la partie concernée dans l'ordre dont le lecteur a besoin, puis comparez la partie reconstruite avec l'original pour repérer tout ce qui aurait été perdu, modifié ou ajouté.

Ne modifiez le texte que pour corriger des problèmes concrets, et ne gardez une correction que si elle améliore le texte. Arrêtez-vous quand il ne reste plus aucun problème concret, de sorte qu'un bon texte ressorte presque inchangé. Proportionnez le temps que vous y consacrez à la longueur et aux enjeux du texte.

## Deux problèmes à rechercher

Quand vous lisez un brouillon ou un texte comme le ferait son lecteur, recherchez en particulier les deux problèmes suivants.

**Interférences d'autres langues.** Les langues autres que celle du texte y laissent des traces, même celles qui n'apparaissent nulle part dans ce qui vous a été fourni ni dans votre raisonnement. Cherchez-en les signes plutôt que d'essayer d'identifier la langue en cause : ordre des mots, tournures, collocations, expressions idiomatiques, ponctuation et guillemets, formats des nombres et des dates ou façons de s'adresser au lecteur, calqués sur une autre langue. Cherchez aussi les mots étrangers que ce lecteur n'emploierait pas, ainsi que le mélange de variantes régionales d'orthographe ou de vocabulaire, ou le mélange de systèmes d'écriture.

**Contexte que le lecteur n'a pas vu.** Cherchez les endroits qui reposent sur quelque chose que le lecteur n'a pas vu (voir « Le critère »), comme votre conversation avec l'utilisateur, des notes dont le lecteur ne dispose pas ou des noms que vous avez donnés à certains éléments en cours de travail. Pour chaque nom, chaque terme et chaque renvoi à un élément antérieur, demandez-vous où ce lecteur l'aurait appris. Si vous ne pouvez pas désigner cet endroit, exprimez l'idée avec des mots que ce lecteur connaît, comme ceux qu'il a lui-même employés, ou, s'il a besoin du terme, expliquez-le là où il apparaît pour la première fois.

## Textes fournis par l'utilisateur

Quand vous révisez ou traduisez un texte fourni par l'utilisateur :

- Conservez les faits, les idées et la voix de l'auteur, et ne modifiez pas plus que ce que la demande exige.
- Considérez qu'une demande générale (réviser, peaufiner, rendre le texte plus naturel ou moins semblable à un texte d'IA) couvre tous les niveaux. Une demande restreinte, comme corriger les fautes de frappe, ne couvre pas les problèmes de plus grande ampleur : signalez, au lieu de les corriger, ceux qui induiraient le lecteur en erreur ou le dérouteraient, comme les erreurs factuelles, et ne faites aucune suggestion de style.
- Signalez, plutôt que de les corriger, les erreurs factuelles et toute ambiguïté que seule une supposition sur l'intention de l'auteur permettrait de lever. Une incohérence que vous pouvez résoudre à partir des faits du texte lui-même, comme une consigne qui contredit un horaire donné dans le texte, est un problème à corriger, et non à signaler.

## Dans toutes les tâches

- N'utilisez que les faits, les chiffres et les citations dont vous disposez. Seule exception : quand un texte fourni par l'utilisateur ne contient que des généralités et que la demande consiste notamment à le rendre plus naturel ou moins semblable à un texte d'IA, vous pouvez ajouter des informations générales exactes et largement connues, comme le fonctionnement d'une technique courante. N'ajoutez jamais d'expériences vécues, de données, de citations ni d'affirmations concernant l'utilisateur ou son organisation, et dressez la liste de tout ce que vous avez ajouté.
- S'il manque une information, demandez-la à l'utilisateur, et rédigez la phrase qui la nécessite en y laissant un espace réservé entre crochets, de sorte que le texte soit prêt dès que l'utilisateur l'aura rempli. Quand vous ne pouvez pas poser la question, par exemple quand vous travaillez sans supervision, signalez le manque dans le texte de la même façon.
- Si vous doutez de votre jugement sur la langue ou sur le sujet, modifiez moins et dites-le.
- Livrez le texte final ainsi que ce que l'utilisateur doit savoir, notamment les points que vous avez signalés au lieu de les corriger et, si vous avez restructuré le texte de l'utilisateur, une phrase qui explique pourquoi. N'incluez ni notes de travail ni brouillons, sauf si l'utilisateur les demande.

## Mode approfondi

N'utilisez le mode approfondi que si l'utilisateur demande explicitement un travail plus lent et plus minutieux, dans la conversation ou dans ses instructions enregistrées, car il coûte bien plus cher en temps et en tokens. En mode approfondi, vous recueillez sur le texte les regards extérieurs de deux contextes vierges avant de le juger vous-même. Les contextes vierges sont des contextes qui n'ont pas vu la conversation, comme de nouveaux sous-agents, et non des copies ou des forks du contexte actuel. Ne donnez à chacun que ce qui est indiqué ci-dessous, sans y joindre vos propres observations ni vos soupçons sur le texte.

- **Lecteur de références.** Indiquez-lui la langue du texte, le lecteur visé et le genre, une idée générale de sa finalité et les règles relatives aux sources ci-dessous, mais pas le texte lui-même. Demandez-lui de trouver quelques textes de même genre et de même finalité qui respectent ces règles, et de les lire en entier plutôt que de se fier aux extraits affichés dans les résultats de recherche. Il indique les sources qu'il a utilisées et la manière dont ces textes sont écrits : structure, formules consacrées, longueur, registre et tout ce que le genre exige par ailleurs.
- **Lecteur à froid.** Ne lui donnez que le texte et une note sur son lecteur et sa finalité ; pour une traduction, donnez-lui la traduction, et non le texte source. Demandez-lui de lire le texte comme le ferait ce lecteur. Il indique où il bute ou perd le fil, et ce qu'il considère comme l'idée principale.

Suivez ensuite ces étapes :

1. **Obtenez les deux rapports.** Pour une révision, lancez les deux lecteurs en même temps. Pour un nouveau texte, traduction comprise, lancez d'abord le lecteur de références et rédigez avec son rapport sous les yeux. Donnez ensuite directement le brouillon terminé au lecteur à froid, sans faire d'abord la lecture prévue dans « Rédiger un nouveau texte » : vous le lirez vous-même à l'étape 2. Si vous ne disposez pas de contextes vierges, renoncez à la lecture à froid et trouvez puis lisez vous-même les références : avant de chercher des problèmes, pour une révision, ou avant de rédiger, pour un nouveau texte.
2. **Lisez vous-même le texte.** Les rapports en main, lisez le texte et dressez la liste de ses problèmes. Considérez les rapports comme des éléments à mettre en balance avec votre propre lecture, et non comme une liste de modifications à apporter.
3. **Vérifiez auprès des sources.** Contrôlez les termes, les noms, les chiffres et les graphies dont dépend le texte, ainsi que tout point dont vous n'êtes pas sûr, en vous appuyant sur des sources actuelles qui font autorité, comme les dictionnaires, les guides d'usage et les sites officiels. Le texte de l'utilisateur pouvant être confidentiel, faites vos recherches avec des termes, des noms et de courtes expressions, et non avec des passages du texte.
4. **Révisez.** Procédez comme dans « Réviser un texte ». Servez-vous des références comme d'un étalon pour mesurer le texte, et non comme de formulations à recopier. Dans le texte de l'utilisateur, les faits, les idées et la voix de l'auteur priment sur les références.
5. **Rendez compte.** Indiquez brièvement à l'utilisateur ce que vous avez consulté et ce que cela a changé, et mentionnez chaque étape que vous avez sautée ou que vous n'avez pas pu réaliser.

**Règles relatives aux sources** (étapes 1 et 3). Utilisez des sources rédigées à l'origine dans la langue du texte, dont la formulation a été vérifiée par une personne ou une organisation qui en assume la responsabilité. Les traductions, y compris les pages traduites des sites multilingues, ne conviennent pas, car elles peuvent garder les tournures de la langue source. Seule exception, à l'étape 3 : pour vérifier comment une organisation écrit ses propres noms et termes, vous pouvez consulter ses pages officielles dans la langue du texte, même s'il s'agit de traductions. Pour les tournures et les conventions du genre, utilisez des textes de même genre et de même finalité, par exemple :

- les pages d'institutions publiques, de grandes entreprises, de grands médias et d'éditeurs reconnus ;
- les écrits d'auteurs respectés dans le genre ;
- des textes issus de corpus soigneusement constitués.

N'utilisez pas de textes dont personne ne semble avoir vérifié la formulation, comme les pages anonymes, les sites qui produisent des articles en masse et les résumés générés automatiquement.

## Périmètre

Le périmètre ne compte que lorsque personne ne vous a demandé d'utiliser cette compétence : il détermine à quels textes vous l'appliquez de votre propre initiative. Quel que soit le périmètre, révisez toujours ce que l'utilisateur vous demande de réviser. Il existe trois périmètres :

- **Textes destinés à d'autres personnes et comptes rendus à l'utilisateur** (par défaut) : les textes destinés à d'autres personnes, tels que définis ci-dessous, et vos comptes rendus à l'utilisateur. Il existe deux sortes de comptes rendus : votre réponse finale à une demande que l'utilisateur vous adresse directement, lorsque vous avez dû effectuer un travail pour y répondre (par exemple lire des fichiers, exécuter des commandes ou confier des tâches à des sous-agents) ; et tout document ou autre support que vous préparez à l'intention de l'utilisateur. Ce que vous écrivez dans la conversation en travaillant à la réponse finale n'est pas un compte rendu, pas plus qu'une réponse courte que vous pouvez donner à partir de la seule conversation.
- **Textes destinés à d'autres personnes** : les textes que vous rédigez et dont les lecteurs finaux sont d'autres personnes que l'utilisateur.
- **Tous les textes** : tous les textes que vous rédigez.

Si aucun périmètre n'est fixé dans vos instructions ou votre mémoire, appliquez le périmètre par défaut. Après avoir livré le premier texte relevant du périmètre par défaut, demandez à l'utilisateur s'il souhaite conserver ce périmètre, appliquer la compétence à tous les textes que vous rédigez ou ne l'appliquer qu'aux textes destinés à d'autres personnes. Posez cette question seulement si toutes les conditions suivantes sont réunies :

- Vous travaillez avec l'utilisateur de manière interactive, et non en tant que sous-agent ou sans supervision.
- L'utilisateur peut faire ce choix. L'utilisateur final du produit d'un tiers, par exemple, ne le peut pas.
- Il existe un emplacement approprié pour enregistrer la réponse.

Ne posez cette question qu'une seule fois, toutes sessions confondues. Si l'utilisateur passe à autre chose sans répondre, considérez qu'il a choisi le périmètre par défaut et enregistrez ce choix comme indiqué ci-dessous, afin qu'aucune session ultérieure ne repose la question.

Lorsque l'utilisateur répond, ou modifie le périmètre par la suite, enregistrez son choix sous la forme d'une phrase, dans la langue de l'utilisateur, qui nomme la compétence et le périmètre. En anglais, par exemple :

- « Use the readers-ear skill on text you write for other people to read and on your final answers and documents for me. » (en français : « Utilise la compétence readers-ear pour les textes que tu rédiges à l'intention d'autres personnes, ainsi que pour tes réponses finales et les documents que tu prépares pour moi. »)
- « Use the readers-ear skill on all prose you write. » (en français : « Utilise la compétence readers-ear pour tous les textes que tu rédiges. »)
- « Use the readers-ear skill only on text you write for other people to read. » (en français : « Utilise la compétence readers-ear uniquement pour les textes que tu rédiges à l'intention d'autres personnes. »)

Enregistrez cette phrase dans un emplacement personnel que chargent toutes les sessions futures, comme un fichier d'instructions au niveau utilisateur ou la mémoire du compte, plutôt que dans un fichier partagé avec une équipe, dans une mémoire limitée à un projet ou dans un emplacement qui ne sera pas chargé la prochaine fois, comme un environnement cloud jetable. Indiquez à l'utilisateur où vous l'avez enregistrée. Si l'utilisateur modifie le périmètre alors qu'aucun emplacement de ce type n'existe, appliquez ce choix à la conversation en cours uniquement, dites-le, et donnez à l'utilisateur la phrase à coller dans ses propres instructions.

Quand vous appliquez la compétence sans qu'on vous l'ait demandé, ne travaillez que sur les textes que vous rédigez vous-même, et laissez tels quels les textes écrits par d'autres, même dans le même fichier. Si vous l'appliquez dans le cadre d'une autre tâche, comme la rédaction d'un message de commit ou d'un compte rendu à l'utilisateur, livrez le texte sous la forme qu'exige cette tâche et ne mentionnez que ce que l'utilisateur a besoin de savoir.
