# readers-ear (traduction française)

> Cette traduction est fournie à titre indicatif. Les agents ne chargent que l'original anglais, [`plugin/skills/readers-ear/SKILL.md`](../plugin/skills/readers-ear/SKILL.md) ; en cas de divergence, la version anglaise fait foi. Traduction établie d'après la version anglaise du 25 octobre 2026.

```yaml
---
name: readers-ear
description: Révise un texte, de sa structure à sa formulation, quels que soient sa langue et son genre, pour qu'il paraisse naturel au lecteur auquel il est destiné. À utiliser chaque fois que vous rédigez un texte que liront d'autres personnes que l'utilisateur (e-mails, articles, documents, publications, diapositives, discours, fiction, traductions, textes d'interface), même si l'utilisateur ne demande pas de révision ; chaque fois que l'utilisateur demande de réviser ou de peaufiner un texte, ou de le rendre plus naturel ou moins « IA » ; enfin, pour tout texte si les instructions enregistrées par l'utilisateur le prévoient.
---
```

# Reader's Ear

Visez un texte qui se lise comme si quelqu'un qui maîtrise la langue et le genre de ce texte l'avait écrit pour le lecteur auquel il est destiné. La référence, c'est ce lecteur, pas des règles : ne travaillez pas à partir de listes de tournures ou de mots interdits, et gardez les formules consacrées qu'exigent le genre ou les conventions. Jugez le texte selon les normes de sa propre langue, et non selon celles de la langue de ces instructions (l'anglais, dans l'original) ni selon celles de la langue dans laquelle vous pensez. Les exemples et les guides de style fournis par l'utilisateur priment sur tout ce que disent ces instructions.

## Révision standard

Lisez le texte comme le découvrirait le lecteur auquel il est destiné. Examinez ensuite l'ensemble avant le détail : déterminez d'abord ce que le texte doit transmettre à ce lecteur, puis voyez si, selon les normes du genre, sa structure s'y prête (ce qui vient en premier, comment les parties sont regroupées et ordonnées, à quoi sert chacune) ; ne passez qu'ensuite aux paragraphes, aux phrases et aux mots. Des phrases soignées ne sauvent pas une structure qui ne fonctionne pas, et reconstruire la structure les modifiera de toute façon.

Ne modifiez que ce que vous pouvez désigner comme un problème concret : ce qui ferait buter le lecteur, lui ferait perdre le fil ou l'empêcherait de trouver ce dont il a besoin au moment où il en a besoin, ou ce que quelqu'un qui maîtrise cette langue et ce genre n'aurait pas écrit ainsi. Corrigez chaque problème au niveau où il se situe, du mot au texte entier ; parfois, la solution consiste à supprimer un passage. Retoucher les phrases une à une ne change rien à la structure. Quand le problème tient à la structure, dressez donc la liste de ce que le texte doit transmettre (ses faits, ses idées, son objectif), puis reconstruisez à partir de cette liste la partie concernée, ou le texte entier, dans l'ordre et sous la forme dont ce lecteur a besoin. Comparez ensuite le résultat à l'original pour repérer les faits ou les idées que la reconstruction aurait perdus ou modifiés, et les affirmations qu'elle aurait ajoutées. Ne gardez une modification que si elle améliore le texte, et arrêtez-vous quand vous ne pouvez plus désigner d'autre problème. Un texte déjà bon devrait ressortir presque inchangé. Proportionnez votre effort à la longueur et aux enjeux du texte.

Deux sortes de problèmes passent facilement inaperçues. La première est l'interférence d'autres langues que celle du texte, y compris de celles qui n'apparaissent ni dans ce qu'on vous a fourni ni dans votre raisonnement. Elle se manifeste par des calques dans l'ordre des mots, les tournures, les collocations, les expressions idiomatiques, la ponctuation et les guillemets, le format des nombres et des dates ou la façon de s'adresser à quelqu'un ; par des mots étrangers que ce lecteur n'emploierait pas ; par un mélange de systèmes d'écriture ou de variantes régionales d'orthographe ou de vocabulaire. La seconde est le recours à un contexte que le lecteur n'a jamais vu, comme votre conversation avec l'utilisateur.

Quel que soit le texte que vous révisez :

- Dans un texte que l'utilisateur vous soumet, préservez les faits, les idées et la voix de son auteur, et ne modifiez pas plus que la demande ne l'exige. Signalez les erreurs ou ambiguïtés qui touchent au sens plutôt que de les corriger. Une demande générale, comme celle de réviser ou de peaufiner le texte, ou de le rendre plus naturel, porte aussi sur sa structure ; une demande plus restreinte, comme celle de corriger les fautes de frappe ou de grammaire, ne la concerne pas : signalez alors les problèmes de structure plutôt que de les corriger. Une traduction garde la structure de l'original, sauf si l'utilisateur vous demande d'adapter cette structure.
- N'inventez ni faits, ni chiffres, ni citations pour rendre un texte plus concret ; signalez ce qui manque ou posez la question.
- Si vous doutez de votre jugement sur la langue ou le sujet, limitez vos modifications et dites-le.
- Livrez le texte final, ainsi que ce que l'utilisateur doit savoir, par exemple les points signalés plutôt que corrigés. Si vous avez restructuré un texte qu'il vous a soumis, indiquez en une ou deux phrases ce que vous avez changé et pourquoi. N'incluez ni vos notes de travail ni vos brouillons, sauf si on vous les demande.

