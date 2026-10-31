# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · [Español](README.es.md) · **Français** · [Deutsch](README.de.md) · [Português (Brasil)](README.pt-BR.md)

Reader's Ear est une compétence pour agents ([Agent Skill](https://agentskills.io)) qui amène un agent d'IA à rédiger et à réviser des textes, dans n'importe quelle langue et n'importe quel genre, de façon qu'ils paraissent naturels au lecteur auquel ils sont destinés. Plutôt que des listes de mots à éviter, elle donne à l'agent une méthode de travail. Vous pouvez l'installer dans Claude (Claude Code, claude.ai, Claude Desktop et Cowork) et dans d'autres agents comme Codex, Cursor, Gemini CLI et GitHub Copilot.

## Pourquoi une méthode plutôt que des règles

De nombreuses compétences de type « humanizer » s'appuient sur des règles : des listes de mots et de tournures typiques des textes d'IA. Les règles présentent des inconvénients :

- Elles sont généralement écrites pour une seule langue et ne se transposent pas aux autres.
- Elles imposent des choix qui ne conviennent pas à certains usages, comme l'interdiction d'une formule qu'exige un contrat ou un e-mail professionnel.
- Elles plafonnent les résultats : les modèles ont beau progresser, le texte produit ne peut pas être meilleur que les règles.

Reader's Ear part du principe que le modèle sait déjà distinguer un bon texte d'un mauvais dans n'importe quelle langue, et qu'il lui manque non pas des règles, mais une méthode de travail. La compétence ne fournit donc qu'une méthode valable dans toutes les langues et laisse le jugement au modèle, ce qui signifie qu'un meilleur modèle donne de meilleurs résultats.

## Ce que fait Reader's Ear

Les instructions complètes se trouvent dans [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md) (traduction française : [`SKILL.fr.md`](SKILL.fr.md)). En résumé :

- **Rédaction.** Quand l'agent rédige un nouveau texte, il détermine d'abord qui le lira, ce que ce lecteur sait déjà et dans quel but il le lit, puis il écrit pour lui dès le premier jet. Il lit ce premier jet une fois en se mettant à la place de ce lecteur et corrige les problèmes qu'il y trouve.
- **Révision.** Il lit le texte comme le ferait son lecteur et ne corrige que des problèmes concrets, où qu'ils se trouvent, du simple mot à la structure du texte entier. Il conserve les faits, les idées principales et la voix de votre texte, et laisse presque intact un texte déjà bon. Il signale, sans les corriger, les erreurs factuelles et les problèmes qui dépassent ce que vous avez demandé.
- **Problèmes qui passent facilement inaperçus.** En rédaction comme en révision, il recherche en particulier les traces d'autres langues, comme un ordre des mots ou un format de date repris d'une autre langue, et les passages qui supposent un contexte que le lecteur n'a pas vu, comme la conversation de l'agent avec vous ou les noms qu'il a donnés à certains éléments en cours de travail.
- **Mode approfondi.** Une méthode de travail plus lente et plus minutieuse, qui fait appel à des regards extérieurs ; elle n'est employée que sur demande, car elle coûte bien plus cher en temps et en tokens. Avant que l'agent porte son propre jugement sur le texte, deux nouvelles instances d'IA (par exemple des sous-agents) lui viennent en aide : l'une rassemble des textes de référence du même genre sans voir le vôtre, l'autre lit le texte à froid. L'agent vérifie ensuite les formulations et les faits essentiels dans des sources rédigées à l'origine dans la langue du texte (et non dans des traductions), puis révise le texte. Il vous indique ce qu'il a consulté et les éventuelles étapes qu'il a sautées.
- **Périmètre.** Par défaut, la compétence intervient d'elle-même sur les textes que l'agent rédige pour d'autres personnes et sur les comptes rendus qu'il vous adresse : la réponse finale à une demande sur laquelle il a travaillé et les documents qu'il prépare à votre intention. Vous pouvez l'étendre à tout ce que rédige l'agent, ou la limiter aux textes destinés à d'autres personnes (voir « Utilisation »).

## Sécurité et confidentialité

Reader's Ear ne contient que des instructions : aucun script, aucun hook, aucun serveur MCP. En dehors du texte traité, la compétence n'écrit qu'une chose : une phrase qui enregistre votre choix de périmètre. Quand vous choisissez ou modifiez le périmètre, ou que vous laissez sans réponse la question que l'agent vous pose à ce sujet, celui-ci enregistre cette phrase dans votre fichier d'instructions personnelles (par exemple un fichier `CLAUDE.md` au niveau utilisateur) ou dans la mémoire de votre compte, et vous indique où.

En mode approfondi, l'agent lance également de nouvelles instances d'IA, comme des sous-agents, et il recherche et lit des textes de référence et d'autres sources, par exemple des pages web. Pour ses recherches, il utilise des termes, des noms et de courtes expressions, et non des passages de votre texte.

## Installation

