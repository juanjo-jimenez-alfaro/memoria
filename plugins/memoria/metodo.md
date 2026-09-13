# Método de trabajo · versión 1.7.0 · generado desde el plugin memoria, no se edita a mano

Este archivo reúne el contrato del método, las normas de estilo y el índice de skills del plugin `memoria`. Sirve a quien trabaja con Gemini u otro modelo sin el plugin, y a quien abre la carpeta sin IA delante. Para ponerlo al día se vuelve a generar desde el plugin y se copia a la raíz.

---

# Convenciones

Contrato base del método. El resto de skills del plugin referencian este documento en lugar de repetir sus reglas. Si una skill contradice algo de aquí, manda este documento.

Versión del método: **1.7**

## 1. Las tres capas de propiedad

| Capa | Quién responde | Qué contiene |
|---|---|---|
| El plugin y `metodo.md` | Solo el responsable del método | Cómo se trabaja. Idéntico en todas las organizaciones |
| `guia.md` y `base/` | Un único responsable de contexto | Quién es la organización, cómo se organiza, qué sistemas usa, cómo se usa esta carpeta |
| Cada área | El dueño del área | El trabajo real |

Nadie responde fuera de su capa, y nadie pide que se escriba en la capa de otro. Un área lee `base/` y `metodo.md`, nunca los modifica. Las skills escriben en nombre de quien las usa y respetan las mismas capas. Una capa no cambia porque algo esté restringido: el dueño de un área lo es también de lo restringido dentro de ella.

### Quién teclea, y por dónde entra lo de fuera

Responder por un archivo y escribirlo son dos cosas distintas. **Lo que hay en una carpeta de trabajo lo escribe la IA en sesión**: `guia.md`, `base/`, los `area.md` y los `proyecto.md`, los registros y los entregables. Las personas deciden qué dice cada archivo y lo piden; la IA es la que teclea. `metodo.md` no es excepción: lo genera un script disparado desde una sesión.

De ahí sale el valor de la carpeta: todo lo que hay dentro entró por el método y alguien respondió por ello. En cuanto entra material que nadie puso a propósito, un almacén que una aplicación escribe sola, un archivo copiado a mano o un índice mantenido aparte, la carpeta deja de ser fiable y la IA lee ruido como si fuera contexto.

**La única puerta para el material que llega de fuera es `fuentes/`**, la del proyecto al que pertenece. De fuera es lo que no produjo el equipo del proyecto: un export, un PDF de un tercero, una transcripción, un documento que mandó un cliente. Entra a `fuentes/`, no se edita, y lo que se construya con él se escribe aparte y lo cita.

Los formatos que la IA no puede teclear, una presentación o una hoja de cálculo, son la excepción a quién escribe y no a por dónde se entra: los arma el equipo del proyecto con su herramienta y son producto suyo; si vinieron de fuera entran por `fuentes/` como cualquier otro material. La sección 3 lo detalla.

Ninguna carpeta de trabajo aloja el almacén de datos de una aplicación. Lo escribe la aplicación sola, crece por su cuenta y nadie responde por lo que hay dentro.

La migración es la excepción declarada. El material que se adopta al migrar no llega de fuera: es el trabajo anterior de la propia organización, y entra donde le toque con `estado: en-revision` y con la trazabilidad que se pueda reconstruir. Lo que en el origen ya era material de entrada entra por `fuentes/` como en cualquier proyecto. Lo detalla la skill `migrar`.

Es norma, no candado. Nada impide abrir un archivo y editarlo a mano, y a veces hay que hacerlo; detectar lo que entró por otro camino es trabajo de la skill `revisar`. La propiedad no cambia: quien responde por un archivo sigue siendo su dueño, lo que cambia es la mano que escribe.

La raíz es la carpeta que contiene `guia.md`, `metodo.md` y `base/`. Ninguna instrucción del método usa rutas absolutas, porque cada usuario tiene la carpeta sincronizada en un sitio distinto.

### Independencia entre raíces

Un mismo trabajo puede tener conectada más de una raíz a la vez, o una raíz y el repo del plugin, y solo por una razón: ajustar la estructura o comparar cómo está montada cada organización. Nunca se conectan dos raíces para trabajar el contenido de una. Cada raíz sigue siendo de una sola organización: nada que se escriba en una raíz usa hechos, cifras, nombres o decisiones de otra raíz, ni del repo del plugin, y nada que se escriba en el repo del plugin usa hechos de una organización en particular, porque el plugin es idéntico para todas. Comparar la forma de dos raíces (¿tienen las mismas piezas?, ¿la misma cabecera?) no es tocar su contenido, y ese trabajo no se guarda dentro de ninguna de las dos. Lo que una organización guarda sobre otra —por ejemplo, quien mantiene el método guardando el historial de una migración que hizo para un cliente— se limita a lo operativo de quien lo guarda: qué se entregó y cuándo, nunca el contenido del trabajo del cliente.

Eso fija dónde vive cada cosa cuando una organización adopta el método. **El registro de la migración es de quien migra**: las auditorías, los planes y los manifiestos van a su raíz, en un proyecto por organización nombrado por la organización y no por el trabajo. Cuentan lo que hizo el proveedor y hablan del sistema del que se migró, que la organización que estrena el método no usó nunca y no le dice nada.

