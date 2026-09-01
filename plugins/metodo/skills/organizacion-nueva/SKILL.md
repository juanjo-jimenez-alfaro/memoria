---
name: organizacion-nueva
description: Monta la raiz completa de una organizacion nueva: guia.md, metodo.md, empresa/ con sus cuatro archivos y plantillas, y la primera area si la hay. Usala cuando digan 'monta la carpeta de...', 'nueva organizacion', 'arranca el metodo para este cliente', 'crea la raiz' o cuando una carpeta conectada este vacia.
---

# Organización nueva

Montar la raíz completa de una organización que empieza a usar el método. Reglas de estructura, cabecera y nombres: la skill `convenciones`.

## Cuándo

"Monta la carpeta de Acme", "nueva organización", "arranca el método para este cliente", "crea la raíz", o cuando la carpeta conectada a Cowork está vacía y alguien intenta trabajar en ella.

Se hace una vez por organización. Si la carpeta ya tiene `guia.md` o `empresa/`, no es esta skill: es `area-nueva`, `proyecto-nuevo` o `migrar`, según lo que haya.

## Qué leo antes de escribir nada

1. La carpeta conectada: si está vacía o tiene algo. Si tiene documentos de otra estructura, se para y se propone `migrar` después de montar la raíz
2. `metodo.md` del plugin, para copiarlo tal cual: está en la raíz de la carpeta del plugin, dos niveles por encima de esta skill
3. Las cuatro plantillas de `plantillas/`, junto a esta skill

## Las cuatro preguntas

Juntas, en una tanda, en lenguaje llano:

1. ¿Cómo se llama la organización?
2. ¿Quién es el responsable de contexto, la persona que mantiene `empresa/`? Nombre y apellido
3. ¿Qué sistemas usan a diario? Nombre y para qué, aunque sea una lista rápida
4. ¿Hay ya una primera área con la que empezar? Si sí, quién es su dueño

La pregunta 2 es bloqueante: sin responsable de contexto no hay quien escriba `empresa/`, y una raíz sin `empresa/` mantenida no sirve como memoria. Las otras se rellenan con lo que haya; lo que falte queda marcado como hueco.

## Qué escribo y dónde

**1. `guia.md`.** Para personas, sin cabecera de método, con estas secciones:

```markdown
# [Nombre de la organización] · cómo trabajamos con esta carpeta

## Qué es esto
Esta carpeta es la memoria de trabajo de [organización]. Cada área documenta sus proyectos
aquí, en archivos de texto, y la IA lee esta carpeta antes de ayudar a cualquiera.
Las reglas completas están en `metodo.md`. No hace falta leerlas para empezar: las aplica
el plugin `metodo` cuando trabajas con Claude.

## Cómo se organiza
`empresa/` es quién somos y qué usamos. Lo mantiene [responsable de contexto].
Cada carpeta de área es de su dueño. Dentro, cada proyecto tiene su carpeta con
`proyecto.md`, `decisiones.md`, `sesiones.md`, `entregables/` y `fuentes/`.

## Áreas
- `[area]/` · [qué es en media línea] · [dueño]

## Cómo conectarla a un proyecto de Cowork
Crea un proyecto en Cowork, conecta esta carpeta e instala el plugin `metodo`.
Pega este texto en las instrucciones del proyecto, cambiando el área:

    Esta carpeta sigue el método de trabajo del plugin `metodo`. Úsalo en todo lo que hagas aquí.
    Lee `guia.md` al empezar; ahí está la lista de áreas y quién responde por cada una.
    Antes de crear, mover o renombrar un archivo, aplica la skill `convenciones`.
    Trabajo en el área `<area>`. No escribas en `empresa/` ni en la carpeta de otra área.
    No cambies ningún entregable a `vigente`; eso lo pide su dueño con la skill `revisar`.
    No edites entradas ya escritas de `decisiones.md` ni de `sesiones.md`; los registros solo crecen.
    Al empezar a trabajar en un proyecto, abre sesión; al terminar, ciérrala.
    Para saber qué sabe ya la organización sobre algo, usa la skill `consulta`.
    Si algo no tiene sitio claro, usa la skill `donde-va` antes de guardarlo.
    Redacta con la skill `estilo`: primero la conclusión, sin rodeos.

## Si usas otro modelo
Gemini u otro modelo sin el plugin: pídele que lea `metodo.md` al empezar. Contiene las
reglas y el estilo, y el índice de lo que hace cada skill.

## Si programas
El `CLAUDE.md` de tu repositorio enlaza la carpeta del proyecto en esta raíz, como
`area/proyecto`. Las decisiones de código que dependen de un diseño se anclan en el
`decisiones.md` y en los entregables vigentes de ese proyecto, no en comentarios del
código. Antes de decidir algo que ya pudo decidir otra área, usa la skill `consulta`.
```