Si vous utilisez à la fois claude.ai et Claude Code, vérifiez d'abord ce point : Claude Code charge les compétences de votre compte claude.ai dans les sessions cloud et, à partir de la version 2.1.273, dans les sessions de terminal où vous vous êtes connecté à ce compte avec `/login`. Si c'est ainsi que vous utilisez Claude Code, l'import d'un ZIP sur votre compte claude.ai suffit, et installer aussi le plugin amènerait Claude Code à charger la compétence deux fois.

Sinon, choisissez la méthode adaptée à l'endroit où vous utilisez l'agent :

| Où vous l'utilisez | Méthode recommandée |
| --- | --- |
| Claude Code sur votre propre machine | [Plugin Claude Code](#plugin-claude-code) |
| claude.ai, Claude Desktop, Cowork ou Claude Code sur le web | [Import d'un ZIP sur votre compte claude.ai](#claudeai-claude-desktop-et-cowork) |
| Codex, Cursor, Gemini CLI, GitHub Copilot et autres agents | [`npx skills`](#autres-agents) |

### Plugin Claude Code

Dans une session Claude Code, exécutez :

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

La première commande ajoute ce dépôt comme marketplace de plugins. La seconde installe le plugin `readers-ear` depuis cette marketplace ; la marketplace et le plugin portent le même nom.

À partir de Claude Code 2.1.275, une seule commande fait les deux :

```
/plugin install readers-ear --marketplace motestream/readers-ear
```

**Pour mettre à jour le plugin**, exécutez `/plugin marketplace update readers-ear`, ou activez la mise à jour automatique de cette marketplace dans l'onglet **Marketplaces** de `/plugin`.

**Pour partager le plugin avec une équipe**, ouvrez un terminal à la racine du dépôt du projet et exécutez :

```sh
claude plugin marketplace add motestream/readers-ear --scope project
```

Commitez ensuite le fichier `.claude/settings.json` que cette commande écrit. Lorsque Claude Code demande aux membres de l'équipe s'ils font confiance au dossier du projet, ceux qui acceptent obtiennent la marketplace et peuvent installer le plugin depuis celle-ci.

**Les sessions cloud** (Claude Code sur le web) ne chargent pas les plugins installés sur votre propre machine. Pour ces sessions, importez plutôt la compétence sur claude.ai, ou copiez le dossier `plugin/skills/readers-ear/` (tiré d'un clone ou d'un téléchargement ZIP de ce dépôt) dans le dossier `.claude/skills/` du projet, puis commitez-le.

### claude.ai, Claude Desktop et Cowork

1. Assurez-vous que l'exécution de code est activée, car les compétences en ont besoin. Avec les offres Free, Pro et Max, le réglage se trouve dans **Settings > Capabilities** (dans l'interface en français : **Paramètres > Capacités**). Avec l'offre Team, l'exécution de code et les compétences sont activées par défaut pour l'organisation. Avec l'offre Enterprise, un propriétaire de l'organisation vérifie que les deux sont activées dans **Organization settings > Plugins & skills** (**Paramètres de l'organisation > Plugins et compétences**), onglet **Policy** (**Politique**).
2. Téléchargez ce dépôt au format ZIP (sur GitHub, **Code** > **Download ZIP**) et décompressez-le.
3. Compressez le dossier `plugin/skills/readers-ear` dans un nouveau fichier ZIP, de sorte que celui-ci contienne un dossier `readers-ear` avec `SKILL.md` à l'intérieur. Le dossier doit garder le nom `readers-ear`.
4. Sur claude.ai, ouvrez **Customize > Skills** (**Personnaliser > Compétences**), sélectionnez le bouton **+**, puis **Create skill** > **Upload a skill** (**+ Créer une compétence** > **Télécharger une compétence**), et choisissez le fichier ZIP.

La compétence est alors rattachée à votre compte : Claude Desktop et Cowork l'utilisent donc aussi, de même que Claude Code dans les conditions décrites au début de la section [Installation](#installation). Les propriétaires d'organisations Enterprise peuvent également importer la compétence pour la déployer auprès de tous les membres.

**Pour mettre à jour la compétence**, supprimez l'ancienne version dans **Customize > Skills** (**Personnaliser > Compétences**) et importez le nouveau fichier ZIP.

### Autres agents

Cette méthode nécessite Node.js. Exécutez :

```sh
npx skills add motestream/readers-ear -g
```

L'option `-g` installe la compétence de façon globale, pour tous vos projets ; sans elle, la compétence n'est installée que dans le projet courant. La commande détecte les agents installés sur votre machine et vous demande pour lesquels installer la compétence. Pour en choisir un à l'avance, ajoutez `-a`, par exemple `-a codex`.

**Pour mettre à jour la compétence**, exécutez `npx skills update`.

**Avec GitHub CLI 2.90 ou une version ultérieure**, vous pouvez utiliser à la place `gh skill`, actuellement en préversion :

```sh
gh skill install motestream/readers-ear readers-ear --scope user
```

Cette commande vous demande pour quel agent installer la compétence ; vous pouvez aussi en désigner un avec `--agent`. Pour la mettre à jour, exécutez `gh skill update`.

**Pour installer la compétence à la main**, copiez le dossier `plugin/skills/readers-ear/` (tiré d'un clone ou d'un téléchargement ZIP de ce dépôt) dans le répertoire des compétences de l'agent, par exemple `~/.claude/skills/` pour Claude Code.

## Utilisation

Reader's Ear se déclenche automatiquement quand l'agent rédige un texte destiné à d'autres personnes ou vous rend compte de son travail. Vous pouvez aussi la solliciter avec vos propres mots, par exemple « Rends ce texte plus naturel », ou l'appeler par son nom avec `/readers-ear` (`/readers-ear:readers-ear` si vous l'avez installée comme plugin Claude Code).

**Mode approfondi.** L'agent ne l'utilise que si vous le demandez explicitement, par exemple : « Prends ton temps et révise ce texte avec soin » ou « Prends ton temps et rédige ce texte avec soin ». Pour qu'il l'utilise à chaque fois, indiquez-le dans vos instructions enregistrées, par exemple dans un fichier `CLAUDE.md`.

**Limiter les modifications.** Indiquez à l'agent à quoi se limiter, par exemple : « Corrige seulement les fautes de frappe ». Il signale alors les autres problèmes au lieu de les corriger.

**Périmètre.** Le périmètre par défaut couvre les textes destinés à d'autres personnes et les comptes rendus que l'agent vous adresse : sa réponse finale à une demande pour laquelle il a dû travailler, par exemple en lisant des fichiers ou en exécutant des commandes, et les documents qu'il prépare à votre intention. Il ne couvre ni ce que l'agent écrit en travaillant à la réponse finale, ni les réponses courtes qu'il peut donner à partir de la seule conversation. Dans une session interactive où les réglages peuvent être enregistrés, l'agent demande une seule fois, après avoir livré un premier texte relevant du périmètre par défaut, s'il faut conserver ce périmètre, appliquer la compétence à tout ce qu'il rédige ou la limiter aux textes destinés à d'autres personnes. Si vous ne répondez pas, il conserve le périmètre par défaut et enregistre ce choix, si bien qu'il ne reposera pas la question. Pour changer de périmètre plus tard, demandez-le à l'agent. Là où les réglages ne peuvent pas être enregistrés, l'agent ne pose pas la question ; si vous lui demandez de changer de périmètre dans un tel environnement, le changement ne s'applique qu'à la conversation en cours, et l'agent vous donne une phrase à ajouter à vos propres instructions pour que les sessions suivantes en tiennent compte.

## Essayer la compétence

Avant de vous fier à la compétence, faites les essais suivants :

- Comparez les résultats obtenus avec et sans la compétence sur le même modèle, idéalement dans plusieurs langues et dans des genres qui ont leurs formules consacrées, comme l'e-mail professionnel, les clauses contractuelles et les textes d'interface.
- Demandez à l'agent de rédiger, à partir de vos notes, un texte destiné à d'autres personnes. Le texte qu'il livre devrait convenir à son lecteur sans qu'il faille le retravailler.
- Donnez-lui un texte déjà bon et demandez-lui de le réviser. Le texte devrait ressortir presque inchangé.
- Donnez-lui un texte dont les faits sont exacts mais dont l'ordre est difficile à suivre, et demandez-lui de le réviser. L'agent devrait réorganiser le texte en conservant tous les faits.
- Pendant un travail de programmation, vérifiez que la compétence améliore les messages de commit, les descriptions de pull request et la documentation que rédige l'agent, et qu'elle ne touche pas aux textes existants écrits par d'autres.
- Après une tâche en plusieurs étapes, vérifiez que la réponse finale de l'agent emploie des mots que vous connaissez plutôt que des noms qu'il a inventés en cours de travail, et qu'elle n'est pas plus longue que nécessaire.

## Traductions

L'agent ne charge que le fichier anglais [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md). Les traductions sont destinées aux lecteurs humains. Si une traduction diffère de l'anglais, c'est la version anglaise qui fait foi.

| Langue | README | Instructions de la compétence |
| --- | --- | --- |
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## Contribution

- Quand `SKILL.md` ou le README anglais est modifié, mettez à jour les traductions correspondantes dans le même commit, y compris la date en tête de chaque traduction des instructions de la compétence.
- Testez les modifications de `SKILL.md` dans au moins trois langues, dont une langue peu représentée dans les données d'entraînement, et avec chaque modèle que le projet prend en charge. Vérifiez aussi le comportement de la question sur le périmètre et de l'enregistrement de la réponse lors d'une exécution non interactive (`claude -p`) et dans une session cloud.

## Licence

Reader's Ear est distribuée sous [licence MIT](../LICENSE).