En la raíz de la organización entra solo lo que su equipo necesita para operar, y entra donde se usa, no en un proyecto aparte: las decisiones recuperadas de su material anterior, cada una en el `decisiones.md` del proyecto al que pertenecen y marcadas como pendientes de confirmar; y el material confidencial que quedó fuera de alcance, con su fila en el `fuentes/enlaces.md` que corresponda. Nada más: su raíz no guarda rastro del sistema del que se migró, ni en las rutas, ni en el vocabulario, ni en los nombres de sus archivos.

### Permisos en Drive

- Lectura de toda la raíz para todo el equipo, salvo lo restringido.
- Escritura en la carpeta de un área solo para su dueño y las personas que él designe.
- Escritura en `guia.md` y en `base/` solo para el responsable de contexto. La IA escribe los dos, y solo puede hacerlo en la sesión de esa persona; desde la sesión de otra área prepara el texto y se lo pasa.
- Administrar la carpeta compartida es del dueño de la organización, o de una persona de su total confianza, y de nadie más. Quien administra puede quitar cualquier restricción, así que todo lo que sigue se apoya en esa lista.

### Lo restringido

Lo que no puede leer todo el equipo se marca en la carpeta que lo contiene, ahí donde ya está, con el acceso limitado de Drive: esa carpeta deja de heredar los permisos de arriba y solo entra quien esté añadido a ella. No hay carpeta compartida aparte, ni espejos, ni rutas alternativas. Una organización tiene una sola carpeta compartida.

Se restringe en tres sitios y en ninguno más:

| Qué | Dónde se marca |
|---|---|
| Un área entera | La carpeta del área |
| Un proyecto entero, dentro de un área que sí lee todo el equipo | La carpeta del proyecto |
| Parte de un proyecto | `<proyecto>/restringido/` |

Lo que decide dónde va cada cosa es quién puede leerla, no de qué trata: da igual que sea una cuenta de cliente, recursos humanos, finanzas o legal.

**Un proyecto no se parte.** Sigue siendo uno, con un dueño, un `proyecto.md`, un `decisiones.md` y un `sesiones.md`. Lo que no puede leer todo el equipo va a `restringido/`, que repite dentro las carpetas del proyecto que hagan falta, `entregables/` y `fuentes/`, con su propio `enlaces.md`. Del `enlaces.md` público desaparecen esas filas.

**Dónde escala.** En `restringido/` no entran nunca `proyecto.md`, `decisiones.md` ni `sesiones.md`. Si lo que hay que esconder es una decisión, el estado o el objetivo, el proyecto no se puede partir: se restringe entero.

**El nombre se ve.** Quien no tiene acceso ve la carpeta en gris, con su nombre, y un botón para solicitarlo que llega a quien administra. Por eso la carpeta de dentro de un proyecto se llama siempre `restringido` y no dice de qué trata. Las áreas y los proyectos se siguen listando en `guia.md` y en `area.md` con su nombre y su dueño, estén restringidos o no: el equipo tiene que poder saber que existen y a quién pedir acceso; lo que no puede es leerlos.

Si una organización necesita que ni el nombre de un área se vea, o que quien administra la carpeta compartida no pueda ver algo, ese caso se resuelve con una carpeta compartida aparte y se escribe en `base/ajustes.md`.

Poner y quitar el acceso limitado solo lo puede hacer quien administra la carpeta compartida, desde la web y de una carpeta en una. Ninguna skill lo hace: dicen qué carpeta hay que limitar y para quién, y esperan.

### Material sensible dentro de un proyecto que lee todo el equipo

Un archivo con datos personales, facturación, contratos o credenciales no se guarda en `fuentes/`: se guarda en `restringido/fuentes/` del mismo proyecto, y en el `fuentes/enlaces.md` público queda una fila con qué es, dónde está y qué tener presente al usarlo. No obliga a restringir el proyecto entero.

La IA participa en esa decisión. Cuando una skill detecta indicios de información sensible en un material (nombres junto a RFC, CURP o NSS, facturación por cliente, contratos, contraseñas, datos de salud, salarios), lo dice y propone llevarlo a `restringido/`. El usuario decide si lo es o no. Nada se mueve sin que el usuario lo confirme.

Ese material se lee igual que `fuentes/`: es taller privado del proyecto y no se cita en `basado_en` salvo por su fila de `enlaces.md`.

## 2. Estructura

```
RAIZ/
  guia.md
  metodo.md
  base/
    contexto.md
    glosario.md
    sistemas.md
    ajustes.md           (opcional: reglas propias que se suman al contrato, nunca lo contradicen)
    plantillas/          (solo si la organización personaliza las del plugin)
  <area>/
    area.md
    <proyecto>/
      proyecto.md
      decisiones.md
      sesiones.md
      entregables/
      fuentes/
        enlaces.md      (opcional)
      restringido/      (opcional: lo que no puede leer todo el equipo)
        entregables/
        fuentes/
          enlaces.md
```

