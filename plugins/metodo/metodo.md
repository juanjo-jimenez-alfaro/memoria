# Método de trabajo · versión 1.2 · generado desde el plugin, no se edita a mano

Este archivo reúne el contrato del método, las normas de estilo y el índice de skills del plugin `metodo`. Sirve a quien trabaja con Gemini u otro modelo sin el plugin, y a quien abre la carpeta sin IA delante. Para ponerlo al día se vuelve a generar desde el plugin y se copia a la raíz.

---

# Convenciones

Contrato base del método. El resto de skills del plugin referencian este documento en lugar de repetir sus reglas. Si una skill contradice algo de aquí, manda este documento.

Versión del método: **1.2**

## 1. Las tres capas de propiedad

| Capa | Quién escribe | Qué contiene |
|---|---|---|
| El plugin y `metodo.md` | Solo el responsable del método | Cómo se trabaja. Idéntico en todas las organizaciones |
| `empresa/` | Un único responsable de contexto | Quién es la organización, cómo se organiza, qué sistemas usa |
| Cada área | El dueño del área | El trabajo real |

Nadie escribe fuera de su capa. Un área lee `empresa/` y `metodo.md`, nunca los modifica. Las skills escriben en nombre de quien las usa y respetan las mismas capas.

La raíz es la carpeta que contiene `guia.md`, `metodo.md` y `empresa/`. Ninguna instrucción del método usa rutas absolutas, porque cada usuario tiene la carpeta sincronizada en un sitio distinto.

### Permisos en Drive

- Lectura de toda la raíz para todo el equipo.
- Escritura en la carpeta de un área solo para su dueño y las personas que él designe.
- `fuentes/` de cada proyecto restringida al dueño del área.
- `empresa/` la escribe únicamente el responsable de contexto.
- Un archivo con datos personales, facturación o contratos que entre en `fuentes/` va acompañado de una nota `.md` con el mismo nombre base (`nomina-2026.xlsx` y `nomina-2026.md`) que dice qué contiene y qué no se puede hacer con él.

## 2. Estructura

```
RAIZ/
  guia.md
  metodo.md
  empresa/
    contexto.md
    glosario.md
    sistemas.md
    mantenimiento.md
    plantillas/
      brief.md
      comparativo.md
      reporte-de-decision.md
      handoff.md
  <area>/
    area.md
    <proyecto>/
      proyecto.md
      decisiones.md
      sesiones.md
      entregables/
      fuentes/
        enlaces.md      (opcional)
```

Tres niveles como máximo: área, proyecto, carpeta del proyecto. Un cuarto nivel significa que ahí había dos proyectos.

`guia.md` es para personas: qué es esta carpeta, qué áreas hay y quién responde por cada una, cómo conectarla a un proyecto de Cowork y qué hacer si programas. `metodo.md` lo genera el plugin y nadie lo edita: lleva este contrato, el estilo y el índice de skills, para que funcionen también con Gemini o con quien abra la carpeta sin el plugin.

### Los archivos de `empresa/`

| Archivo | Qué contiene |
|---|---|
| `contexto.md` | Quién es la organización, criterios transversales, qué datos son sensibles |
| `glosario.md` | Vocabulario de la casa: siglas, nombres internos, qué significa cada cosa |
| `sistemas.md` | Una tabla con cuatro columnas: sistema, para qué, quién da acceso, antes de usarlo |
| `mantenimiento.md` | Capas y permisos, cómo se avisa entre áreas, cuándo se revisa cada cosa |
| `plantillas/` | Las cuatro plantillas del método: brief, comparativo, reporte de decisión, handoff |

### Estructura de `area.md`

Fija, porque varias skills leen y escriben en ella:

```markdown
# [Nombre del área]

## Qué es
[Dos o tres líneas]

## Prioridades ahora
[Tres a cinco líneas. Las reescribe el dueño, o el cierre de sesión a petición suya]

## Proyectos
- `nombre-del-proyecto/` — qué es
  - nombre-del-entregable — qué es · actualizado AAAA-MM-DD

## Quién participa
Dueño: [nombre y apellido]
[Otras personas y su papel]
```