**2. `metodo.md`.** Copia exacta del `metodo.md` del plugin. No se edita ni una línea: su primera línea lleva la versión del método y es lo que `sesion` compara al abrir.

**3. `empresa/contexto.md`.** Esqueleto con las secciones y cada una con su hueco marcado, para que el responsable de contexto las rellene con la IA en su primera sesión:

```markdown
---
estado: borrador
dueno: [responsable de contexto]
actualizado: AAAA-MM-DD
---

# [Organización]

## Quién es
[Hueco: qué hace la organización, para quién, tamaño, dónde opera]

## Cómo se organiza
[Hueco: áreas, quién responde por cada una, cómo se decide]

## Criterios transversales
[Hueco: lo que aplica a todo proyecto sin que nadie lo diga. Presupuesto, plazos, idioma, formato de los documentos, quién firma]

## Datos sensibles
[Hueco: qué tipos de datos no salen de `fuentes/`, qué no se cita en entregables, qué no se comparte fuera del área]
```

**4. `empresa/glosario.md`.** Cabecera, título y una lista vacía con el formato: `término: qué significa`. Si el usuario dio siglas o nombres internos al responder, se meten ya.

**5. `empresa/sistemas.md`.** Cabecera, título y la tabla con sus cuatro columnas. Con las filas de la pregunta 3 si las hubo; si no, vacía:

```markdown
| Sistema | Para qué | Quién da acceso | Antes de usarlo |
|---|---|---|---|
```

**6. `empresa/mantenimiento.md`.** Las capas y los permisos tal como los fija `convenciones`, con los nombres de esta organización: quién escribe en `empresa/`, quién escribe en cada área, que `fuentes/` está restringida al dueño del área, que la carpeta no notifica y por eso al cerrar sesión se avisa a mano a otras áreas, y que `contexto.md` se revisa al menos cada 90 días porque `sesion` avisa si no se hace.

**7. `empresa/plantillas/`.** Copia de las cuatro plantillas del plugin: `brief.md`, `comparativo.md`, `reporte-de-decision.md`, `handoff.md`. Tal cual, sin adaptar; si la organización quiere cambiarlas, lo hace el responsable de contexto después.

**8. La primera área**, si la hay, con la skill `area-nueva`. Si no la hay, la lista de áreas de `guia.md` queda con una línea que dice que todavía no hay ninguna.

Nada más. Ni proyectos, ni entregables, ni carpetas vacías esperando.

## Qué respondo al terminar

Tres o cuatro líneas: qué se creó, quién es el responsable de contexto, y los dos siguientes pasos: dar permisos en Drive (lectura de la raíz a todo el equipo, escritura en `empresa/` al responsable de contexto) y rellenar `contexto.md` en una primera sesión con el responsable. Si había documentos de otra estructura, se recuerda que el siguiente paso es `migrar`.

## Lo que nunca hago

- Montar una raíz sin responsable de contexto con nombre y apellido
- Editar `metodo.md` al copiarlo, ni añadirle el nombre de la organización
- Crear una carpeta `metodo/`, un `AGENTS.md` o un índice
- Rellenar `contexto.md` con lo que parece razonable para una organización de ese tipo. Un hueco es un hueco
- Crear proyectos ni entregables
- Crear un área sin dueño
- Poner prefijos numéricos a nada
- Montar la raíz encima de una carpeta que ya tiene documentos sin haber avisado de que después toca `migrar`

## Ejemplo completo

**Usuario:** monta la carpeta para Acme, que empezamos con ellos el lunes

**Respuesta:**

> La carpeta conectada está vacía, así que monto la raíz desde cero. Cuatro preguntas:
>
> 1. ¿El nombre es Acme, o tiene otro nombre completo?
> 2. ¿Quién va a mantener `empresa/`, la parte de quién es Acme y qué usa?
> 3. ¿Qué sistemas usan a diario?
> 4. ¿Hay una primera área con la que empezar, y quién es su dueño?

**Usuario:** Acme Distribución. El contexto lo lleva Jorge Salas. Usan SAP para todo lo de compras y finanzas, HubSpot en comercial y Google Workspace. Empezamos por Compras, con Ana Pérez.

**Respuesta:**

> Montada la raíz de Acme Distribución: `guia.md` con el texto para Cowork y el párrafo para programadores, `metodo.md` en versión 1.2, `empresa/` con contexto, glosario, sistemas (tres filas: SAP, HubSpot, Google Workspace, con "quién da acceso" como hueco) y mantenimiento, las cuatro plantillas, y `compras/` con Ana Pérez como dueña.
>
> Dos siguientes pasos. Permisos en Drive: lectura de la raíz para todo el equipo, escritura en `empresa/` para Jorge y en `compras/` para Ana. Y una sesión con Jorge para rellenar `contexto.md`, que ahora mismo son cuatro huecos.