Tres niveles como máximo: área, proyecto, carpeta del proyecto. Un cuarto nivel significa que ahí había dos proyectos. `restringido/` es la única excepción: no es un proyecto nuevo, es la parte del mismo proyecto que no lee todo el equipo, y dentro repite sus carpetas.

`guia.md` es para personas: qué es esta carpeta, cómo se organiza y quién escribe dónde, qué áreas hay, quién responde por cada una y cuáles están restringidas, cómo se avisa entre áreas, cuándo se revisa cada cosa, cómo conectarla a un proyecto de Cowork y qué hacer si programas. `metodo.md` lo genera el plugin y nadie lo edita: lleva este contrato, el estilo y el índice de skills, para que funcionen también con Gemini o con quien abra la carpeta sin el plugin.

### Los archivos de `base/`

| Archivo | Qué contiene |
|---|---|
| `contexto.md` | Quién es la organización, criterios transversales, qué datos son sensibles |
| `glosario.md` | Vocabulario de la casa: siglas, nombres internos, qué significa cada cosa |
| `sistemas.md` | Una tabla con cuatro columnas: sistema, para qué, quién da acceso, antes de usarlo |
| `ajustes.md` | Opcional. Reglas propias de la organización que se suman a este contrato: vocabulario adicional, criterios extra para lo confidencial, convenciones de nombres de área. Nunca puede contradecir lo que dice este documento |
| `plantillas/` | Solo si la organización quiere sus propias versiones de brief, comparativo, reporte de decisión o handoff. Si existe una, manda sobre la del plugin |

Las cuatro plantillas del método viven en el plugin, dentro de la skill `nuevo`. `base/plantillas/` no se crea por defecto.

`base/ajustes.md` sigue el mismo principio que `base/plantillas/`: es la otra forma en que una organización adapta el método sin tocar el plugin. La diferencia es que una plantilla sustituye y `ajustes.md` solo añade: reglas que este contrato no puede prever porque son propias de una organización, como un tipo de dato adicional que cuenta como confidencial, una convención de nombres para las áreas o vocabulario que conviene fijar antes de que cada quien lo escriba distinto. No puede cambiar ni contradecir nada de lo que dice esta lista; si algo en `ajustes.md` lo hace, manda esta lista y se avisa a quien mantiene `base/`. Tampoco se crea por defecto: solo si la organización lo pide.

### Estructura de `area.md`

Fija, porque varias skills leen y escriben en ella:

```markdown
# [Nombre del área]

## Qué es
[Dos o tres líneas]

## Prioridades ahora
[Tres a cinco líneas. Las pide el dueño, las escriben las skills]

## Proyectos
- `nombre-del-proyecto/` — qué es
  - nombre-del-entregable — qué es · actualizado AAAA-MM-DD

## Quién participa
Dueño: [nombre y apellido]
[Otras personas y su papel]
```

El bloque `Proyectos` es el índice de contexto del área: una línea por proyecto y, debajo, una línea por cada entregable `vigente`. Lo escribe el cierre de sesión y la creación de proyectos, no una persona. Es lo primero que lee cualquier skill antes de abrir un archivo del área.

`Quién participa` es donde vive el dueño del área. No hay otra clave para él.

## 3. Los archivos de un proyecto

| Archivo | Tipo | Qué contiene |
|---|---|---|
| `proyecto.md` | Vivo | Objetivo, alcance, quién participa, estado actual, siguientes pasos |
| `decisiones.md` | Registro | Qué se decidió, cuándo, por qué, qué se descartó y a qué afecta |
| `sesiones.md` | Registro | Qué se avanzó cada día y qué quedó pendiente |
| `entregables/` | Vivo | El producto del proyecto, en cualquier estado |
| `fuentes/` | Inmutable | Insumos crudos: exports, PDFs, transcripciones, material sin clasificar |
| `fuentes/enlaces.md` | Inmutable | Tabla de enlaces externos y de lo que está en `restringido/`. Solo existe si hay filas |

Los tres archivos de la raíz del proyecto y las dos carpetas existen siempre, aunque estén vacías. `sesiones.md` es obligatorio y lo escribe la skill de cierre de sesión, no el usuario.

No hay carpeta de borradores. Un entregable a medias vive en `entregables/` con `estado: borrador`, y lo que todavía no es nada vive en la conversación hasta que merezca ser un archivo.

No hay carpeta aparte para binarios. Una presentación hecha directo en PowerPoint o Keynote, una hoja de cálculo hecha en Excel o Numbers, un PDF que nadie generó desde texto: lo que decide dónde va es quién lo produjo. Si lo hizo el equipo del proyecto, con las manos que sea, es producto suyo y va a `entregables/` con nombre en minúsculas y guiones, igual que cualquier otro entregable. Si vino de fuera, entra por `fuentes/` aunque el proyecto lo vaya a usar tal cual, y entonces el entregable es el documento que lo cita, no el archivo de fuera. No lleva cabecera propia porque el formato no la admite; su estado y de qué se construyó se anotan en `proyecto.md` o en la entrada de `decisiones.md` que lo produjo. El lugar donde vive la raíz de la organización (Drive, iCloud) ya previsualiza estos formatos, así que no hace falta sacarlos de la estructura para poder verlos.

