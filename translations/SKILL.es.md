# readers-ear (traducción orientativa al español)

> Esta es una traducción orientativa. Los agentes solo cargan el original en inglés, [`plugin/skills/readers-ear/SKILL.md`](../plugin/skills/readers-ear/SKILL.md); si hay diferencias, prevalece la versión inglesa. Traducción basada en la versión inglesa del 25 de octubre de 2026.

```yaml
---
name: readers-ear
description: Revisa textos, desde la estructura hasta la redacción, para que resulten naturales a su destinatario, en cualquier idioma o género. Úsala siempre que escribas textos que vayan a leer personas distintas del usuario (correos, artículos, documentos, publicaciones, diapositivas, discursos, ficción, traducciones, textos de interfaz), aunque el usuario no pida una revisión; siempre que el usuario pida revisar o pulir un texto, o hacer que suene natural o menos a IA; y en todos los textos si las instrucciones guardadas del usuario así lo indican.
---
```

# Reader's Ear

Procura que el texto parezca escrito para su destinatario por alguien que domina el idioma y el género. La referencia es ese lector, no las reglas: no te guíes por listas de palabras o patrones prohibidos, y conserva las fórmulas fijas que exigen el género o las convenciones. Juzga el texto según las normas de su propio idioma, no las del idioma de estas instrucciones (el inglés, en el original) ni las del idioma en que piensas. Los ejemplos y las guías de estilo del usuario tienen prioridad sobre cualquier indicación de estas instrucciones.

## Revisión estándar

Lee el texto como lo leería su destinatario al verlo por primera vez. A continuación, examina el conjunto antes que las partes: plantéate primero qué necesita decirle el texto a este lector y si, según las normas del género, su estructura sirve para transmitirlo (qué va primero, cómo se agrupan y ordenan las partes, para qué sirve cada una); solo entonces pasa a los párrafos, las oraciones y las palabras. Pulir las oraciones no salva una estructura que no funciona, y si se rehace la estructura, las oraciones cambiarán de todos modos.

Cambia solo lo que puedas identificar como un problema concreto: algo que haría que el lector tropezara, perdiera el hilo o no encontrara lo que necesita cuando lo necesita, o algo que alguien que domina el idioma y el género no habría escrito así. Corrige cada problema en el nivel que le corresponde, desde una palabra hasta el texto entero; a veces, lo mejor es suprimir un pasaje. Retocar las oraciones una a una deja intacta la estructura, así que, cuando el problema está en la estructura, haz una lista de lo que el texto tiene que transmitir (sus datos, sus ideas y su propósito) y, a partir de ella, reconstruye la parte afectada o el texto entero, con el orden y la forma que necesita este lector. Luego compara el resultado con el texto de partida para detectar cualquier dato o idea que la reconstrucción haya perdido o alterado, y cualquier afirmación que haya añadido. Conserva un cambio solo si mejora el texto, y detente cuando no puedas identificar otro problema. Un texto que ya es bueno debería quedar casi sin cambios. Ajusta el esfuerzo a la extensión y la importancia del texto.

Hay dos tipos de problemas fáciles de pasar por alto. Uno es la interferencia de cualquier idioma que no sea el del texto, aunque no aparezca ni en lo que recibes ni en tu razonamiento. Se manifiesta como calcos en el orden de las palabras, los giros, las colocaciones, los modismos, la puntuación y las comillas, los formatos de números y fechas o las fórmulas de tratamiento; como palabras extranjeras que este lector no usaría, o como una mezcla de grafías, sistemas de escritura o vocabulario de distintas regiones. El otro es depender de un contexto que el lector nunca vio, como tu conversación con el usuario.

Sea cual sea el texto que revises:

- En los textos que te dé el usuario, conserva los datos, las ideas y la voz de su autor, y no cambies más de lo que pide el encargo. En lugar de corregirlos, señala los errores o ambigüedades que afecten al sentido. Un encargo general, como revisar o pulir el texto o hacer que suene natural, incluye su estructura; uno más limitado, como corregir erratas o la gramática, no la incluye, así que en ese caso señala los problemas de estructura en lugar de corregirlos. Una traducción conserva la estructura del original, salvo que el usuario te pida adaptarla.
- No inventes datos, cifras ni citas para hacer el texto más concreto; señala lo que falta o pregunta.
- Si dudas de tu criterio sobre el idioma o el tema del texto, cambia menos y dilo.
- Entrega el texto terminado y lo que el usuario necesite saber, como los puntos que hayas señalado en lugar de corregirlos. Si reestructuraste un texto que te dio el usuario, explica en una o dos frases qué cambiaste y por qué. No incluyas tus notas de trabajo ni tus borradores salvo que te los pidan.

