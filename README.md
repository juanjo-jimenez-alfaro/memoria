# Memoria

Marketplace con el plugin `memoria`: la memoria de la organización. Un método de trabajo y documentación por proyecto que la IA lee y sobre el que los equipos construyen.

Nueve skills que escriben y mantienen una estructura de carpetas compartida en Drive, con sesiones, decisiones y entregables en Markdown, para que la carpeta sirva de memoria que la IA lee antes de ayudar a cualquiera.

## Instalación

En Claude Code, Claude Desktop o Cowork:

```
/plugin marketplace add juanjo-jimenez-alfaro/memoria
/plugin install memoria@memoria-marketplace
```

Para probar en local antes de publicar, desde la carpeta del repo:

```
/plugin marketplace add .
/plugin install memoria@memoria-marketplace
```

En una organización de Claude Team o Enterprise, el propietario puede distribuir el plugin a todos los usuarios sin que cada uno lo instale.

## Qué incluye

| Skill | Para qué |
|---|---|
| `convenciones` | Contrato base: estructura, cabeceras, estados, cómo se lee, qué es público, qué se restringe |
| `estilo` | Normas de redacción, siempre activas |
| `sesion` | Abrir y cerrar sesión de trabajo sobre un proyecto |
| `nuevo` | Dar de alta lo que falte: la raíz de la organización, un área o un proyecto |
| `entregable` | Crear o actualizar un entregable |
| `revisar` | Revisar, detectar desfase y publicar |
| `donde-va` | Colocar material que llega en el sitio correcto |
| `consulta` | Responder qué sabe ya la organización, sin escribir nada |
| `migrar` | Adoptar una carpeta que venía de otra estructura, sin borrar los originales |

El plugin trae además las cuatro plantillas del método (brief, comparativo, reporte de decisión, handoff), dentro de la skill `nuevo`, y el archivo `metodo.md` generado.

## Cómo se usa con una organización

Cada organización tiene una raíz sincronizada en Drive, autocontenida, con `guia.md`, `metodo.md` y `base/`, y una carpeta por área. La monta la skill `nuevo`.

`guia.md` es para personas: qué es la carpeta, quién escribe dónde, qué áreas hay, cómo se avisa entre áreas, cuándo se revisa cada cosa, cómo conectarla a Cowork con el texto para pegar en las instrucciones del proyecto, y qué hacer si programas. `metodo.md` lo genera el plugin y nadie lo edita: reúne el contrato, el estilo y el índice de skills, para que funcionen también con Gemini o con quien abra la carpeta sin el plugin.

El número de versión vive en el plugin y en la primera línea de `metodo.md`. Al abrir sesión se comparan y se avisa si la raíz se quedó atrás; ponerla al día es regenerar `metodo.md` con `plugins/memoria/build-metodo.sh` y copiarlo a la raíz.

## Lo restringido

Lo que no puede leer todo el equipo se queda donde está y se marca con el acceso limitado de Drive, que desactiva la herencia de permisos en esa carpeta: solo entra quien esté añadido a ella. Una organización tiene una sola carpeta compartida. No hay unidad aparte ni espejos.

Se restringe un área entera, un proyecto entero, o solo una parte de un proyecto. En el tercer caso el proyecto no se parte: sigue siendo uno, con un dueño y un registro, y lo que no puede leer todo el equipo vive en su carpeta `restringido/`, con su fila en el `fuentes/enlaces.md` público. Si lo que hay que esconder es una decisión, el estado o el objetivo, el proyecto se restringe entero.

Quien no tiene acceso ve la carpeta en gris, con su nombre, y un botón para pedirlo que llega a quien administra. Las áreas y los proyectos se listan en `guia.md` y en `area.md` estén restringidos o no: el equipo sabe que existen y a quién pedir acceso, pero no los lee. La cita va en una sola dirección: lo restringido cita a lo que lee todo el equipo, nunca al revés, y lo aprendido sale reescrito, sin los datos ni los nombres de donde salió.

El modelo se apoya en una condición: administrar la carpeta compartida es del dueño de la organización o de una persona de su total confianza, porque quien administra puede quitar cualquier restricción. Si hace falta esconder algo también de él, esa organización abre una carpeta compartida aparte y lo escribe en `base/ajustes.md`.

Las skills participan: cuando `donde-va`, `migrar`, `entregable` o el cierre de sesión detectan indicios de información sensible en un material, lo dicen y proponen llevarlo a `restringido/`. El usuario decide, y nada se mueve sin su confirmación. Poner y quitar el acceso limitado lo hace una persona en la web de Drive, nunca una skill.

## Versiones

