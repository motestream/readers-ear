# Reader's Ear

[English](../README.md) · [日本語](README.ja.md) · [简体中文](README.zh-Hans.md) · [한국어](README.ko.md) · **Español** · [Français](README.fr.md) · [Deutsch](README.de.md) · [Português (Brasil)](README.pt-BR.md)

Reader's Ear (`readers-ear`) es una [Agent Skill](https://agentskills.io) que hace que un agente de IA revise un texto, en cualquier idioma y género, hasta que le resulte natural a su destinatario.

## Por qué

La mayoría de las skills de tipo "humanizer" se basan en reglas: listas de palabras y patrones que suenan a IA. Esto tiene tres inconvenientes:

- Las reglas suelen estar escritas para un solo idioma y no sirven en otros.
- Las reglas rígidas imponen decisiones que son erróneas para ciertos fines.
- A medida que mejoran los modelos, las reglas se convierten en un techo.

Esta skill adopta el enfoque contrario. Parte de la premisa de que la IA ya es lo bastante capaz como para distinguir un buen texto de uno malo en cualquier idioma, y de que lo que le falta no son reglas, sino una forma de trabajar. Por eso la skill solo contiene principios válidos en cualquier idioma: juzgar el texto desde el punto de vista de su lector, encontrar problemas concretos al releerlo empezando por la estructura, corregir cada uno en el nivel adecuado (desde una palabra hasta el texto entero) y detenerse cuando ya no queda ningún problema concreto. Todo lo demás queda en manos del modelo, así que un modelo mejor da mejores resultados.

## Qué hace

- **Revisión estándar**: lee el texto como lo haría su destinatario, mirando la estructura antes que las oraciones, y corrige solo los problemas concretos que puede identificar. Cuando lo que falla es la estructura, en lugar de pulir oraciones, hace una lista de lo que el texto tiene que transmitir, lo reconstruye a partir de ella y comprueba que no se haya perdido ningún dato ni ninguna idea. Se detiene cuando ya no encuentra ningún problema, así que un texto que ya es bueno te lo devuelve casi sin cambios. El esfuerzo depende de la extensión y la importancia del texto. Al final recibes el texto terminado y, si los hay, los puntos que la skill señaló en lugar de corregirlos, además de una breve explicación si cambió la estructura.
- **Revisión minuciosa** (solo cuando la pides, porque lleva mucho más tiempo y consume muchos más tokens): antes de que el agente se forme su propia opinión sobre el texto, dos instancias nuevas de IA que no han visto tu conversación (por ejemplo, subagentes) trabajan en paralelo. Una busca en la web textos del mismo género y con el mismo propósito, sin ver el tuyo, y resume cómo están escritos. La otra lee solo tu texto y una nota sobre su destinatario y su propósito, e indica dónde tropieza. Después, el agente busca los problemas con ambos informes delante, comprueba las expresiones clave y los datos, y corrige el texto. Por último, te cuenta qué consultó y qué pasos no pudo hacer. Las referencias, como diccionarios, corpus y documentos de instituciones públicas y grandes empresas, tienen que estar escritas originalmente en el idioma del texto, y su redacción tiene que haberla revisado y respaldado una persona o una organización; como modelos de redacción se prefieren los textos escritos antes de la difusión de la IA generativa. Nunca usa traducciones como referencia, porque pueden arrastrar los patrones de su idioma de origen.
- **Alcance**: por iniciativa propia, solo revisa los textos que el agente escribe para otras personas. Donde puede guardar la configuración, te pregunta una sola vez si debe abarcar, en cambio, todo lo que escribe el agente, y guarda tu respuesta donde la carguen las sesiones futuras.

## Instalación

Elige el método según dónde uses la skill.