El bloque `Proyectos` es el índice de contexto del área: una línea por proyecto y, debajo, una línea por cada entregable `vigente`. Lo escribe el cierre de sesión y la creación de proyectos, no una persona. Es lo primero que lee cualquier skill antes de abrir un archivo del área.

## 3. Los archivos de un proyecto

| Archivo | Tipo | Qué contiene |
|---|---|---|
| `proyecto.md` | Vivo | Objetivo, alcance, estado actual, siguientes pasos |
| `decisiones.md` | Registro | Qué se decidió, cuándo, por qué, qué se descartó y a qué afecta |
| `sesiones.md` | Registro | Qué se avanzó cada día y qué quedó pendiente |
| `entregables/` | Vivo | El producto del proyecto, en cualquier estado |
| `fuentes/` | Inmutable | Insumos crudos: exports, PDFs, transcripciones, material sin clasificar |
| `fuentes/enlaces.md` | Inmutable | Enlaces externos, uno por línea con qué es. Solo existe si hay enlaces |

Los tres archivos de la raíz del proyecto y las dos carpetas existen siempre, aunque estén vacías. `sesiones.md` es obligatorio y lo escribe la skill de cierre de sesión, no el usuario.

No hay carpeta de borradores. Un entregable a medias vive en `entregables/` con `estado: borrador`, y lo que todavía no es nada vive en la conversación hasta que merezca ser un archivo.

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

Todo `.md` empieza con estas claves y ninguna más, salvo `guia.md` y `metodo.md`, que están hechos para leerse sin nada delante y empiezan directamente por el título:

```yaml
---
estado: vigente
dueno: Ana Pérez
actualizado: 2026-08-29
construido_a_partir_de:
  - empresa/contexto.md
  - compras/automatizacion-ordenes/fuentes/entrevista-ana.md
---
```

Inmediatamente después va el título en `#`, para que quien abra el archivo sin renderizador vea de qué trata en la primera línea legible.

**estado**, cuatro valores y nada más:

- `borrador`: lo está escribiendo alguien, no se construye encima
- `en-revision`: terminado, esperando aprobación del dueño
- `vigente`: aprobado, se puede consumir
- `reemplazado`: superado. Requiere una quinta clave, `reemplazado_por`, con la ruta del sustituto

El paso a `vigente` lo pide siempre el dueño de forma explícita y tiene requisitos: los aplica la skill `revisar`. Ninguna otra skill cambia ese estado por su cuenta.

**dueno**: una persona con nombre y apellido. Nunca un área ni un equipo.

**actualizado**: fecha en formato `AAAA-MM-DD`, la del último cambio de contenido real.

**construido_a_partir_de**: rutas relativas a la raíz de todo lo que se usó para escribir el archivo. Es lo que permite detectar que un entregable quedó desactualizado cuando cambia algo aguas arriba. Es obligatoria en los entregables y la escribe la skill, no la persona. Para material adoptado sin trazabilidad se permite la lista vacía `[]`, y `revisar` la pide completa antes de publicar. Los registros, las fuentes y los archivos de `empresa/` no llevan esta clave.

Las claves van sin acentos ni eñes.

## 6. Nombres

Minúsculas, guiones en vez de espacios, sin acentos ni eñes, sin fechas ni números de versión, sin números de fase ni de etapa. `flujo-aprobacion.md`, no `Flujo de Aprobación v2 FINAL.md` ni `fase1-flujo-aprobacion.md`.

El nombre de un archivo es estable durante toda su vida. La versión la lleva Drive, el estado lo lleva la cabecera y el orden de las fases lo cuenta `proyecto.md`.

## 7. Qué es público

La superficie pública de un proyecto son `entregables/` y `decisiones.md`. Es lo único que otra persona puede leer para construir encima, y solo si el entregable está `vigente`. `area.md` y `proyecto.md` también se leen desde fuera, porque son el índice que lleva hasta esa superficie.

`sesiones.md` y `fuentes/` son taller privado. Nadie de fuera del proyecto los lee ni los cita en `construido_a_partir_de`.

## 8. Rotación

Cuando un registro pasa de unas 1.500 líneas o cambia el año, se archiva con el año en el nombre (`sesiones-2026.md`) y se abre uno nuevo. Lo hace la skill de cierre de sesión, sin preguntar.