**1.6** · Lo restringido deja de vivir en una carpeta compartida aparte y pasa a marcarse donde ya está, con el acceso limitado de Drive. Desaparecen la unidad restringida, el espejo parcial de la raíz y sus reglas, y la prohibición de restringir carpetas dentro de la raíz. Una organización tiene una sola carpeta compartida y se restringe en tres sitios: un área, un proyecto, o `<proyecto>/restringido/` cuando solo una parte del proyecto no puede leerla todo el equipo. Un proyecto ya no se parte entre dos sitios: sigue siendo uno, y escala a restringirse entero solo si lo que hay que esconder tendría que entrar en `proyecto.md`, `decisiones.md` o `sesiones.md`. La condición que lo sostiene entra al contrato: administrar la carpeta compartida es del dueño de la organización o de una persona de su total confianza, porque quien administra puede quitar cualquier restricción; el caso en que haya que esconder algo también de él se resuelve con una carpeta aparte declarada en `base/ajustes.md`. El montaje en Cowork baja de tres reglas a dos, porque solo hay una carpeta que conectar, y dice que un proyecto admite una sola carpeta elegida al crearlo y no ampliable. `Independencia entre raíces` fija que conectar varias raíces a la vez solo se hace para trabajar la estructura. La lista de lo que no existe nombra la memoria de proyecto de Claude, que hoy sí es una función y no guarda estado del método. Las siete skills que preguntaban si la unidad estaba conectada pasan a tratar la falta de acceso como un error de lectura.

**1.5.2** · El nombre sugerido para la unidad pasa de `<Organización> · Restringido` a `<Organización> - Restringido`. El punto medio era decorativo y no está en el teclado: el nombre de una carpeta compartida se teclea muchas veces —al buscarla, al pedir acceso, al nombrarla en un correo, en la terminal o en un script—, y un signo que hay que copiar de algún lado se escribe distinto cada vez y obliga a comprobar en cada herramienta nueva si lo admite. El contrato gana una subsección en `Nombres` que fija cómo se llama una carpeta compartida —letras, números, espacios y guiones, con los acentos y eñes del nombre propio— y `nuevo` la aplica: revisa el nombre de la carpeta conectada y el de la unidad antes de escribir nada, y lo suma a su lista de lo que nunca hace. Cambian los ejemplos de `nuevo`, `donde-va` y `migrar`. Las organizaciones que ya tienen una unidad con el nombre viejo la renombran cuando quieran: el método no usa rutas absolutas y nada se rompe al hacerlo.

**1.5.1** · El nombre sugerido para la unidad pasa de `<Organización> · Confidencial` a `<Organización> · Restringido`, para que el nombre visible en Drive use la misma palabra que el contrato. Sale de la primera aplicación de 1.5: una organización que renombre su unidad y un plugin que siga proponiendo la palabra vieja parten el vocabulario en la siguiente que se monte. Cambian los ejemplos de `nuevo`, `donde-va` y `migrar`, y el texto de `guia.md` que escribe `nuevo`; el contrato no cambia de reglas. Se corrige además un ejemplo de `nuevo` que había entrado con el nombre de una organización real y el de una de sus cuentas: los ejemplos del plugin no nombran a ninguna organización.

**1.5** · El método deja de suponer que toda la raíz la puede leer todo el equipo. Entra el concepto de **unidad restringida**: una raíz puede tener ninguna, una o varias carpetas compartidas aparte, cada una con su propio acceso, y cada una es un espejo parcial de la raíz —mismas áreas, mismos proyectos, misma estructura— sin `guia.md`, `metodo.md` ni `base/`, porque su método y su contexto son los de la raíz. Lo que se restringe es un área, no un tipo de documento, así que sirve igual para una cuenta de cliente, para recursos humanos o para finanzas; un área puede vivir entera a un lado o partida entre los dos, pero la partición es por proyecto y lo único que cruza dentro de un proyecto es material sensible suelto, que es el caso que el método ya cubría. Las áreas restringidas se listan siempre en `guia.md`, con su dueño y dónde viven. La cita va en **una sola dirección**: lo restringido cita a la raíz, nada de la raíz nombra ni resume lo restringido, y lo aprendido vuelve a la memoria común reescrito y sin los datos de donde salió. Quien trabaja en un área restringida conecta dos carpetas en su proyecto de Cowork, raíz y unidad, porque la unidad sola no significa nada. `nuevo` da de alta áreas restringidas y las lista en `guia.md`; `donde-va` decide primero a qué lado va cada cosa; `consulta` y `sesion` se paran en lo que no pueden abrir y lo dicen en vez de deducirlo; `migrar` manda a la unidad el origen que es trabajo restringido; `entregable` y `revisar` bloquean la cita en la dirección prohibida.

**1.3.4** · Se cierra cómo se conecta una raíz a Claude, que el método daba por sabido. `guia.md` trae ahora una receta de cinco pasos que cada persona ejecuta sola: crear su proyecto con el nombre de su área, instalar el plugin desde el marketplace, conectar la carpeta, pegar las instrucciones y comprobar con «abre sesión en…». Dos reglas nuevas: **un proyecto por persona**, y **se conecta la raíz completa, nunca la carpeta de un área** —`guia.md`, `metodo.md` y `base/` viven en la raíz, la lectura en cascada cruza áreas, y `consulta` y `sesion` necesitan verlas todas—; quién escribe dónde lo fijan los permisos de la carpeta compartida y la línea del área, no el alcance de la conexión. La unidad confidencial no se conecta salvo en la sesión que la necesite. El texto para pegar pasa a ser **portable sin cambios**: no nombra organización, no lleva huecos que rellenar y no dice nada propio de una raíz, porque eso vive en `base/ajustes.md`, que el propio texto manda leer. Dónde escribe cada quien va en una línea aparte que añade la persona; si falta, se pregunta antes de escribir en vez de suponer.

