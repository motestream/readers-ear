# readers-ear (traducción orientativa al español)

> Esta es una traducción orientativa. Los agentes solo cargan el original en inglés, [`plugin/skills/readers-ear/SKILL.md`](../plugin/skills/readers-ear/SKILL.md); si hay diferencias, prevalece la versión inglesa. Traducción basada en la versión inglesa del 31 de octubre de 2026.

## Nombre y descripción

Esta sección traduce los campos `name` y `description` del principio del archivo en inglés. La descripción le indica al agente cuándo debe usar la skill.

- **Nombre**: `readers-ear`
- **Descripción**: Escribe y revisa textos de cualquier idioma y género para que le resulten naturales a su destinatario. Úsala en estos casos:
  - al escribir textos que vayan a leer personas distintas del usuario, como correos, artículos, documentos, publicaciones, diapositivas, discursos, ficción, traducciones, textos de interfaz, mensajes de commit y descripciones de PR
  - al informar al usuario, en la respuesta final después de trabajar en lo que pidió o en un documento preparado para que lo lea

  En estos dos casos, úsala aunque el usuario no haya pedido ayuda con la redacción. Úsala también cuando el usuario pida revisar o pulir un texto, o hacer que suene natural o menos a IA, y en todo lo que escriba el agente en prosa si las instrucciones guardadas del usuario así lo indican.

A continuación se traduce el cuerpo de las instrucciones.

# Reader's Ear

Haz que el texto que escribas o revises parezca escrito para su destinatario por alguien que domina el idioma y el género del texto.

## El criterio

La medida del texto es su destinatario, no las reglas. Pregúntate qué sabe ya este lector, qué necesita del texto, qué relación tiene con quien escribe y qué espera del género y del idioma del texto. Que una palabra, una oración o una estructura funcionen o no depende de esas respuestas, así que la misma decisión puede ser acertada en un texto y equivocada en otro. Conserva las fórmulas fijas que pide el género, aunque parezcan estereotipadas.

Para averiguar qué sabe ya el lector, separa lo que ha visto de lo que solo sabes tú. Cuando el lector es el usuario, lo que ha visto de la conversación son sus propios mensajes, tus respuestas finales a sus peticiones y los documentos que preparaste para él. Da por no visto todo lo demás, como lo que escribiste en la conversación mientras trabajabas en una respuesta, tu razonamiento, los resultados de las herramientas, los informes de los subagentes y los nombres que les pusiste a las cosas durante el trabajo. Más allá de la conversación, el usuario cuenta con lo que conoce por su propio trabajo y su especialidad.

Juzga el texto según las normas de su propio idioma, no según las del inglés (el idioma original de estas instrucciones) ni las del idioma en que piensas.

Los ejemplos de redacción y las guías de estilo que aporte el usuario tienen prioridad sobre esta skill. Si el usuario no ha dicho quién es el lector, dedúcelo del texto y de la petición.

## Escribir textos nuevos

Aplica esta sección cuando escribas tú mismo un texto a partir de la información de que dispones, también cuando traduzcas.

Antes de redactar, responde a las preguntas de «El criterio» pensando en este lector. Decide para qué va a leer el texto: por ejemplo, para tomar una decisión, ejecutar un comando, saber en qué punto están las cosas o disfrutar de una historia. A partir de ese propósito, decide qué necesita llevarse del texto y qué necesita encontrar primero. Elige la estructura que esperan el género y el lector; en una traducción, conserva la estructura del original (el orden de sus secciones y de sus puntos), salvo que el usuario te pida adaptarla. Después escribe el borrador para ese lector, siguiendo las normas del idioma y del género del texto.

Después de redactar, lee el borrador una vez como lo leería su lector y corrige los problemas concretos que encuentres con los criterios y los métodos de «Revisar textos». Si el borrador ya se lee bien, déjalo como está.

## Revisar textos

Sigue este procedimiento para revisar un texto que ya existe.