| Dónde la usas | Método recomendado |
|---|---|
| Claude Code en tu propia máquina | [Plugin](#claude-code) desde este repositorio |
| claude.ai, Claude Desktop, Cowork o Claude Code en la web | [Subir un ZIP](#claudeai-claude-desktop-y-cowork) a tu cuenta de claude.ai |
| Codex, Cursor, Gemini CLI, GitHub Copilot y otros agentes | [`npx skills`](#otros-agentes) |

Si usas claude.ai y Claude Code, con subir el ZIP te basta para ambos, porque Claude Code carga las skills de tu cuenta de claude.ai cuando inicias sesión con ella. No instales además el plugin, porque Claude Code cargaría dos copias.

### Claude Code

Ejecuta estos comandos en una sesión de Claude Code:

```
/plugin marketplace add motestream/readers-ear
/plugin install readers-ear@readers-ear
```

El primer comando añade este repositorio como marketplace de plugins; el segundo instala el plugin `readers-ear` desde ese marketplace (el marketplace y el plugin se llaman igual). En Claude Code 2.1.275 o posterior, un solo comando hace ambas cosas: `/plugin install readers-ear --marketplace motestream/readers-ear`.

- **Actualizar**: ejecuta `/plugin marketplace update readers-ear` o activa la actualización automática de este marketplace en **Marketplaces**, dentro de `/plugin`.
- **Compartir con un equipo**: en el repositorio de tu proyecto, ejecuta `claude plugin marketplace add motestream/readers-ear --scope project` y haz commit del `.claude/settings.json` que genera. Cuando Claude Code pregunte a tus compañeros de equipo si confían en la carpeta del proyecto, quienes acepten tendrán disponible el marketplace y podrán instalar el plugin desde él.
- **Las sesiones en la nube** (Claude Code en la web) no cargan los plugins instalados en tu propia máquina. En su lugar, sube la skill a claude.ai (sección siguiente) o copia la carpeta `plugin/skills/readers-ear/` en el `.claude/skills/` de tu proyecto y haz un commit con ella.

### claude.ai, Claude Desktop y Cowork

Los nombres de menús y botones se indican tal como aparecen en la interfaz en inglés.

1. Asegúrate de que la ejecución de código esté activada. En los planes Free, Pro y Max, la opción está en **Settings > Capabilities**; en los planes Team y Enterprise, la activa un propietario, junto con las skills, en **Organization settings > Plugins & skills**.
2. Descarga este repositorio y comprime la carpeta `plugin/skills/readers-ear` en un ZIP, de modo que el ZIP contenga `readers-ear/SKILL.md`. La carpeta debe seguir llamándose `readers-ear`.
3. En claude.ai, abre **Customize > Skills**, selecciona **+**, luego **Create skill** > **Upload a skill** y elige el ZIP.

Con esto, la skill queda vinculada a tu cuenta, así que también la usan Claude Desktop y Cowork. Claude Code (2.1.273 o posterior) también la carga cuando inicias sesión con la misma cuenta, incluidas las sesiones en la nube. Para actualizarla, elimina la versión anterior en **Customize > Skills** y sube el nuevo ZIP. Los propietarios de organizaciones Team y Enterprise pueden poner la skill a disposición de todos los miembros.

### Otros agentes

```
npx skills add motestream/readers-ear -g
```

`-g` la instala para tu cuenta de usuario; sin esa opción, se instala en el proyecto actual. El comando detecta los agentes que tienes y pregunta para cuáles instalarla; para indicar uno, añade `-a`, como en `-a codex`. Para actualizar, usa `npx skills update`.

Con GitHub CLI 2.90 o posterior (`gh skill` está en versión preliminar), también puedes ejecutar `gh skill install motestream/readers-ear readers-ear --scope user`. El comando pregunta para qué agente instalarla, o puedes indicar uno con `--agent`. Para actualizar, usa `gh skill update`.

Para instalarla a mano, copia `plugin/skills/readers-ear/` en el directorio de skills de tu agente, como `~/.claude/skills/` en Claude Code.

## Uso

- La skill se activa sola siempre que el agente escribe textos para otras personas. También puedes pedirle al agente directamente que revise un texto ("haz que esto suene natural") o llamarla por su nombre: `/readers-ear`, o `/readers-ear:readers-ear` si está instalada como plugin de Claude Code.
- Para una revisión minuciosa, pídela expresamente ("tómate tu tiempo y revisa esto a fondo").
- Cuando le pidas que revise tu texto, puede rehacer la estructura si el problema está en ella. Si prefieres conservar la estructura y cambiar solo detalles, dilo ("corrige solo las erratas"); en ese caso, la skill señala los problemas de estructura en lugar de corregirlos.
- La primera vez que se ejecuta en un lugar donde puede guardar tu respuesta, te pregunta si debe revisar todo lo que escribe el agente o únicamente los textos para otras personas. Para cambiar el alcance más adelante, basta con pedirlo. Si cambias el alcance en un lugar donde no se puede guardar la configuración, la skill aplica el cambio solo a la conversación actual y te da una frase para añadir a tus propias instrucciones, de modo que las sesiones posteriores la tengan en cuenta.
- **Lo que escribe fuera de la conversación**: solo cuando eliges o cambias el alcance, la skill guarda una frase en tus instrucciones personales o en la memoria de tu cuenta (por ejemplo, en tu `CLAUDE.md` de usuario) y te dice dónde. No escribe nada más fuera del texto con el que trabajas.

## Traducciones

El agente solo carga el [`SKILL.md`](../plugin/skills/readers-ear/SKILL.md) en inglés. Las traducciones son para lectores humanos; si alguna difiere del original, prevalece la versión inglesa.

| Idioma | README | Instrucciones de la skill |
|---|---|---|
| 日本語 | [README.ja.md](README.ja.md) | [SKILL.ja.md](SKILL.ja.md) |
| 简体中文 | [README.zh-Hans.md](README.zh-Hans.md) | [SKILL.zh-Hans.md](SKILL.zh-Hans.md) |
| 한국어 | [README.ko.md](README.ko.md) | [SKILL.ko.md](SKILL.ko.md) |
| Español | [README.es.md](README.es.md) | [SKILL.es.md](SKILL.es.md) |
| Français | [README.fr.md](README.fr.md) | [SKILL.fr.md](SKILL.fr.md) |
| Deutsch | [README.de.md](README.de.md) | [SKILL.de.md](SKILL.de.md) |
| Português (Brasil) | [README.pt-BR.md](README.pt-BR.md) | [SKILL.pt-BR.md](SKILL.pt-BR.md) |

## Cómo probarla

Antes de confiar en la skill, pruébala con tus propios textos:

- Compara los resultados con y sin la skill en el mismo modelo, idealmente en varios idiomas y en géneros con fórmulas fijas, como correos comerciales, cláusulas de contratos y textos de interfaz.
- Dale un texto que ya esté bien escrito. Debería devolverlo casi sin cambios.
- Dale un texto de contenido correcto pero mal estructurado, como un informe con la conclusión escondida en mitad del texto, y pídele que lo revise. Debería rehacer la estructura y conservar todos los datos.
- Durante el trabajo de programación, comprueba que pule los mensajes de commit, las descripciones de PR y la documentación que escribe el agente, y que no toca los textos existentes escritos por otras personas.

## Contribuir

- Cuando cambies `SKILL.md` o el README en inglés, actualiza en el mismo commit las traducciones correspondientes, incluida la fecha que aparece al principio de cada traducción de la skill.
- Prueba los cambios en `SKILL.md` en al menos tres idiomas, uno de ellos con pocos datos de entrenamiento, y con cada modelo en el que quieras que funcione. Comprueba también cómo se comportan la pregunta sobre el alcance y el guardado de la respuesta en una ejecución no interactiva (`claude -p`) y en una sesión en la nube.

## Licencia

Se publica bajo la [licencia MIT](../LICENSE).