## Revisión minuciosa

Haz esta revisión solo cuando el usuario pida expresamente una revisión más pausada y minuciosa de lo habitual, porque lleva mucho más tiempo y consume muchos más tokens. Esta revisión añade a la estándar lecturas externas, que se recaban antes de que te formes tu propio juicio sobre el texto, para que ese juicio no influya en ellas. Sigue este orden:

1. Antes de buscar problemas por tu cuenta, abre dos contextos nuevos que no hayan visto tu conversación, como subagentes recién creados (no copias de este contexto); pueden trabajar a la vez. No les cuentes a ninguno de los dos lo que hayas observado o sospeches sobre el texto.
   - Búsqueda de referencias: indícale a este contexto el idioma del texto, su destinatario, su género, su propósito en términos generales y los criterios sobre fuentes que se indican más abajo, pero no le pases el texto. Pídele que busque algunos textos del mismo género y con el mismo propósito que cumplan esos criterios; que lea las páginas completas, no solo los fragmentos que muestra el buscador; que enumere las páginas que usó, y que resuma cómo están escritas: estructura, fórmulas fijas, extensión, registro y cualquier otra cosa que exija el género.
   - Lectura en frío: pásale a este contexto solo el texto y una nota sobre su destinatario y su propósito. Pídele que lo lea como lo haría ese destinatario y que te indique dónde tropieza o pierde el hilo, y cuál cree que es la idea principal del texto.
2. Con los dos informes delante, lee tú el texto y haz una lista de sus problemas.
3. Comprueba en fuentes actuales y autorizadas, como diccionarios, manuales de uso del idioma y páginas oficiales, lo que más le importa al destinatario o aquello de lo que tengas más dudas (ortografía, puntuación, términos, datos, etc.).
4. Corrige como en la revisión estándar. Usa las referencias como patrón con el que medir el texto, no como redacción que copiar; en los textos que te dé el usuario, los datos, las ideas y la voz de su autor siguen siendo lo primero.

Criterios sobre las fuentes de los pasos 1 y 3: usa fuentes en el idioma del texto cuya redacción haya revisado una persona o una organización que se haga responsable de ella.

- No uses traducciones, por buenas que sean, porque pueden arrastrar los patrones de su idioma de origen. Esto incluye las versiones traducidas de las páginas de sitios multilingües.
- Para la expresión y las convenciones del género, usa textos del mismo género y con el mismo propósito, como las páginas que las instituciones públicas, las grandes empresas y las editoriales de prestigio publican originalmente en ese idioma; las obras de autores reconocidos del género, y los textos recogidos en corpus. De todos ellos, los más fiables son los textos anteriores a la difusión de la IA generativa (hacia 2022); los posteriores también sirven cuando es evidente que un editor o una institución responde de ellos.

Si no puedes abrir contextos nuevos, omite la lectura en frío, busca y lee tú mismo las referencias antes de buscar problemas y continúa desde el paso 2.

Cuéntale brevemente al usuario qué consultaste y qué cambiaste a raíz de ello, y menciona cualquier paso que no hayas podido hacer, como las lecturas en contextos nuevos o las búsquedas. Nunca presentes como realizado un paso que hayas omitido.

## Alcance

El alcance solo determina qué revisas sin que te lo pidan; siempre revisas lo que el usuario te pida. Hay dos alcances:

- A (predeterminado): los textos que escribes y cuyos lectores finales son personas distintas del usuario.
- B: todos los textos que escribes.

Si tus instrucciones o tu memoria no fijan un alcance, usa A y, después de entregar el texto, pregunta una sola vez al usuario si quiere B. No hagas esta pregunta cuando el usuario no pueda tomar esa decisión (por ejemplo, si es el usuario final de un producto de terceros), cuando trabajes como subagente o sin supervisión, o cuando no haya un lugar adecuado donde guardar la respuesta (véase más abajo).

Cuando el usuario responda, o si más adelante cambia el alcance, guarda su elección como una frase que mencione esta skill y el alcance, escrita en el idioma del usuario (por ejemplo, "Usa la skill readers-ear en todos los textos que escribas" o "Usa la skill readers-ear en los textos que escribas para que los lean otras personas"). Guárdala en un lugar personal que carguen todas las sesiones futuras, como un archivo de instrucciones a nivel de usuario o la memoria de la cuenta. No uses archivos compartidos con un equipo, una memoria limitada a un solo proyecto ni lugares donde la frase se pueda guardar pero no se cargue la próxima vez, como un entorno desechable en la nube. Dile al usuario dónde la guardaste. Si no existe un lugar así, aplica la elección solo a esta conversación, avísale y dale la frase para que la pegue en sus propias instrucciones.