Lee el texto como lo leería su destinatario al encontrarlo por primera vez. Algo cuenta como problema solo si puedes señalarlo:

- un punto en el que el lector tropezaría, perdería el hilo o no encontraría lo que necesita cuando lo necesita
- un punto que alguien que domina ese idioma y ese género no habría escrito así, y puedes decir cómo lo habría escrito
- un pasaje que no le aporta al lector nada que necesite

Para juzgar este último caso, pregúntate si, sin ese pasaje, el texto serviría peor al propósito del lector.

Hay problemas en todos los niveles: una palabra, una oración, un pasaje o la estructura del texto entero. Examina todos los niveles.

Corrige cada problema en su propio nivel. Suprime los pasajes que no le aporten al lector nada que necesite; en los textos que aporta el usuario, hazlo solo si la petición es general (véase «Textos que aporta el usuario») y di qué suprimiste. En una traducción, conserva todo lo que dice el original y conserva también su estructura, salvo que el usuario te pida adaptarla. Corrige los problemas de estructura reconstruyendo, no reformulando: haz una lista de lo que el texto tiene que transmitir, reconstruye la parte afectada en el orden que necesita el lector y compárala con el original para detectar cualquier cosa que se haya perdido, cambiado o añadido.

Cambia el texto solo para corregir problemas concretos, y conserva una corrección solo si el texto mejora con ella. Detente cuando no quede ningún problema concreto, de modo que un texto bueno salga casi sin cambios. Dedica a la tarea un tiempo proporcional a la extensión y la importancia del texto.

## Dos problemas que hay que buscar

Cuando leas un borrador o un texto como su lector, busca en particular estos dos problemas.

**Interferencia de otros idiomas.** Los idiomas que no son el del texto dejan huellas, incluso los que no aparecen en ninguna parte de lo que recibes ni de tu razonamiento. Busca los indicios en lugar de intentar averiguar de qué idioma vienen: el orden de las palabras, los giros, las colocaciones, los modismos, la puntuación y las comillas, los formatos de números y fechas o las formas de tratamiento calcados de otro idioma. Busca también palabras extranjeras que el lector no usaría y mezclas de grafías, sistemas de escritura o vocabulario de distintas regiones.

**Contexto que el lector no ha visto.** Busca los puntos que dependen de algo que el lector no ha visto (véase «El criterio»), como tu conversación con el usuario, notas que el lector no tiene o nombres que les pusiste a las cosas mientras trabajabas. Ante cada nombre, cada término y cada referencia a algo anterior, pregúntate dónde lo habría aprendido este lector. Si no puedes señalar ese lugar, dilo con palabras que conozca, como las que él mismo usó, o, si necesita el término, explícalo donde aparece por primera vez.

## Textos que aporta el usuario

Cuando revises o traduzcas un texto que aporta el usuario:

- Conserva los datos, las ideas y la voz del autor, y no cambies más de lo que se te pide.
- Una petición general (revisar, pulir, hacer que suene natural o menos a IA) abarca todos los niveles. Una petición acotada, como corregir erratas, no abarca problemas de mayor nivel: señala, en lugar de corregirlos, los que inducirían a error al lector o lo confundirían, como los errores factuales, y no hagas sugerencias de estilo.
- Señala, en lugar de corregirlos, los errores factuales y cualquier ambigüedad que solo podrías resolver adivinando qué quiso decir el autor. Una incoherencia que puedes resolver con los propios datos del texto, como una instrucción que no cuadra con una hora indicada en otra parte, es un problema que hay que corregir, no señalar.

## En todas las tareas