## Révision approfondie

N'y procédez que si l'utilisateur demande explicitement une révision plus lente et plus minutieuse que d'habitude, car elle coûte bien plus de temps et de tokens. Elle ajoute à la révision standard des lectures extérieures, recueillies avant que vous vous soyez forgé votre propre opinion sur le texte, pour que celle-ci ne les oriente pas. Procédez dans cet ordre :

1. Avant de chercher vous-même des problèmes, ouvrez deux nouveaux contextes qui n'ont pas vu votre conversation, par exemple des sous-agents nouvellement créés (et non des copies de ce contexte) ; ils peuvent travailler en parallèle. Ne communiquez à aucun des deux vos propres remarques ou soupçons sur le texte.
   - Recherche de références : indiquez à ce contexte la langue du texte, son lectorat visé, son genre, son objectif en termes généraux et les critères ci-dessous, mais ne lui donnez pas le texte. Demandez-lui de trouver quelques textes du même genre et destinés au même usage qui respectent ces critères, de lire les pages elles-mêmes plutôt que les extraits affichés par le moteur de recherche, d'indiquer les pages utilisées et de résumer la manière dont ces textes sont écrits : structure, formules consacrées, longueur, registre et tout ce que le genre exige par ailleurs.
   - Lecture à froid : donnez à ce contexte uniquement le texte et une note sur son lectorat et son objectif. Demandez-lui de le lire comme le ferait ce lectorat et de signaler les passages où il bute ou perd le fil, ainsi que ce qu'il retient comme idée principale du texte.
2. Une fois les deux comptes rendus en main, lisez vous-même le texte et dressez la liste de ses problèmes.
3. Vérifiez ce qui compte le plus pour le lecteur ou ce dont vous êtes le moins sûr (orthographe, ponctuation, terminologie, faits, etc.) dans des sources actuelles qui font autorité, comme les dictionnaires, les ouvrages sur le bon usage et les pages officielles des organismes concernés.
4. Révisez comme pour la révision standard. Servez-vous des références comme d'un étalon pour mesurer le texte, non comme de formulations à recopier ; dans un texte que l'utilisateur vous a soumis, les faits, les idées et la voix de son auteur priment toujours.

Critères applicables aux sources des étapes 1 et 3 : utilisez des sources rédigées dans la langue du texte et dont la formulation a été vérifiée par une personne ou une organisation qui en assume la responsabilité.

- N'utilisez pas de traductions, aussi bonnes soient-elles, car elles peuvent garder les tournures de leur langue d'origine. Cela vaut aussi pour les versions traduites des pages des sites multilingues.
- Pour les tournures et les conventions du genre, utilisez des textes relevant du même genre et destinés au même usage, par exemple les pages rédigées dans cette langue par les institutions publiques, les grandes entreprises et les éditeurs de renom ; les écrits des auteurs reconnus du genre ; les extraits de corpus. Parmi ces textes, ceux qui sont antérieurs à la diffusion de l'IA générative (vers 2022) sont les plus sûrs ; les textes plus récents conviennent aussi quand un éditeur ou une institution en répond clairement.

Si vous ne pouvez pas ouvrir de nouveaux contextes, renoncez à la lecture à froid, cherchez et lisez vous-même les références avant de chercher des problèmes, puis reprenez à l'étape 2.

Indiquez brièvement à l'utilisateur ce que vous avez consulté et ce que cela a changé, et mentionnez toute étape que vous n'avez pas pu réaliser, comme les lectures dans de nouveaux contextes ou les recherches. Ne présentez jamais comme accomplie une étape que vous avez sautée.

## Portée

La portée ne détermine que ce que vous révisez de votre propre initiative ; vous révisez toujours ce que l'utilisateur vous demande de réviser. Il existe deux portées :

- A (par défaut) : les textes que vous rédigez et dont les lecteurs finaux sont d'autres personnes que l'utilisateur.
- B : tout texte que vous rédigez.

Si vos instructions ou votre mémoire ne fixent aucune portée, appliquez A et, après avoir livré le texte, demandez une seule fois à l'utilisateur s'il préfère B. Ne posez pas la question si l'utilisateur ne peut pas faire ce choix (par exemple, s'il est l'utilisateur final d'un produit conçu par un tiers), si vous fonctionnez en tant que sous-agent ou sans surveillance, ou s'il n'existe aucun emplacement approprié où enregistrer la réponse (voir ci-dessous).

Lorsque l'utilisateur répond, ou modifie la portée par la suite, enregistrez son choix sous la forme d'une phrase rédigée dans sa langue, qui nomme cette compétence (skill) et indique la portée (par exemple : « Utilisez la compétence readers-ear pour tout texte que vous rédigez. » ou « Utilisez la compétence readers-ear pour les textes que vous rédigez et que liront d'autres personnes. »). Enregistrez-la dans un emplacement personnel que chargent toutes les sessions futures, comme un fichier d'instructions au niveau utilisateur ou la mémoire du compte. N'utilisez ni fichiers partagés avec une équipe, ni mémoire limitée à un projet, ni emplacements où la phrase peut être enregistrée mais ne sera pas chargée à la session suivante, comme un environnement cloud jetable. Indiquez à l'utilisateur où vous l'avez enregistrée. S'il n'existe aucun emplacement de ce type, appliquez ce choix à cette conversation uniquement, dites-le, et donnez à l'utilisateur la phrase à coller dans ses propres instructions.
