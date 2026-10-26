# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · [Español](README.es.md) · **Français** · [Deutsch](README.de.md) · [Português (Brasil)](README.pt-BR.md)

Reader's Ear (`readers-ear`) est une compétence pour agents ([Agent Skill](https://agentskills.io)) qui amène un agent d'IA à réviser un texte, dans n'importe quelle langue et n'importe quel genre, jusqu'à ce qu'il paraisse naturel au lecteur auquel il est destiné.

## Pourquoi

La plupart des compétences de type « humanizer » s'appuient sur des règles : des listes de mots et de tournures qui sonnent « IA ». Cela a trois inconvénients :

- Les règles sont le plus souvent écrites pour une seule langue et ne fonctionnent pas dans les autres.
- Des règles figées imposent des choix inadaptés à certains usages.
- À mesure que les modèles progressent, les règles finissent par les brider.

Cette compétence prend le parti inverse. Elle part du principe que l'IA est déjà assez douée pour distinguer un bon texte d'un mauvais dans n'importe quelle langue, et que ce qui lui manque, ce ne sont pas des règles, mais une méthode de travail. Elle ne contient donc que des principes valables dans toutes les langues : juger le texte du point de vue de son lecteur ; repérer des problèmes concrets en relisant le texte, structure d'abord ; corriger chacun à la bonne échelle, du mot à la structure d'ensemble ; et s'arrêter quand il ne reste plus de problème concret. Le reste est laissé au modèle : un meilleur modèle donne de meilleurs résultats.

## Ce qu'elle fait

- **Révision standard** : relit le texte comme le ferait son lecteur, en examinant la structure avant les phrases, et corrige les problèmes concrets qu'elle repère. Quand c'est la structure qui pèche, plutôt que de peaufiner les phrases, elle dresse la liste de ce que le texte doit transmettre, reconstruit à partir de cette liste la partie concernée ou le texte entier, et vérifie qu'aucun fait ni aucune idée ne s'est perdu en route. Elle s'arrête quand il ne reste plus de problème, si bien qu'un texte déjà bon ressort presque inchangé. L'effort est proportionné à la longueur et aux enjeux du texte. Vous recevez le texte final, les éventuels points qu'elle a signalés plutôt que corrigés et, si elle a restructuré le texte, une brève explication.
- **Révision approfondie** (uniquement sur demande, car elle prend bien plus de temps et de tokens) : avant que l'agent se forge son propre avis sur le texte, deux nouvelles instances d'IA qui n'ont pas vu votre conversation, par exemple des sous-agents, travaillent en parallèle. L'une cherche sur le Web des textes du même genre et destinés au même usage, sans voir le vôtre, et résume la manière dont ils sont écrits. L'autre ne lit que votre texte et une note sur son lectorat et son objectif, puis signale les passages où elle bute. L'agent cherche ensuite les problèmes à la lumière de ces deux comptes rendus, vérifie les formulations clés et les faits, puis révise le texte. Il vous indique enfin ce qu'il a consulté et les étapes qu'il n'a pas pu réaliser. Les références (dictionnaires, corpus, documents d'institutions publiques et de grandes entreprises, etc.) doivent être rédigées à l'origine dans la langue du texte, et leur formulation doit avoir été vérifiée par une personne ou une organisation qui en assume la responsabilité ; pour le choix des tournures, les textes antérieurs à la diffusion de l'IA générative sont privilégiés. Les traductions ne servent jamais de références, car elles peuvent garder les tournures de leur langue d'origine.
- **Portée** : elle ne révise d'elle-même que les textes que l'agent rédige pour d'autres personnes. Là où elle peut enregistrer ce réglage, elle vous demande une seule fois si elle doit plutôt s'appliquer à tout ce que l'agent rédige, et enregistre votre réponse là où les sessions futures la chargeront.

## Installation

Choisissez la méthode selon l'endroit où vous utilisez la skill.