- Usa solo los datos, las cifras y las citas que tienes. Hay una única excepción: cuando un texto que aporta el usuario solo ofrece generalidades y la petición incluye hacer que se lea con naturalidad o que suene menos a IA, puedes añadir información general exacta y ampliamente conocida, como el funcionamiento de una técnica común. Nunca añadas experiencias, datos, citas ni afirmaciones sobre el usuario o su organización, y enumera todo lo que hayas añadido.
- Si falta información, pregúntasela al usuario y escribe la oración que la necesita con un marcador de posición entre corchetes, para que el texto quede listo en cuanto el usuario lo rellene. Cuando no puedas preguntar, por ejemplo porque trabajas sin supervisión, marca el hueco en el texto de la misma forma.
- Si dudas de tu criterio sobre el idioma o el tema, cambia menos y dilo.
- Entrega el texto terminado junto con lo que el usuario necesite saber, incluidos los puntos que señalaste en lugar de corregirlos y, si reorganizaste su texto, una frase que explique por qué. No incluyas notas de trabajo ni borradores salvo que el usuario los pida.

## Modo minucioso

Usa el modo minucioso solo cuando el usuario pida expresamente un trabajo más lento y exhaustivo, en la conversación o en sus instrucciones guardadas, porque lleva mucho más tiempo y consume muchos más tokens. En el modo minucioso, antes de juzgar el texto tú mismo, consigues que dos contextos nuevos te den una visión externa de él. Son contextos nuevos los que no han visto la conversación, como subagentes recién creados, no copias ni bifurcaciones del actual. Dale a cada uno solo lo que se indica a continuación, y nada de lo que tú hayas observado o sospeches sobre el texto.

- **Lector de referencias.** Dale el idioma del texto, su destinatario y su género, una idea aproximada de su propósito y las reglas sobre fuentes que se indican más abajo, pero no el texto. Pídele que busque algunos textos del mismo género y propósito que cumplan esas reglas, y que los lea completos en lugar de fiarse de los fragmentos que muestra el buscador. Su informe recoge qué fuentes usó y cómo están escritos esos textos: estructura, fórmulas fijas, extensión, registro y cualquier otra cosa que espere el género.
- **Lector en frío.** Dale solo el texto y una nota sobre su lector y su propósito; en una traducción, dale la traducción, no el original. Pídele que lea como lo haría ese lector. Su informe recoge dónde tropieza o pierde el hilo, y cuál cree que es la idea principal.

Después, sigue estos pasos:

1. **Consigue los dos informes.** Si estás revisando, pon a trabajar a los dos lectores a la vez. Si estás escribiendo un texto nuevo, incluida una traducción, pon a trabajar primero al lector de referencias y redacta con su informe delante. Después pasa el borrador terminado directamente al lector en frío, sin hacer antes la lectura del borrador que se describe en «Escribir textos nuevos»; tú lo leerás en el paso 2. Si no dispones de contextos nuevos, omite la lectura en frío y busca y lee tú mismo las referencias: antes de buscar problemas, si estás revisando, o antes de redactar, si estás escribiendo un texto nuevo.
2. **Lee tú el texto.** Con los informes delante, lee el texto y haz una lista de sus problemas. Trata los informes como elementos de juicio que contrastar con tu propia lectura, no como una lista de cambios que hacer.
3. **Contrasta con fuentes.** Comprueba en fuentes actuales y autorizadas, como diccionarios, guías de uso del idioma y sitios oficiales, los términos, los nombres, las cifras y la ortografía de los que depende el texto, y cualquier punto sobre el que tengas dudas. Como el texto del usuario puede ser confidencial, busca con términos, nombres y frases cortas, no con pasajes del texto.
4. **Revisa.** Trabaja como en «Revisar textos». Usa las referencias como patrón con el que medir el texto, no como redacción que copiar. En el texto del usuario, los datos, las ideas y la voz del autor tienen prioridad sobre las referencias.
5. **Informa.** Cuéntale brevemente al usuario qué consultaste y qué cambiaste a raíz de ello, y nombra cada paso que omitiste o no pudiste hacer.