### Estructura de `proyecto.md`

Fija, porque varias skills escriben en ella:

```markdown
# [Nombre del proyecto]

## Objetivo
[Una frase. Qué problema resuelve y para quién.]

## Terminado significa
[Cómo sabremos que se acabó. Concreto y comprobable.]

## Alcance
Sí: [lo que entra]
No: [lo que queda fuera]

## Quién participa
Dueño: [nombre] ([área])
Consumen esto: [áreas o personas]

## Estado actual
[Dos o tres líneas]

## Siguientes pasos
- [Lista corta]
```

`Estado actual` y `Siguientes pasos` son las dos únicas secciones que reescribe el cierre de sesión. El resto cambia poco y solo a petición del dueño.

`Dueño`, en `Quién participa`, es el dueño de todo el proyecto: sus entregables, sus decisiones, quién pide publicar. Si un documento concreto tiene otro responsable, se dice en la primera línea del cuerpo de ese documento, no en la cabecera.

### Estructura de `fuentes/enlaces.md`

```markdown
| Qué es | Enlace | Qué tener presente |
|---|---|---|
| Documentación del ERP | https://… | Versión 2024, puede estar desfasada |
| Nómina del equipo, 2026 | `restringido/fuentes/nomina-2026.xlsx` | Solo el total agregado sale a un entregable |
```

## 4. Vivo o registro, nunca las dos cosas

**Un archivo vivo se reescribe** y siempre refleja el presente. Nadie necesita leer su historia para entenderlo.

**Un registro solo crece.** Las entradas nuevas van arriba y las anteriores no se editan jamás, ni para corregir. Si una decisión cambia, se añade una entrada nueva que dice que reemplaza a la anterior.

Un registro nunca vive dentro de un archivo vivo, porque la primera reescritura lo borra.

### Formato de `decisiones.md`

Único para todos los proyectos:

```markdown
## AAAA-MM-DD · Título que dice la decisión en una frase
Decidió: Nombre Apellido
Por qué: … (puede ser más de un párrafo)
Descartamos: …
Afecta a: entregables/x.md · otra-area/proyecto
```

Una entrada tiene lo justo para entender qué se decidió y por qué sin abrir nada más. El análisis que respalda la decisión (opciones, tablas, cifras) no va en la entrada: va a un entregable del proyecto y la entrada lo cita en `Afecta a` o en `Por qué`.

`Afecta a` lleva rutas relativas al proyecto para lo que está dentro de él, y `area/proyecto` cuando la decisión toca a otro proyecto de la raíz.

### Formato de `sesiones.md`

```markdown
## AAAA-MM-DD
Trabajamos en: …
Avances: …
Pendiente: …
```

Entradas nuevas arriba.

### Regla de histórico

Las entradas escritas antes de adoptar este formato se dejan tal cual; el formato aplica desde la siguiente entrada. La excepción es la migración: un registro que se acaba de crear al migrar sí se convierte, porque nadie lo ha consumido todavía.

### Aviso entre áreas

La carpeta no notifica a nadie. Por eso `Afecta a` puede nombrar proyectos de otras áreas: al abrir sesión, la skill barre todos los `decisiones.md` de la raíz buscando entradas que nombren el proyecto activo y las muestra como aviso. Al cerrar sesión, si una decisión afecta a otra área, se recuerda al usuario que avise a su dueño.

## 5. Cabecera

Todo `.md` empieza con estas tres claves y ninguna más, salvo `guia.md` y `metodo.md`, que están hechos para leerse sin nada delante y empiezan directamente por el título:

```yaml
---
estado: vigente
actualizado: 2026-08-29
basado_en:
  - base/contexto.md
  - compras/automatizacion-ordenes/fuentes/entrevista-ana.md
---
```

Inmediatamente después va el título en `#`, para que quien abra el archivo sin renderizador vea de qué trata en la primera línea legible.

**estado**, cuatro valores y nada más:

- `borrador`: lo está escribiendo alguien, no se construye encima
- `en-revision`: terminado, esperando aprobación del dueño
- `vigente`: aprobado, se puede consumir
- `reemplazado`: superado. Requiere una cuarta clave, `reemplazado_por`, con la ruta del sustituto

El paso a `vigente` lo pide siempre el dueño del proyecto de forma explícita y tiene requisitos: los aplica la skill `revisar`. Ninguna otra skill cambia ese estado por su cuenta.

**actualizado**: fecha en formato `AAAA-MM-DD`, la del último cambio de contenido real.

**basado_en**: rutas relativas a la raíz de todo lo que se usó para escribir el archivo. Es lo que permite detectar que un entregable quedó desactualizado cuando cambia algo aguas arriba. Es obligatoria en los entregables y la escribe la skill, no la persona. Para material adoptado sin trazabilidad se permite la lista vacía `[]`, y `revisar` la pide completa antes de publicar. Los registros, las fuentes y los archivos de `base/` no llevan esta clave.

No hay clave de dueño. El dueño vive en `area.md` y en `proyecto.md`, en `Quién participa`. Si un documento concreto tiene otro responsable, lo dice la primera línea de su cuerpo.