| Où vous l'utilisez | Méthode recommandée |
|---|---|
| Claude Code sur votre propre machine | [Plugin](#claude-code) depuis ce dépôt |
| claude.ai, Claude Desktop, Cowork ou Claude Code sur le web | [Import d'un ZIP](#claudeai-claude-desktop-et-cowork) sur votre compte claude.ai |
| Codex, Cursor, Gemini CLI, GitHub Copilot et autres agents | [`npx skills`](#autres-agents) |

Si vous utilisez à la fois claude.ai et Claude Code, l'import du ZIP suffit pour les deux, car Claude Code charge les compétences de votre compte claude.ai quand vous vous connectez avec ce compte. N'installez pas le plugin en plus : Claude Code en chargerait deux copies.

### Claude Code

Exécutez dans une session Claude Code :

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

La première commande ajoute ce dépôt comme marketplace de plugins ; la seconde installe le plugin `readers-ear` depuis cette marketplace (la marketplace et le plugin portent le même nom). Avec Claude Code 2.1.275 ou version ultérieure, une seule commande fait les deux : `/plugin install readers-ear --marketplace motestream/readers-ear`.

- **Mise à jour** : exécutez `/plugin marketplace update readers-ear`, ou activez la mise à jour automatique de cette marketplace sous **Marketplaces** dans `/plugin`.
- **Partage avec une équipe** : dans le dépôt de votre projet, exécutez `claude plugin marketplace add motestream/readers-ear --scope project` et commitez le fichier `.claude/settings.json` que cette commande écrit. Les membres de l'équipe ont alors accès à la marketplace et peuvent installer le plugin depuis celle-ci, à condition d'accepter de faire confiance au dossier du projet quand Claude Code le leur demande.
- **Sessions cloud** (Claude Code sur le web) : elles ne chargent pas les plugins installés sur votre propre machine. Importez plutôt la compétence sur claude.ai (section suivante), ou copiez `plugin/skills/readers-ear/` dans le dossier `.claude/skills/` de votre projet et commitez-le.

### claude.ai, Claude Desktop et Cowork

Les libellés cités ci-dessous sont ceux de l'interface en anglais.

1. Vérifiez que l'exécution de code est activée. Avec les offres Free, Pro et Max, le réglage se trouve dans **Settings > Capabilities** ; avec les offres Team et Enterprise, c'est un propriétaire de l'organisation qui l'active, en même temps que la fonctionnalité Skills, dans **Organization settings > Plugins & skills**.
2. Téléchargez ce dépôt et compressez le dossier `plugin/skills/readers-ear` en ZIP, de sorte que le ZIP contienne `readers-ear/SKILL.md`. Le dossier doit garder le nom `readers-ear`.
3. Sur claude.ai, ouvrez **Customize > Skills**, sélectionnez **+**, puis **Create skill** > **Upload a skill**, et choisissez le ZIP.

La compétence est alors rattachée à votre compte : Claude Desktop et Cowork l'utilisent aussi. Claude Code (2.1.273 ou version ultérieure) la charge également, sessions cloud comprises, lorsque vous vous connectez avec le même compte. Pour la mettre à jour, supprimez l'ancienne version dans **Customize > Skills** et importez le nouveau ZIP. Les propriétaires d'organisations Team et Enterprise peuvent déployer la compétence pour tous les membres.

### Autres agents

```
npx skills add motestream/readers-ear -g
```

`-g` l'installe pour votre compte utilisateur ; sans cette option, elle s'installe dans le projet courant. La commande détecte vos agents et demande pour lesquels l'installer ; pour en désigner un, ajoutez `-a`, comme dans `-a codex`. Pour la mettre à jour, exécutez `npx skills update`.

Avec GitHub CLI 2.90 ou version ultérieure (`gh skill` est en préversion), vous pouvez exécuter à la place `gh skill install motestream/readers-ear readers-ear --scope user`. Cette commande demande pour quel agent installer la compétence ; vous pouvez aussi en désigner un avec `--agent`. Pour la mettre à jour, exécutez `gh skill update`.

Pour l'installer à la main, copiez `plugin/skills/readers-ear/` dans le répertoire de compétences de votre agent, par exemple `~/.claude/skills/` pour Claude Code.

## Utilisation

- La compétence se déclenche d'elle-même quand l'agent rédige un texte destiné à d'autres personnes. Vous pouvez aussi la solliciter directement (« rends ce texte plus naturel ») ou l'appeler par son nom : `/readers-ear`, ou `/readers-ear:readers-ear` si elle est installée comme plugin Claude Code.
- Pour une révision approfondie, demandez-la explicitement (« prends ton temps et révise ce texte avec soin »).
- Quand vous lui demandez de réviser votre texte, elle peut en reconstruire la structure si c'est là que se situe le problème. Pour garder la structure et ne modifier que des détails, précisez-le (« corrige seulement les fautes de frappe ») ; elle signale alors les problèmes de structure sans les corriger.
- La première fois qu'elle s'exécute dans un environnement où elle peut enregistrer votre réponse, elle demande une seule fois s'il faut réviser tout ce que l'agent rédige ou seulement les textes destinés à d'autres personnes. Pour changer de portée plus tard, il suffit de le demander. Si vous changez de portée dans un environnement où le réglage ne peut pas être enregistré, la compétence l'applique uniquement à la conversation en cours et vous donne une phrase à ajouter à vos propres instructions pour que les sessions suivantes en tiennent compte.
- **Ce qu'elle écrit en dehors de la conversation** : uniquement quand vous choisissez ou modifiez la portée, la compétence enregistre une phrase dans vos instructions personnelles ou dans la mémoire de votre compte (par exemple votre `CLAUDE.md` au niveau utilisateur) et vous indique où. Hormis cette phrase, elle n'écrit que dans le texte sur lequel vous travaillez.

## Traductions

L'agent ne charge que le fichier [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md) anglais. Les traductions sont destinées aux lecteurs humains ; en cas de divergence, la version anglaise fait foi.

| Langue | README | Instructions de la compétence |
|---|---|---|
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## Essayer la compétence

Avant de vous fier à la compétence, essayez-la sur vos propres textes :

- Comparez les résultats obtenus avec et sans la compétence sur le même modèle, idéalement dans plusieurs langues et dans des genres qui ont leurs formules consacrées, comme l'e-mail professionnel, les clauses contractuelles et les textes d'interface.
- Donnez-lui un texte déjà bien écrit. Il devrait ressortir presque inchangé.
- Donnez-lui un texte dont le fond est solide mais la structure bancale, par exemple un rapport dont la conclusion est noyée dans le corps du texte, et demandez-lui de le réviser. Elle devrait reconstruire la structure en conservant tous les faits.
- Pendant le travail de programmation, vérifiez qu'elle peaufine les messages de commit, les descriptions de PR et la documentation que l'agent rédige, sans toucher aux textes existants écrits par d'autres.

## Contribuer

- Quand vous modifiez `SKILL.md` ou le README anglais, mettez à jour les traductions correspondantes dans le même commit, y compris la date en tête de chaque traduction de la compétence.
- Testez les modifications de `SKILL.md` dans au moins trois langues, dont une peu représentée dans les données d'entraînement, et avec chaque modèle que vous comptez prendre en charge. Vérifiez aussi comment la compétence gère la question sur la portée et l'enregistrement de la réponse lors d'une exécution non interactive (`claude -p`) et dans une session cloud.

## Licence

Ce projet est distribué sous la [licence MIT](../LICENSE).