**Reglas sobre fuentes** (para los pasos 1 y 3). Usa fuentes escritas originalmente en el idioma del texto, cuya redacción haya revisado una persona u organización que se haga responsable de ella. Las traducciones, incluidas las páginas traducidas de los sitios multilingües, no sirven, porque pueden arrastrar los patrones de su idioma de origen. La única excepción está en el paso 3: para comprobar cómo escribe una organización sus propios nombres y términos, puedes usar sus páginas oficiales en el idioma del texto. Para la expresión y las convenciones del género, usa textos del mismo género y propósito, como:

- páginas de instituciones públicas, grandes empresas, grandes medios de comunicación y editoriales de prestigio
- obras de autores reconocidos del género
- textos de corpus compilados con criterio

No uses textos cuya redacción no parezca haber revisado nadie, como páginas anónimas, sitios que producen artículos en masa y resúmenes generados automáticamente.

## Alcance

El alcance solo importa cuando nadie te ha pedido que uses esta skill: es lo que determina a qué textos la aplicas por iniciativa propia. Sea cual sea el alcance, revisa siempre lo que el usuario te pida revisar. Hay tres alcances:

- **Textos para otros e informes para el usuario** (el predeterminado): los textos para otros, tal como se definen más abajo, y tus informes para el usuario. Un informe es tu respuesta final a una petición que el usuario te hace directamente, cuando para responderla has tenido que trabajar (por ejemplo, leer archivos, ejecutar comandos o delegar en subagentes), o bien un documento u otro material que preparas para que lo lea el usuario. Lo que escribes en la conversación mientras trabajas en la respuesta final no es un informe, ni tampoco lo es una respuesta breve que puedes dar a partir solo de la conversación.
- **Textos para otros**: los textos que escribes y cuyos lectores finales son personas distintas del usuario.
- **Toda la prosa**: todo lo que escribes en prosa.

Si tus instrucciones o tu memoria no fijan un alcance, usa el predeterminado. Después de entregar el primer texto dentro del alcance predeterminado, pregúntale al usuario si quiere mantener este alcance, aplicar la skill a todo lo que escribas en prosa o aplicarla solo a los textos para otros. Haz esta pregunta solo si se cumple todo lo siguiente:

- Trabajas con el usuario de forma interactiva, no como subagente ni sin supervisión.
- El usuario puede tomar esa decisión. El usuario final de un producto de terceros, por ejemplo, no puede.
- Hay un lugar adecuado donde guardar la respuesta.

Haz esta pregunta una sola vez en total, contando todas las sesiones. Si el usuario sigue adelante sin responder, tómalo como una elección del alcance predeterminado y guárdala como se describe más abajo, para que ninguna sesión posterior vuelva a preguntar.

Cuando el usuario responda, o si más adelante cambia el alcance, guarda su elección como una frase en el idioma del usuario que mencione la skill y el alcance. En inglés, por ejemplo: «Use the readers-ear skill on text you write for other people to read and on your final answers and documents for me», «Use the readers-ear skill on all prose you write» o «Use the readers-ear skill only on text you write for other people to read».

Guarda la frase en un lugar personal que carguen todas las sesiones futuras, como un archivo de instrucciones a nivel de usuario o la memoria de la cuenta, y no en un archivo compartido con un equipo, en una memoria limitada a un solo proyecto ni en un lugar que no se vaya a cargar la próxima vez, como un entorno desechable en la nube. Dile al usuario dónde la guardaste. Si el usuario cambia el alcance donde no existe un lugar así, aplica su elección solo a la conversación actual, díselo y dale la frase para que la pegue en sus propias instrucciones.

Cuando apliques la skill sin que te lo pidan, trabaja solo en los textos que escribes tú y deja como están los textos de otras personas, aunque estén en el mismo archivo. Si la aplicas dentro de otra tarea, como escribir un mensaje de commit o un informe para el usuario, entrega el texto como lo requiera esa tarea y menciona solo lo que el usuario necesite saber.