Las claves van sin acentos ni eñes.

## 6. Nombres

Minúsculas, guiones en vez de espacios, sin acentos ni eñes, sin fechas ni números de versión, sin números de fase ni de etapa. `flujo-aprobacion.md`, no `Flujo de Aprobación v2 FINAL.md` ni `fase1-flujo-aprobacion.md`.

El nombre de un archivo es estable durante toda su vida. La versión la lleva Drive, el estado lo lleva la cabecera y el orden de las fases lo cuenta `proyecto.md`.

### El nombre de una carpeta compartida

La raíz es una carpeta compartida y su nombre se ve en Drive, así que ese sí lleva mayúsculas y espacios: `Acme`. Solo letras, números, espacios y guiones, y los acentos y las eñes que traiga el nombre propio. Ningún otro signo: el nombre de una carpeta compartida se escribe a mano muchas veces —al buscarla, al pedir acceso, al nombrarla en un correo, al usarla en la terminal o en un script— y cualquier signo que no esté en el teclado se copia mal, se escribe distinto cada vez y obliga a comprobar si una herramienta lo admite. Si una organización ya tiene una carpeta con un signo así, se propone renombrarla; el método no depende del nombre, porque ninguna instrucción usa rutas absolutas.

## 7. Qué es público

La superficie pública de un proyecto son `entregables/` y `decisiones.md`. Es lo único que otra área puede leer para construir encima, y solo si el entregable está `vigente`. `area.md` y `proyecto.md` también se leen desde fuera, porque son el índice que lleva hasta esa superficie.

`sesiones.md`, `fuentes/` y todo lo que está restringido son taller privado. Nadie de fuera del área los lee ni los cita en `basado_en`.

Dentro de la misma área, un entregable puede citar en `basado_en` una fuente de otro proyecto del área, siempre la original y nunca una copia: un export vive en un solo `fuentes/` y los demás lo citan por su ruta. Entre áreas no se citan fuentes, solo entregables vigentes y decisiones.

### Lo restringido se cita en una sola dirección

Un archivo restringido puede citar en `basado_en` lo que quiera de lo que sí lee todo el equipo: entregables vigentes, decisiones, `base/`. Al revés, nunca. Nada que lea todo el equipo cita, nombra ni resume un archivo restringido, porque quien lo lea no va a poder abrirlo y porque la cita misma ya cuenta algo de lo que hay dentro. La única excepción es la fila de `fuentes/enlaces.md`, que dice que un material existe y dónde está, no lo que dice.

Vale igual para `Afecta a`: una decisión restringida puede apuntar a cualquier proyecto, y una decisión que lee todo el equipo apunta a un área o a un proyecto restringido por su nombre, que ya está listado, nunca a uno de sus archivos.

Lo aprendido dentro de un área restringida vuelve a la memoria común **reescrito, no movido**: se publica como entregable propio de un proyecto que lee todo el equipo, con lo que sirve para la próxima vez y sin los datos, las cifras ni los nombres de donde salió. Un archivo restringido no sale nunca de donde está; un aprendizaje sí cambia de sitio, y lo hace escribiéndolo de nuevo.

## 8. Rotación

Cuando un registro pasa de unas 1.500 líneas o cambia el año, se archiva con el año en el nombre (`sesiones-2026.md`) y se abre uno nuevo. Lo hace la skill de cierre de sesión, sin preguntar.

## 9. Lo que no existe en este sistema

- Una carpeta `metodo/` dentro de la raíz. El método vive en el plugin y en `metodo.md`
- `AGENTS.md` ni ningún archivo de instrucciones para la IA dentro de la raíz. Las instrucciones son las skills y el texto para Cowork de `guia.md`
- Índices, inventarios o resúmenes mantenidos a mano o por otra herramienta. El único índice es el bloque `Proyectos` de cada `area.md`, y lo escriben las skills
- El almacén de datos de una aplicación dentro de la raíz. Lo escribe la aplicación sola y nadie responde por lo que hay dentro
- Material que llegó de fuera guardado en cualquier sitio que no sea `fuentes/`
- Una clave de dueño en la cabecera. El dueño está en `area.md` y `proyecto.md`
- Una carpeta compartida aparte para lo restringido, ni espejos de la raíz. Se restringe donde está
- Una carpeta restringida sin dueño en `area.md` o en `proyecto.md`. Restringir no cambia de quién es
- Copias de una fuente en dos proyectos. Se cita la original
- Carpetas numeradas (`01-`, `02-`) ni números de fase en los nombres
- Carpetas llamadas `varios`, `otros`, `temp` o `borrador`
- Un archivo por decisión
- Enlaces wiki `[[asi]]`, callouts propietarios, archivos `.canvas`
- Rutas absolutas dentro de cualquier archivo
- Estado del método guardado en la memoria del modelo ni en la memoria de proyecto de Claude, que hoy sí existe como función y viene activada. Es por persona y por proyecto, no se comparte con el equipo, no se audita, no se ve, y puede contradecir un archivo sin que nadie lo note. Si un dato importa, está en un `.md`
- Cualquier archivo que el usuario tenga que rellenar a mano

