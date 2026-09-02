---
name: convenciones
description: Contrato base del metodo de trabajo: estructura de carpetas, cabecera de los archivos, estados, como se lee la raiz, que es publico y que va a la unidad confidencial. Consultala antes de crear o modificar cualquier archivo dentro de la memoria de una organizacion, y cuando pregunten como se organiza algo, donde va, que significa un estado o quien puede escribir donde.
---

# Convenciones

Contrato base del método. El resto de skills del plugin referencian este documento en lugar de repetir sus reglas. Si una skill contradice algo de aquí, manda este documento.

Versión del método: **1.3**

## 1. Las tres capas de propiedad

| Capa | Quién escribe | Qué contiene |
|---|---|---|
| El plugin y `metodo.md` | Solo el responsable del método | Cómo se trabaja. Idéntico en todas las organizaciones |
| `base/` | Un único responsable de contexto | Quién es la organización, cómo se organiza, qué sistemas usa |
| Cada área | El dueño del área | El trabajo real |

Nadie escribe fuera de su capa. Un área lee `base/` y `metodo.md`, nunca los modifica. Las skills escriben en nombre de quien las usa y respetan las mismas capas.

La raíz es la carpeta que contiene `guia.md`, `metodo.md` y `base/`. Ninguna instrucción del método usa rutas absolutas, porque cada usuario tiene la carpeta sincronizada en un sitio distinto.

### Permisos en Drive

- Lectura de toda la raíz para todo el equipo.
- Escritura en la carpeta de un área solo para su dueño y las personas que él designe.
- `base/` la escribe únicamente el responsable de contexto.
- Dentro de la raíz no se restringe ninguna carpeta. Lo que no deba leer todo el equipo no entra en la raíz.

### La unidad confidencial

Cada organización tiene una segunda unidad compartida, restringida, con acceso solo para los dueños de área que la necesiten. Nombre sugerido: `<Organización> · Confidencial`.

Un archivo con datos personales, facturación, contratos, credenciales o cualquier cosa que no deba leer todo el equipo no se guarda en `fuentes/`: se guarda en la unidad confidencial, y en `fuentes/enlaces.md` del proyecto queda una fila con qué es, su liga a la unidad confidencial y qué tener presente al usarlo.

La IA participa en esa decisión. Cuando una skill detecta indicios de información sensible en un material (nombres junto a RFC, CURP o NSS, facturación por cliente, contratos, contraseñas, datos de salud, salarios), lo dice y propone llevarlo a la unidad confidencial. El usuario decide si es confidencial o no. Nada se mueve sin que el usuario lo confirme.

