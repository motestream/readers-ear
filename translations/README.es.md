# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · **Español** · [Français](README.fr.md) · [Deutsch](README.de.md) · [Português (Brasil)](README.pt-BR.md)

Reader's Ear es una [Agent Skill](https://agentskills.io) que hace que un agente de IA escriba y revise textos, en cualquier idioma y género, de modo que le resulten naturales a su destinatario. En lugar de listas de palabras que evitar, le da al agente una forma de trabajar. Puedes instalarla en Claude (Claude Code, claude.ai, Claude Desktop y Cowork) y en otros agentes, como Codex, Cursor, Gemini CLI y GitHub Copilot.

## Por qué un método y no reglas

Muchas skills de tipo «humanizer» se basan en reglas: listas de palabras y patrones que suenan a IA. Las reglas tienen inconvenientes:

- Suelen estar escritas para un solo idioma y no sirven para otros.
- Imponen decisiones que son erróneas para algunos fines, como prohibir una expresión imprescindible en un contrato o en un correo comercial.
- Ponen un techo: por mucho que mejoren los modelos, el resultado no puede ser mejor que las reglas.

Reader's Ear parte de la premisa de que el modelo ya sabe distinguir un buen texto de uno malo en cualquier idioma, y de que lo que le falta no son reglas, sino una forma de trabajar. Por eso la skill solo aporta un método que funciona en todos los idiomas y deja el criterio en manos del modelo, así que un modelo mejor da mejores resultados.

## Qué hace

Las instrucciones completas están en [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md) (traducción al español: [`SKILL.es.md`](SKILL.es.md)). En resumen:

- **Escritura.** Cuando el agente escribe un texto nuevo, primero averigua quién lo va a leer, qué sabe ya y para qué lo lee, y escribe para ese lector desde el primer borrador. Después lee el borrador una vez como ese lector y corrige lo que encuentra.
- **Revisión.** Al revisar, el agente lee el texto como lo leería su destinatario y corrige solo problemas concretos, estén donde estén, desde una sola palabra hasta la estructura del texto entero. Conserva tus datos, tus ideas principales y tu voz, y te devuelve casi sin cambios un texto que ya es bueno. Los errores factuales y los problemas que van más allá de lo que pediste los señala en lugar de corregirlos.
- **Problemas fáciles de pasar por alto.** Tanto al escribir como al revisar, el agente busca en particular huellas de otros idiomas, como un orden de palabras o un formato de fecha calcados, y la dependencia de un contexto que el lector no ha visto, como la conversación del agente contigo o los nombres que les puso a las cosas mientras trabajaba.
- **Modo minucioso.** Es una forma de trabajar más lenta y exhaustiva que incorpora opiniones externas. Este modo solo se usa si lo pides, porque lleva mucho más tiempo y consume muchos más tokens. Antes de que el agente juzgue el texto por sí mismo, lo ayudan dos instancias nuevas de IA (por ejemplo, subagentes): una reúne textos de referencia del mismo género sin ver el tuyo, y la otra lo lee en frío, como lo leería su destinatario al verlo por primera vez. Después, el agente contrasta la redacción y los datos clave con fuentes escritas originalmente en el idioma del texto (no traducciones) y revisa el texto. Te dice qué consultó y si se saltó algún paso.
- **Alcance.** De forma predeterminada, la skill actúa por iniciativa propia en los textos que el agente escribe para otras personas y en sus informes para ti: la respuesta final a una petición en la que ha trabajado y los documentos que prepara para que los leas. Puedes ampliar el alcance a todo lo que escribe el agente o limitarlo a los textos para otras personas (consulta la sección Uso).

## Confianza

Reader's Ear consta solo de instrucciones, sin scripts, hooks ni servidores MCP. Aparte del texto con el que trabaja, lo único que escribe es una frase que registra el alcance que elegiste. Cuando eliges o cambias el alcance, o dejas sin responder la pregunta que te hace el agente al respecto, la skill guarda esa frase en tu archivo de instrucciones personal (por ejemplo, un `CLAUDE.md` a nivel de usuario) o en la memoria de tu cuenta, y te dice dónde.

En el modo minucioso, el agente además pone en marcha instancias nuevas de IA, como subagentes, y busca y lee textos de referencia y otras fuentes, como páginas web. En sus búsquedas usa términos, nombres y frases cortas, no pasajes de tu texto.