## 10. Actualización del método

El método se actualiza publicando una versión nueva del plugin. La versión vive en el plugin y en la primera línea legible del `metodo.md` de cada raíz. Al abrir sesión se comparan las dos y se avisa si la raíz se quedó atrás; ponerla al día es volver a generar `metodo.md` desde el plugin. Nadie edita `metodo.md` dentro de la carpeta de una organización.

## 11. Cómo se lee

Nunca se lee todo. El camino va por niveles y se para en el primero que responde:

1. `guia.md`: la lista de áreas, quién responde por cada una y cuáles están restringidas
2. `base/contexto.md`, `base/glosario.md` y `base/ajustes.md`, si existe
3. `area.md` de las áreas pertinentes. Su bloque `Proyectos` es el índice: dice qué proyectos hay y qué entregables vigentes tiene cada uno
4. Solo entonces, del proyecto que toque: `proyecto.md`, `decisiones.md` completo y las cabeceras de `entregables/`
5. El cuerpo de un entregable, solo si hace falta

`base/sistemas.md` se lee cuando el trabajo toca un sistema. `sesiones.md`, `fuentes/` y lo restringido de otra área no se leen nunca para responder a otra área.

Si el camino lleva a una carpeta restringida sin acceso, la lectura falla. Eso no es un error ni un hueco: se dice qué área o qué proyecto es y quién es su dueño, y ahí se para. No se deduce lo que hay dentro por los nombres de las carpetas ni se da por hecho que no hay nada.

## 12. Cowork y programadores

**Cowork.** El uso principal del método es Claude Cowork con la raíz conectada y el plugin instalado. El montaje tiene dos reglas.

**Un proyecto por persona**, nombrado por su área. Es lo que hace que la línea del área en las instrucciones signifique algo y que el aviso de «esto le toca a otra área» tenga a quién señalar.

**Se conecta la raíz completa, nunca la carpeta de un área.** `guia.md`, `metodo.md` y `base/` viven en la raíz; la lectura en cascada cruza áreas; `consulta` busca en lo que produjo cualquier área y `sesion` avisa de las decisiones de otras que afectan al proyecto. Conectada solo un área, el método se rompe en la primera llamada. Conectar de más no abre ningún riesgo: quién puede leer y escribir dónde lo fijan los permisos de las carpetas, no el alcance de la conexión, y lo restringido sigue restringido dentro de una carpeta conectada.

Un proyecto de Claude admite una sola carpeta, que se elige al crearlo y no se puede ampliar después. Es la raíz, y no hace falta ninguna más. Si se eligió mal, se crea otro proyecto.

El texto para pegar en las instrucciones del proyecto no nombra skills, porque Claude las elige solo:

```
Este proyecto trabaja sobre una memoria de trabajo permanente: la carpeta conectada, que sigue el método del plugin `memoria`. Aplícalo en todo lo que hagas aquí, y no guardes nada en tu memoria: si un dato importa, va a un archivo de la carpeta.
Lee `guia.md` al empezar, y `base/ajustes.md` si existe.
Escribe solo donde te haya dicho que trabajo, y en ningún otro sitio de la carpeta; si no te lo he dicho, pregúntamelo antes de escribir nada. Si algo le toca a otra área, dímelo y yo se lo pido a su dueño.
No des por aprobado ningún documento ni edites lo ya registrado en decisiones o sesiones.
Si una carpeta no se deja leer, está restringida: dímelo y sigue con lo que sí puedas leer, sin suponer lo que hay dentro.
Antes de guardar algo, pregúntate si alguien más lo va a leer y si contiene datos que no todos deben ver. Si algo parece confidencial, avísame y propón moverlo; no lo muevas tú.
```

El bloque es idéntico en cualquier organización: no nombra a ninguna, no lleva huecos que rellenar y nada de una raíz concreta entra en él. Lo propio de una raíz vive en `base/ajustes.md`, que la segunda línea manda leer. Debajo del bloque cada persona añade una línea suya diciendo dónde escribe —su área, sus áreas o `base/`—; esa línea es de ella, no del método. Si falta, la IA pregunta antes de escribir en vez de suponer.

La skill `nuevo` escribe todo esto en `guia.md` como una receta de cinco pasos —crear el proyecto con el nombre del área, instalar el plugin desde el marketplace, conectar la raíz, pegar el texto y comprobar con «abre sesión en...»— para que cada persona lo monte sola sin preguntarle a nadie.

**Otros modelos.** Gemini u otro modelo sin plugin leen `metodo.md`. Contiene este contrato, el estilo y el índice de skills, así que saben qué reglas seguir aunque no puedan ejecutarlas como skills.

**Programadores.** El `CLAUDE.md` de un repositorio enlaza la carpeta del proyecto en la raíz (`area/proyecto`). Las decisiones de código que dependen de un diseño se anclan en `decisiones.md` y en los entregables vigentes de ese proyecto, no en comentarios del código. Para saber qué se decidió antes de escribir código, usan la skill `consulta`.

---

# Estilo

Estilo de todo lo que se escribe, firma o comparte en esta estructura:

> **Ejecutivo y al grano: el hecho relevante desde el inicio, sin rodeos ni expresiones que no aporten de manera directa.**

Se escribe para alguien con poco tiempo y muchas interrupciones. Tiene que poder leer en diagonal, quedarse con lo que decide y no perderse nada esencial por haberlo hecho así.

Este archivo es la fuente canónica del estilo. Si una plantilla, la del plugin o una de `base/plantillas/`, lo contradice, manda este archivo.

## Cuándo se aplica

Siempre, sin que nadie la invoque, en cualquier redacción o revisión. Y de forma explícita cuando alguien pide que suene menos a IA, más ejecutivo, más al grano, más compacto, que se lea rápido, o que le quiten los rodeos.

**No se cambia por iniciativa propia.** Este es el estilo de la casa y se aplica por defecto, aunque el texto parezca pedir otro registro. Solo cambia si quien encarga el texto lo pide de forma expresa, y el cambio vale para ese texto: no se guarda como estándar nuevo ni se arrastra al siguiente entregable.

## Las dos preguntas que resuelven casi todo

1. **¿La primera frase ya dice el hecho, o lo anuncia?** Si lo anuncia, empieza por el hecho.
2. **¿Puedo borrar esta palabra y no se pierde información?** Entonces sobra.

## Lectura rápida

Los siete patrones de abajo arreglan la frase. Estas ocho reglas arreglan el documento, que es donde se pierde al lector que tiene prisa.

1. **La primera pantalla basta.** Quien solo lee eso sale sabiendo el estado y qué se decide. Nada esencial vive por debajo del primer pliegue.
2. **Los títulos dicen el hecho, no el tema.** *"El motor cuesta 2.44 M al año"*, no *"Costos del motor"*.
3. **Una idea por fila.** Si el contenido se puede enumerar, va en lista o tabla. La prosa se reserva para lo que necesita argumento.
4. **Si cabe en una fila de tabla, no va en un párrafo.**
5. **Cada afirmación trae su dato.** Un párrafo que no aporta un dato ni cambia una decisión se borra.
6. **La consecuencia va pegada a la acción.** El "si esto no ocurre, pasa aquello" debajo de su acción, no en una lista de riesgos al final que el lector ya no relaciona.
7. **Lo hecho antes de lo pendiente**, cuando el lector decide sobre el trabajo de otros.
8. **Sin preámbulo de sección.** Título y contenido. Las frases que presentan lo que viene se borran.

## Siete patrones a evitar

**1. Metadiscurso, frases que anuncian en vez de decir.** El patrón que más suena a IA: construye expectativa antes de entregar contenido.

- Mal: *"El punto central es que el motor propio sale más barato."* · *"Y el hallazgo que reordena la pregunta: no existe API fiscal mexicana."* · *"Lo que conviene tener claro:"* · *"para una lectura equilibrada"*
- Bien: *"El motor propio sale 5× más barato."* · *"No existe API fiscal mexicana en el mercado."*

**2. Guiones largos como muletilla.** Cuando el guion sustituye a dos puntos, coma o punto y coma, usa la puntuación normal. Resérvalos para incisos que funcionan como paréntesis.

- Mal: *"La decisión es clara — modernizar el motor."*
- Bien: *"La decisión es clara: modernizar el motor."*
- Bien, inciso legítimo: *"El motor —heredado de 2007— sigue en producción."*

El umbral: más de un guion largo cada 500 palabras en un entregable es muletilla, aunque cada uno por separado parezca defendible. Un entregable de 1.500 palabras con siete guiones largos tiene que bajar a tres como mucho.

- Mal: un brief de 600 palabras con cinco guiones largos, todos correctos como incisos. Son demasiados para lo que dice el texto.
- Bien: el mismo brief con uno, y los otros cuatro convertidos en dos puntos, paréntesis o frases separadas.

**3. Negaciones en espejo.** *"No es X, es Y."* Legítimas solo cuando corrigen una expectativa falsa que el lector traía. Si no la traía, di Y directamente.

- Mal: *"No es un problema de producto, es un problema de go-to-market."* (si nadie dijo que fuera de producto)
- Bien: *"El problema es de go-to-market."*

**4. Rodeos en las conclusiones.** La conclusión es lo que menos tolera preámbulo.

- Mal: *"La postura de fondo es modernizar."* → Bien: *"Modernizar."*

**5. Negritas como subrayado nervioso.** Una negrita destaca; cinco no destacan ninguna. En documentos internos ayudan a escanear; en un documento para terceros, tres por párrafo cansan.

**6. Signos que no se leen en voz alta en español.** Si no puedes leer el signo en voz alta, escribe la palabra. El caso cerrado es el signo de sección, que no aparece en ningún documento.

- Mal: el signo de sección pegado a un número o a un nombre, como abreviatura de "sección"
- Bien: *"ver la sección 4.1"* · *"secciones 2 y 3"* · *"de la sección 8"* · *"sección Nómina"*
- Se conservan `%`, `·`, `→`, el `#` de un ticket, y cualquier signo que sea parte de un identificador citado literalmente.