La unidad confidencial se lee igual que `fuentes/`: es taller privado del proyecto. No se cita en `basado_en` salvo por su fila de `enlaces.md`.

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
```

Tres niveles como máximo: área, proyecto, carpeta del proyecto. Un cuarto nivel significa que ahí había dos proyectos.

`guia.md` es para personas: qué es esta carpeta, cómo se organiza y quién escribe dónde, qué áreas hay y quién responde por cada una, cómo se avisa entre áreas, cuándo se revisa cada cosa, cómo conectarla a un proyecto de Cowork y qué hacer si programas. `metodo.md` lo genera el plugin y nadie lo edita: lleva este contrato, el estilo y el índice de skills, para que funcionen también con Gemini o con quien abra la carpeta sin el plugin.

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
[Tres a cinco líneas. Las reescribe el dueño, o el cierre de sesión a petición suya]

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
| `fuentes/enlaces.md` | Inmutable | Tabla de enlaces externos y de lo que está en la unidad confidencial. Solo existe si hay filas |

Los tres archivos de la raíz del proyecto y las dos carpetas existen siempre, aunque estén vacías. `sesiones.md` es obligatorio y lo escribe la skill de cierre de sesión, no el usuario.

No hay carpeta de borradores. Un entregable a medias vive en `entregables/` con `estado: borrador`, y lo que todavía no es nada vive en la conversación hasta que merezca ser un archivo.

No hay carpeta aparte para binarios. Una presentación hecha directo en PowerPoint o Keynote, una hoja de cálculo hecha en Excel o Numbers, un PDF que nadie generó desde texto: si es el producto del proyecto, va a `entregables/` con nombre en minúsculas y guiones, igual que cualquier otro entregable; si es material de entrada, a `fuentes/`. No lleva cabecera propia porque el formato no la admite; su estado y de qué se construyó se anotan en `proyecto.md` o en la entrada de `decisiones.md` que lo produjo. El lugar donde vive la raíz de la organización (Drive, iCloud) ya previsualiza estos formatos, así que no hace falta sacarlos de la estructura para poder verlos.

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
| Nómina del equipo, 2026 | (liga a la unidad confidencial) | Solo el total agregado sale a un entregable |
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

## 7. Qué es público

La superficie pública de un proyecto son `entregables/` y `decisiones.md`. Es lo único que otra área puede leer para construir encima, y solo si el entregable está `vigente`. `area.md` y `proyecto.md` también se leen desde fuera, porque son el índice que lleva hasta esa superficie.

`sesiones.md`, `fuentes/` y lo que está en la unidad confidencial son taller privado. Nadie de fuera del área los lee ni los cita en `basado_en`.

Dentro de la misma área, un entregable puede citar en `basado_en` una fuente de otro proyecto del área, siempre la original y nunca una copia: un export vive en un solo `fuentes/` y los demás lo citan por su ruta. Entre áreas no se citan fuentes, solo entregables vigentes y decisiones.

## 8. Rotación

Cuando un registro pasa de unas 1.500 líneas o cambia el año, se archiva con el año en el nombre (`sesiones-2026.md`) y se abre uno nuevo. Lo hace la skill de cierre de sesión, sin preguntar.

## 9. Lo que no existe en este sistema

- Una carpeta `metodo/` dentro de la raíz. El método vive en el plugin y en `metodo.md`
- `AGENTS.md` ni ningún archivo de instrucciones para la IA dentro de la raíz. Las instrucciones son las skills y el texto para Cowork de `guia.md`
- Índices mantenidos a mano. El único índice es el bloque `Proyectos` de cada `area.md`, y lo escriben las skills
- Una clave de dueño en la cabecera. El dueño está en `area.md` y `proyecto.md`
- Carpetas restringidas dentro de la raíz. Lo confidencial va a la unidad confidencial
- Copias de una fuente en dos proyectos. Se cita la original
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
2. `base/contexto.md`, `base/glosario.md` y `base/ajustes.md`, si existe
3. `area.md` de las áreas pertinentes. Su bloque `Proyectos` es el índice: dice qué proyectos hay y qué entregables vigentes tiene cada uno
4. Solo entonces, del proyecto que toque: `proyecto.md`, `decisiones.md` completo y las cabeceras de `entregables/`
5. El cuerpo de un entregable, solo si hace falta

`base/sistemas.md` se lee cuando el trabajo toca un sistema. `sesiones.md`, `fuentes/` y la unidad confidencial de otra área no se leen nunca para responder a otra área.

## 12. Cowork y programadores

**Cowork.** El uso principal del método es Claude Cowork con la raíz conectada y el plugin instalado. `guia.md` trae el texto estándar para pegar en las instrucciones de un proyecto de Cowork, cinco líneas que no nombran skills porque Claude las elige solo:

```
Esta carpeta es la memoria de la organización y sigue el método del plugin `memoria`; úsalo en todo lo que hagas aquí.
Lee `guia.md` al empezar.
Trabajo en el área `<area>`. No escribas en `base/` ni en la carpeta de otra área.
No des por aprobado ningún documento ni edites lo ya registrado en decisiones o sesiones.
Antes de guardar algo, pregúntate si alguien más lo va a leer y si contiene datos que no todos deben ver.
```

La skill `nuevo` escribe ese texto en `guia.md` al montar la raíz.

**Otros modelos.** Gemini u otro modelo sin plugin leen `metodo.md`. Contiene este contrato, el estilo y el índice de skills, así que saben qué reglas seguir aunque no puedan ejecutarlas como skills.

**Programadores.** El `CLAUDE.md` de un repositorio enlaza la carpeta del proyecto en la raíz (`area/proyecto`). Las decisiones de código que dependen de un diseño se anclan en `decisiones.md` y en los entregables vigentes de ese proyecto, no en comentarios del código. Para saber qué se decidió antes de escribir código, usan la skill `consulta`.