## 9. Lo que no existe en este sistema

- Una carpeta `metodo/` dentro de la raíz. El método vive en el plugin y en `metodo.md`
- `AGENTS.md` ni ningún archivo de instrucciones para la IA dentro de la raíz. Las instrucciones son las skills y el texto para Cowork de `guia.md`
- Índices mantenidos a mano. El único índice es el bloque `Proyectos` de cada `area.md`, y lo escriben las skills
- Carpetas numeradas (`01-`, `02-`) ni números de fase en los nombres
- Carpetas llamadas `varios`, `otros`, `temp` o `borrador`
- Un archivo por decisión
- Enlaces wiki `[[asi]]`, callouts propietarios, archivos `.canvas`
- Rutas absolutas dentro de cualquier archivo
- Estado guardado en la memoria del modelo o en un proyecto de Claude. Si un dato importa, está en un `.md`
- Cualquier archivo que el usuario tenga que rellenar a mano

## 10. Actualización del método

El método se actualiza publicando una versión nueva del plugin. La versión vive en el plugin y en la primera línea legible del `metodo.md` de cada raíz. Al abrir sesión se comparan las dos y se avisa si la raíz se quedó atrás; ponerla al día es volver a generar `metodo.md` desde el plugin. Nadie edita `metodo.md` dentro de la carpeta de una organización.

## 11. Cómo se lee

Nunca se lee todo. El camino va por niveles y se para en el primero que responde:

1. `guia.md`: la lista de áreas y quién responde por cada una
2. `empresa/contexto.md` y `empresa/glosario.md`
3. `area.md` de las áreas pertinentes. Su bloque `Proyectos` es el índice: dice qué proyectos hay y qué entregables vigentes tiene cada uno
4. Solo entonces, del proyecto que toque: `proyecto.md`, `decisiones.md` completo y las cabeceras de `entregables/`
5. El cuerpo de un entregable, solo si hace falta

`empresa/sistemas.md` se lee cuando el trabajo toca un sistema. `sesiones.md` y `fuentes/` de otro proyecto no se leen nunca para responder a otra área.

## 12. Cowork y programadores

**Cowork.** El uso principal del método es Claude Cowork con la raíz conectada y el plugin instalado. `guia.md` trae el texto estándar para pegar en las instrucciones de un proyecto de Cowork: usa el plugin `metodo`, aplica `convenciones` antes de crear o mover, no escribas en `empresa/` ni en un área ajena, no publiques a `vigente`, no edites registros, lee `guia.md`. La skill `organizacion-nueva` escribe ese texto al montar la raíz.

**Otros modelos.** Gemini u otro modelo sin plugin leen `metodo.md`. Contiene este contrato, el estilo y el índice de skills, así que saben qué reglas seguir aunque no puedan ejecutarlas como skills.

**Programadores.** El `CLAUDE.md` de un repositorio enlaza la carpeta del proyecto en la raíz (`area/proyecto`). Las decisiones de código que dependen de un diseño se anclan en `decisiones.md` y en los entregables vigentes de ese proyecto, no en comentarios del código. Para saber qué se decidió antes de escribir código, usan la skill `consulta`.

---

# Estilo

Estilo de todo lo que se escribe, firma o comparte en esta estructura:

> **Ejecutivo y al grano: el hecho relevante desde el inicio, sin rodeos ni expresiones que no aporten de manera directa.**

Este archivo es la fuente canónica del estilo. Si una plantilla de `empresa/plantillas/` lo contradice, manda este archivo.

## Cuándo se aplica

Siempre, sin que nadie la invoque, en cualquier redacción o revisión. Y de forma explícita cuando alguien pide que suene menos a IA, más ejecutivo, más al grano, o que le quiten los rodeos.

## Las dos preguntas que resuelven casi todo

1. **¿La primera frase ya dice el hecho, o lo anuncia?** Si lo anuncia, empieza por el hecho.
2. **¿Puedo borrar esta palabra y no se pierde información?** Entonces sobra.

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