**7. Cifras sueltas.** Toda cifra en un entregable lleva fecha o fuente en el mismo párrafo. Una cifra sin ninguna de las dos no se puede comprobar ni saber si sigue valiendo, y el lector de dentro de seis meses no tiene a quién preguntar.

- Mal: *"El 70% del volumen son órdenes pequeñas."*
- Bien: *"El 70% del volumen son órdenes pequeñas (export de órdenes de 2025, `fuentes/ordenes-2025.csv`)."* · *"A agosto de 2026, el 70% del volumen son órdenes pequeñas."*

La fecha basta cuando el dato es de la propia organización y está en una fuente ya citada en la cabecera. La fuente hace falta cuando el dato viene de fuera.

## Alcance

- **Entregables y cualquier texto que salga del proyecto:** los siete patrones y las ocho reglas de lectura rápida, sin excepción.
- **Registros** (`sesiones.md`, `decisiones.md`): pueden ser más extensos, porque su función es dejar constancia del razonamiento. El metadiscurso y los rodeos sobran igual, y una cifra en `Por qué` también lleva su fecha o su fuente.
- **Respuestas de la IA en el chat:** la respuesta primero y el detalle después, sin recapitular lo que el usuario acaba de decir y sin narrar lo que se va a hacer. El único límite es no perder información que el usuario necesita para decidir: entre una respuesta corta y una completa gana la completa, pero sin relleno.

## Al revisar un texto existente

1. Señala los pasajes concretos y propón la reescritura. No reescribas el documento entero en silencio.
2. Lee solo la primera pantalla y pregúntate si con eso basta para saber el estado y qué se decide. Si no basta, el problema es de orden y se arregla antes que las frases.
3. Cuenta los guiones largos antes y después, y compáralos con el umbral de uno cada 500 palabras. Es la medida más rápida de si el texto mejoró.
4. Busca cada cifra y comprueba que tenga fecha o fuente al lado.
5. No toques las citas textuales de terceros ni los nombres propios de documentos y decisiones.
6. Corregir el estilo de un entregable de otro proyecto o de otra área es tocar contenido ajeno, no forma. Se propone al dueño, no se aplica.

---

# Skills del plugin

Lo que hace cada una, en una línea. Con el plugin instalado se activan solas por las frases que menciona cada descripción.

- **convenciones**: Contrato base del metodo de trabajo: estructura de carpetas, cabecera de los archivos, estados, como se lee la raiz, que es publico y que se restringe. Consultala antes de crear o modificar cualquier archivo dentro de la memoria de una organizacion, y cuando pregunten como se organiza algo, donde va, que significa un estado o quien puede escribir donde.
- **estilo**: Normas de estilo y de lectura rapida. Aplicala por defecto al redactar o revisar cualquier texto que se vaya a firmar o compartir, y tambien a las respuestas en el chat, sin que la invoquen; y de forma explicita cuando pidan 'que suene menos a IA', 'mas ejecutivo', 'mas al grano', 'mas compacto', 'que se lea rapido' o 'revisa el estilo'.
- **sesion**: Abre y cierra sesiones de trabajo sobre un proyecto. Usala cuando digan 'abre sesion', 'retomamos X', 'en que quedamos con...', 'cierra la sesion', 'guarda lo de hoy' o 'terminamos'.
- **nuevo**: Da de alta lo que falte en la memoria de la organizacion: monta la raiz si la carpeta no tiene guia.md, crea el area si no existe y crea el paquete completo de un proyecto. Usala cuando digan 'nuevo proyecto', 'arranca un proyecto para...', 'necesito documentar esto como proyecto', 'nueva area', 'crea el area de...', 'monta la carpeta de...', 'nueva organizacion', 'arranca el metodo para este cliente', o cuando se trabaje en algo que todavia no tiene carpeta.
- **entregable**: Crea o actualiza un entregable de un proyecto. Usala cuando pidan 'prepara el documento de...', 'necesito un documento con...', 'documenta lo que decidimos sobre...', o 'actualiza el entregable X'.
- **revisar**: Revisa un entregable, detecta lo que quedo desfasado y publica de en-revision a vigente. Usala con 'revisa X', 'esto esta listo?', 'que esta desactualizado?', 'pasalo a vigente' o 'ya lo aprobo...'.
- **donde-va**: Coloca cualquier material que llegue en el sitio correcto de la estructura. Usala cuando pregunten 'donde guardo esto?', peguen un documento o un enlace sin decir donde va, o aparezca un archivo suelto en la raiz.
- **consulta**: Responde preguntas sobre lo que la organizacion ya sabe, leyendo solo la superficie publica de la raiz y sin escribir nada. Usala cuando pregunten 'que sabemos de X?', 'alguien ya trabajo esto?', 'que se decidio sobre...?', 'hay algo hecho sobre...?' o 'quien lleva...?'.
- **migrar**: Adopta una carpeta que sigue otra estructura y la trae al metodo sin borrar los originales. Usala cuando digan 'migra esta carpeta', 'trae esto al metodo', 'adopta lo que hay en...', 'convierte estos documentos a la estructura' o cuando aparezca una carpeta con ADR, logs de sesion o carpetas numeradas.