## Instalación

Si usas tanto claude.ai como Claude Code, ten en cuenta esto antes de nada: Claude Code carga las skills de tu cuenta de claude.ai en las sesiones en la nube y, a partir de la versión 2.1.273, en las sesiones de terminal en las que te hayas identificado con esa cuenta mediante `/login`. Si usas Claude Code así, basta con subir la skill a claude.ai en un ZIP; si además instalas el plugin, Claude Code cargará la skill dos veces.

Si no es tu caso, elige el método según dónde uses el agente:

| Dónde usas el agente | Método recomendado |
| --- | --- |
| Claude Code en tu propio equipo | [Plugin de Claude Code](#plugin-de-claude-code) |
| claude.ai, Claude Desktop, Cowork o Claude Code en la web | [Subir un ZIP a tu cuenta de claude.ai](#claudeai-claude-desktop-y-cowork) |
| Codex, Cursor, Gemini CLI, GitHub Copilot y otros agentes | [`npx skills`](#otros-agentes) |

### Plugin de Claude Code

En una sesión de Claude Code, ejecuta:

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

El primer comando añade este repositorio como marketplace de plugins. El segundo instala desde él el plugin `readers-ear`; el marketplace y el plugin se llaman igual.

En Claude Code 2.1.275 o posterior, un solo comando hace las dos cosas:

```
/plugin install readers-ear --marketplace motestream/readers-ear
```

**Para actualizar**, ejecuta `/plugin marketplace update readers-ear` o activa la actualización automática de este marketplace en **Marketplaces**, dentro de `/plugin`.

**Para compartirlo con un equipo**, abre una ventana de terminal en la raíz del repositorio del proyecto y ejecuta:

```sh
claude plugin marketplace add motestream/readers-ear --scope project
```

Después haz commit del archivo `.claude/settings.json` que genera. Cuando Claude Code pregunte a tus compañeros si confían en la carpeta del proyecto, quienes acepten tendrán el marketplace y podrán instalar el plugin desde él.

**Las sesiones en la nube** (Claude Code en la web) no cargan los plugins instalados en tu propio equipo. Para esas sesiones, sube la skill a claude.ai o copia la carpeta `plugin/skills/readers-ear/` de un clon o de una descarga en ZIP de este repositorio en la carpeta `.claude/skills/` del proyecto, y haz commit de ella.

### claude.ai, Claude Desktop y Cowork

1. Asegúrate de que la ejecución de código esté activada, porque las skills la necesitan. En los planes Free, Pro y Max, está en **Settings > Capabilities** (Configuración > Capacidades). En los planes Team, la ejecución de código y las skills están activadas de forma predeterminada para la organización. En los planes Enterprise, un propietario se asegura de que ambas estén activadas en **Organization settings > Plugins & skills** (Configuración de la organización > Complementos y habilidades), en la pestaña **Policy** (Política).
2. Descarga este repositorio como ZIP (en GitHub, **Code** > **Download ZIP**) y descomprímelo.
3. Comprime la carpeta `plugin/skills/readers-ear` en un ZIP nuevo, de modo que el ZIP contenga una carpeta `readers-ear` con `SKILL.md` dentro. La carpeta debe seguir llamándose `readers-ear`.
4. En claude.ai, abre **Customize > Skills** (Personalizar > Habilidades), selecciona **+**, luego **Create skill** (Crear habilidad) > **Upload a skill** (Cargar una habilidad) y elige el ZIP.

A partir de ese momento, la skill pertenece a tu cuenta, así que también la usan Claude Desktop y Cowork, al igual que Claude Code en las condiciones descritas al principio de [Instalación](#instalación). Los propietarios de organizaciones Enterprise también pueden subir la skill para ponerla a disposición de todos los miembros.

**Para actualizar**, elimina la versión anterior en **Customize > Skills** y sube el ZIP nuevo.

### Otros agentes

Este método requiere Node.js. Ejecuta:

```sh
npx skills add motestream/readers-ear -g
```

`-g` instala la skill de forma global, para todos tus proyectos; sin esta opción, la skill se instala solo en el proyecto actual. El comando detecta los agentes instalados en tu equipo y te pregunta para cuáles instalarla. Para elegir uno de antemano, añade `-a`, como en `-a codex`.

**Para actualizar**, ejecuta `npx skills update`.

**Con GitHub CLI 2.90 o posterior**, puedes usar en su lugar `gh skill`, que está en versión preliminar:

```sh
gh skill install motestream/readers-ear readers-ear --scope user
```

El comando te pregunta para qué agente instalarla, o puedes indicar uno con `--agent`. Para actualizar, ejecuta `gh skill update`.

**Para instalarla a mano**, copia la carpeta `plugin/skills/readers-ear/` de un clon o de una descarga en ZIP de este repositorio en el directorio de skills del agente, como `~/.claude/skills/` en Claude Code.

## Uso

Reader's Ear se activa sola cuando el agente escribe textos para otras personas o informes para ti. También puedes pedirla con tus propias palabras, por ejemplo: «Haz que esto suene natural». Otra opción es invocarla por su nombre con `/readers-ear` (`/readers-ear:readers-ear` si la instalaste como plugin de Claude Code).

**Modo minucioso.** El agente solo lo usa cuando lo pides expresamente, por ejemplo: «Tómate tu tiempo y revisa esto a fondo» o «Tómate tu tiempo y escribe esto con cuidado». Para que lo use siempre, indícalo en tus instrucciones guardadas, como un `CLAUDE.md`.

**Limitar los cambios.** Dile al agente a qué debe limitarse, por ejemplo: «Corrige solo las erratas». En ese caso, el agente señala los demás problemas en lugar de corregirlos.

**Alcance.** El alcance predeterminado abarca los textos para otras personas y los informes del agente para ti: su respuesta final a una petición para la que tuvo que trabajar, como leer archivos o ejecutar comandos, y los documentos que prepara para que los leas. No abarca lo que el agente escribe mientras trabaja en la respuesta final ni las respuestas breves que puede dar a partir solo de la conversación. En una sesión interactiva en la que se pueda guardar la configuración, el agente pregunta una sola vez, después de entregar el primer texto dentro del alcance predeterminado, si quieres mantener el alcance predeterminado, aplicar la skill a todo lo que escribe o limitarla a los textos para otras personas. Si no respondes, mantiene el alcance predeterminado y lo guarda, así que no vuelve a preguntar. Para cambiar el alcance más adelante, pídeselo al agente. Donde no se puede guardar la configuración, el agente no pregunta; si allí le pides que cambie el alcance, el cambio solo se aplica a la conversación actual, y el agente te da una frase para que la añadas a tus propias instrucciones y las sesiones posteriores la tengan en cuenta.

## Cómo probarla

Antes de confiar en ella, haz estas pruebas:

- Compara los resultados con y sin la skill en el mismo modelo, idealmente en varios idiomas y en géneros con fórmulas fijas, como correos comerciales, cláusulas de contratos y textos de interfaz.
- Pídele al agente que escriba algo para otras personas a partir de tus notas. Lo que entregue debería resultarle natural a su destinatario sin necesidad de otra ronda de correcciones.
- Dale un texto que ya esté bien escrito y pídele que lo revise. Debería devolverlo casi sin cambios.
- Dale un texto con datos correctos pero en un orden difícil de seguir y pídele que lo revise. Debería reorganizarlo y conservar todos los datos.
- Durante el trabajo de programación, comprueba que mejora los mensajes de commit, las descripciones de PR y la documentación que escribe el agente, y que deja como están los textos ya existentes de otras personas.
- Después de una tarea de varios pasos, comprueba que la respuesta final del agente usa palabras que conoces en lugar de nombres que se inventó mientras trabajaba, y que no es más larga de lo necesario.

## Traducciones

El agente solo carga el [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md) en inglés. Las traducciones son para lectores humanos. Si una traducción difiere del inglés, prevalece la versión inglesa.

| Idioma | README | Instrucciones de la skill |
| --- | --- | --- |
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## Contribuir

- Cuando cambien `SKILL.md` o el README en inglés, actualiza en el mismo commit las traducciones correspondientes, incluida la fecha que aparece al principio de cada traducción de la skill.
- Prueba los cambios en `SKILL.md` en al menos tres idiomas, uno de ellos con pocos datos de entrenamiento, y con cada modelo que admita el proyecto. Comprueba también cómo se comportan la pregunta sobre el alcance y el guardado de la respuesta en una ejecución no interactiva (`claude -p`) y en una sesión en la nube.

## Licencia

Reader's Ear se publica bajo la [licencia MIT](../LICENSE).