- **Entregables y cualquier texto que salga del proyecto:** los siete patrones, sin excepción.
- **Registros** (`sesiones.md`, `decisiones.md`): pueden ser más extensos, porque su función es dejar constancia del razonamiento. El metadiscurso y los rodeos sobran igual, y una cifra en `Por qué` también lleva su fecha o su fuente.

## Al revisar un texto existente

1. Señala los pasajes concretos y propón la reescritura. No reescribas el documento entero en silencio.
2. Cuenta los guiones largos antes y después, y compáralos con el umbral de uno cada 500 palabras. Es la medida más rápida de si el texto mejoró.
3. Busca cada cifra y comprueba que tenga fecha o fuente al lado.
4. No toques las citas textuales de terceros ni los nombres propios de documentos y decisiones.
5. Corregir el estilo de un entregable de otro proyecto o de otra área es tocar contenido ajeno, no forma. Se propone al dueño, no se aplica.

---

# Skills del plugin

Lo que hace cada una, en una línea. Con el plugin instalado se activan solas por las frases que menciona cada descripción.

- **convenciones**: Contrato base del metodo de trabajo: estructura de carpetas, cabecera de los archivos, estados, como se lee la raiz y que es publico. Consultala antes de crear o modificar cualquier archivo dentro de la estructura de una organizacion, y cuando pregunten como se organiza algo, donde va, que significa un estado o quien puede escribir donde.
- **estilo**: Normas de estilo de redaccion. Aplicala por defecto al redactar o revisar cualquier texto que se vaya a firmar o compartir, sin que la invoquen, y cuando pidan 'que suene menos a IA', 'mas ejecutivo', 'mas al grano' o 'revisa el estilo'.
- **sesion**: Abre y cierra sesiones de trabajo sobre un proyecto. Usala cuando digan 'abre sesion', 'retomamos X', 'en que quedamos con...', 'cierra la sesion', 'guarda lo de hoy' o 'terminamos'.
- **proyecto-nuevo**: Crea el paquete completo de un proyecto nuevo. Usala cuando digan 'nuevo proyecto', 'arranca un proyecto para...', 'necesito documentar esto como proyecto', o cuando se trabaje en algo que todavia no tiene carpeta.
- **entregable**: Crea o actualiza un entregable de un proyecto. Usala cuando pidan 'prepara el documento de...', 'necesito un documento con...', 'documenta lo que decidimos sobre...', o 'actualiza el entregable X'.
- **revisar**: Revisa un entregable, detecta lo que quedo desfasado y publica de en-revision a vigente. Usala con 'revisa X', 'esto esta listo?', 'que esta desactualizado?', 'pasalo a vigente' o 'ya lo aprobo...'.
- **donde-va**: Coloca cualquier material que llegue en el sitio correcto de la estructura. Usala cuando pregunten 'donde guardo esto?', peguen un documento o un enlace sin decir donde va, o aparezca un archivo suelto en la raiz.
- **consulta**: Responde preguntas sobre lo que la organizacion ya sabe, leyendo solo la superficie publica de la raiz y sin escribir nada. Usala cuando pregunten 'que sabemos de X?', 'alguien ya trabajo esto?', 'que se decidio sobre...?', 'hay algo hecho sobre...?' o 'quien lleva...?'.
- **area-nueva**: Crea un area nueva en la raiz con su area.md y la anota en guia.md. Usala cuando digan 'nueva area', 'crea el area de...', 'necesitamos una carpeta para el equipo de...' o cuando un proyecto nuevo no tenga area donde vivir.
- **organizacion-nueva**: Monta la raiz completa de una organizacion nueva: guia.md, metodo.md, empresa/ con sus cuatro archivos y plantillas, y la primera area si la hay. Usala cuando digan 'monta la carpeta de...', 'nueva organizacion', 'arranca el metodo para este cliente', 'crea la raiz' o cuando una carpeta conectada este vacia.
- **migrar**: Adopta una carpeta que sigue otra estructura y la trae al metodo sin borrar los originales. Usala cuando digan 'migra esta carpeta', 'trae esto al metodo', 'adopta lo que hay en...', 'convierte estos documentos a la estructura' o cuando aparezca una carpeta con ADR, logs de sesion o carpetas numeradas.