**1.3.3** · Se corrige a quién pertenece el registro de una migración, que 1.3.2 había puesto del lado equivocado. Es de quien migra y va a su raíz, en el proyecto de la relación con esa organización: cuenta el trabajo del proveedor y habla de un sistema de origen que el equipo que estrena el método no usó nunca. En la raíz de la organización entra solo lo que su equipo necesita para operar, y donde se usa: las decisiones recuperadas en el `decisiones.md` de su proyecto, y el material confidencial pendiente en su `fuentes/enlaces.md`. Su raíz no guarda rastro del sistema de origen, ni en rutas ni en vocabulario. `migrar` lo suma a "lo que nunca hago".

**1.3.2** · El contrato dice ahora dónde vive la adopción del método por una organización, que "Independencia entre raíces" dejaba sin resolver: las auditorías, los planes de migración y los manifiestos son de la organización y van a su raíz, como proyecto dentro de un área que ya cruce áreas y que ya sea de su dueño; en la raíz de quien mantiene el método queda un proyecto por organización, nombrado por la organización y no por el trabajo, con solo el registro de la relación (qué se entregó, cuándo, con qué versión, qué falta) y sin entregables propios. `migrar` dice dónde se guarda el reporte y `nuevo` recuerda abrir el proyecto de la relación; los dos lo repiten en su lista de "lo que nunca hago".

**1.3.1** · Nueva sección en el contrato, "Independencia entre raíces": si una sesión tiene conectada más de una raíz a la vez, o una raíz y el repo del plugin, nada que se escriba en una usa hechos de otra; comparar la forma de dos raíces no es tocar su contenido, y lo que una organización guarda sobre otra se limita a lo operativo (qué se entregó y cuándo), nunca al contenido del trabajo. `migrar` y `donde-va` lo repiten en su lista de "lo que nunca hago".

**1.3** · `empresa/` pasa a llamarse `base/`: nombre más general, que sirve igual para una empresa, un equipo o un trabajo personal. Nuevo `base/ajustes.md`, opcional: una organización puede sumar ahí reglas propias (vocabulario adicional, criterios extra para lo confidencial, convenciones de nombres de área) sin tocar el plugin y sin poder contradecir el contrato; sigue el mismo principio que `base/plantillas/`, pero suma en vez de sustituir.

**1.2.1** · Lo migrado puede entrar `vigente` al migrar, sin pasar primero por revisión, si quien migra era el dueño del material en el origen y lo pide de forma explícita; `sesiones.md` deja constancia de por qué. No hay carpeta aparte para binarios: una presentación o una hoja de cálculo sin `.md` detrás va directo a `entregables/` (si es el producto) o a `fuentes/` (si es material de entrada), sin cabecera propia porque el formato no la admite; su estado y procedencia se anotan en `proyecto.md`. La convención venía de un sistema anterior que no podía previsualizar binarios; donde vive la raíz de la organización hoy (Drive, iCloud) ya los previsualiza.

**1.2** · El plugin pasa a llamarse `memoria`. Desaparece la carpeta `metodo/` de la raíz; en su lugar hay un `metodo.md` generado desde el plugin y un `guia.md` para personas que absorbe lo que antes era `mantenimiento.md` y trae el texto de cinco líneas para Cowork. La cabecera baja a tres claves: `estado`, `actualizado` y `basado_en` (antes `construido_a_partir_de`); el dueño vive en `area.md` y `proyecto.md`, no en una clave. `area.md` tiene estructura fija y su bloque Proyectos es el índice del área. Sección nueva en el contrato sobre cómo se lee la raíz por niveles. Formato único de decisiones con `Afecta a` entre áreas: al abrir sesión se barren las decisiones de toda la raíz y al cerrar se recuerda avisar. Lo confidencial va a una unidad compartida restringida, con su fila en `fuentes/enlaces.md`, y las skills lo detectan y proponen. Dentro de un área se citan fuentes de otros proyectos sin copiarlas; entre áreas solo entregables vigentes y decisiones. `empresa/sistemas.md` nuevo; `empresa/plantillas/` solo si la organización personaliza las del plugin. Las altas de organización, área y proyecto se funden en la skill `nuevo`; se añaden `consulta` y `migrar`. En estilo, umbral de guiones largos y cifras con fecha o fuente.

**1.1** · Desaparece la carpeta `borrador/`, que colisionaba con `estado: borrador`. Un entregable a medias vive en `entregables/` con ese estado, y el material sin clasificar en `fuentes/`. El dueño pasa a ser bloqueante al crear un proyecto.

**1.0** · Primera versión.
