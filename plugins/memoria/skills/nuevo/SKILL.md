---
name: nuevo
description: Da de alta lo que falte en la memoria de la organizacion: monta la raiz si la carpeta no tiene guia.md, crea el area si no existe y crea el paquete completo de un proyecto. Usala cuando digan 'nuevo proyecto', 'arranca un proyecto para...', 'necesito documentar esto como proyecto', 'nueva area', 'crea el area de...', 'monta la carpeta de...', 'nueva organizacion', 'arranca el metodo para este cliente', o cuando se trabaje en algo que todavia no tiene carpeta.
---

# Nuevo

Dar de alta lo que falte, de fuera hacia dentro: la raíz de la organización, el área, el proyecto. La skill detecta en qué nivel está la carpeta conectada y empieza por ahí. Reglas de estructura, cabecera y nombres: la skill `convenciones`.

## Cuándo

"Nuevo proyecto", "arranca un proyecto para X", "necesito documentar esto como proyecto", "nueva área", "crea el área de operaciones", "monta la carpeta de Acme", "nueva organización", "arranca el método para este cliente", o cuando alguien empieza a trabajar en algo que todavía no tiene carpeta.

También cuando una conversación de trabajo lleva veinte minutos sobre algo que no existe en ninguna carpeta. En ese caso se propone crear el proyecto, no se crea sin avisar.

## Qué leo antes de escribir nada

1. La carpeta conectada: si tiene `guia.md`. Si no lo tiene, falta la raíz y se empieza por el nivel 1. Si tiene documentos de otra estructura, se para y se propone `migrar` después de montar la raíz
2. `guia.md`: qué áreas hay y quién responde por cada una. Si el área del dueño no está, falta el área y se pasa por el nivel 2
3. `empresa/contexto.md` y `empresa/glosario.md`
4. `<area>/area.md`, su bloque `Proyectos`: qué proyectos hay ya y qué entregables vigentes tienen

Si el proyecto se parece a uno existente, se dice antes de crear nada. Dos proyectos sobre el mismo tema son la forma más rápida de romper el sistema. Lo mismo con un área parecida a otra.

Las preguntas de cada nivel se hacen juntas, en una sola tanda, en lenguaje llano. Nadie tiene que saber qué es un alcance ni un entregable para responderlas. Si el usuario responde a medias, se crea igual con lo que haya y lo que falta queda marcado como hueco. La única excepción son las preguntas de dueño y de responsable de contexto: sin nombre y apellido no se crea nada, se pide y se espera.

---

# Nivel 1. La raíz

Solo si la carpeta no tiene `guia.md`. Se hace una vez por organización.

## Las cuatro preguntas

1. ¿Cómo se llama la organización?
2. ¿Quién es el responsable de contexto, la persona que mantiene `empresa/`? Nombre y apellido. Bloqueante
3. ¿Qué sistemas usan a diario? Nombre y para qué, aunque sea una lista rápida
4. ¿Hay ya una primera área con la que empezar, y quién es su dueño?

## Qué escribo y dónde

**1. `guia.md`.** Para personas, sin cabecera de método:

```markdown
# [Organización] · cómo trabajamos con esta carpeta

## Qué es esto
Esta carpeta es la memoria de trabajo de [organización]. Cada área documenta sus proyectos
aquí, en archivos de texto, y la IA lee esta carpeta antes de ayudar a cualquiera.
Las reglas completas están en `metodo.md`. No hace falta leerlas para empezar: las aplica
el plugin `memoria` cuando trabajas con Claude.

## Cómo se organiza y quién escribe dónde
`empresa/` es quién somos y qué usamos. Lo escribe solo [responsable de contexto].
Cada carpeta de área es de su dueño; nadie más escribe en ella. Dentro, cada proyecto
tiene su carpeta con `proyecto.md`, `decisiones.md`, `sesiones.md`, `entregables/` y `fuentes/`.
Toda la carpeta la lee todo el equipo. Lo que no deba leer todo el equipo no entra aquí.

## Lo confidencial
Datos personales, facturación, contratos, credenciales o cualquier cosa que no todos deban
ver van a la unidad compartida `[Organización] · Confidencial`, con acceso solo para los
dueños de área que la necesiten. En el proyecto queda una fila en `fuentes/enlaces.md` con
qué es, su liga y qué tener presente. Si la IA detecta algo que parece confidencial, lo dice
y propone moverlo; la decisión es tuya.

## Áreas
- `[area]/` · [qué es en media línea] · [dueño]

## Cómo se avisa entre áreas
La carpeta no notifica a nadie. Cuando una decisión afecta a otra área, queda anotada en
`Afecta a` y al cerrar sesión la IA te recuerda avisar a su dueño. Al abrir sesión, la IA
te muestra las decisiones de otras áreas que afectan a tu proyecto.

## Cuándo se revisa cada cosa
`empresa/contexto.md` al menos cada 90 días; la IA avisa si se pasa. Un entregable que
lleva más de 30 días en borrador o en revisión aparece como aviso al abrir sesión.
Un registro que pasa de 1.500 líneas o cambia de año se archiva con el año en el nombre.
Un archivo suelto en la raíz o en la carpeta de un área se coloca o se quita; nunca se queda.

## Versión del método
La primera línea de `metodo.md` dice la versión. Si al abrir sesión la IA avisa de que la
carpeta se quedó atrás, [responsable de contexto] vuelve a copiar `metodo.md` desde el plugin.

## Cómo conectarla a un proyecto de Cowork
Crea un proyecto en Cowork, conecta esta carpeta e instala el plugin `memoria`.
Pega este texto en las instrucciones del proyecto, cambiando el área:

    Esta carpeta es la memoria de la organización y sigue el método del plugin `memoria`; úsalo en todo lo que hagas aquí.
    Lee `guia.md` al empezar.
    Trabajo en el área `<area>`. No escribas en `empresa/` ni en la carpeta de otra área.
    No des por aprobado ningún documento ni edites lo ya registrado en decisiones o sesiones.
    Antes de guardar algo, pregúntate si alguien más lo va a leer y si contiene datos que no todos deben ver.

## Si usas otro modelo
Gemini u otro modelo sin el plugin: pídele que lea `metodo.md` al empezar. Contiene las
reglas, el estilo y lo que hace cada skill.

## Si programas
El `CLAUDE.md` de tu repositorio enlaza la carpeta del proyecto en esta raíz, como
`area/proyecto`. Las decisiones de código que dependen de un diseño se anclan en el
`decisiones.md` y en los entregables vigentes de ese proyecto, no en comentarios del
código. Antes de decidir algo que ya pudo decidir otra área, pregunta qué se sabe.
```

**2. `metodo.md`.** Copia exacta del `metodo.md` del plugin, que está en la raíz de la carpeta del plugin, dos niveles por encima de esta skill. No se edita ni una línea: su primera línea lleva la versión del método y es lo que `sesion` compara al abrir.

**3. `empresa/contexto.md`.** Esqueleto con las secciones y cada una con su hueco marcado, para que el responsable de contexto las rellene con la IA en su primera sesión:

```markdown
---
estado: borrador
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
[Hueco: qué tipos de datos van a la unidad confidencial, qué no se cita en entregables, qué no se comparte fuera del área]
```

**4. `empresa/glosario.md`.** Cabecera, título y una lista vacía con el formato `término: qué significa`. Si el usuario dio siglas o nombres internos al responder, se meten ya.

**5. `empresa/sistemas.md`.** Cabecera, título y la tabla con sus cuatro columnas, con las filas de la pregunta 3 si las hubo:

```markdown
| Sistema | Para qué | Quién da acceso | Antes de usarlo |
|---|---|---|---|
```

**6. La primera área**, si la hay, por el nivel 2. Si no la hay, la lista de áreas de `guia.md` queda con una línea que dice que todavía no hay ninguna.

No se crea `empresa/plantillas/`: las plantillas viven en el plugin, junto a esta skill. Solo se crea si la organización quiere las suyas, y entonces manda sobre la del plugin.

## Qué respondo al terminar

Tres o cuatro líneas: qué se creó, quién es el responsable de contexto, y los siguientes pasos: permisos en Drive (lectura de la raíz a todo el equipo, escritura en `empresa/` al responsable de contexto), crear la unidad `[Organización] · Confidencial` con acceso solo a los dueños de área, y rellenar `contexto.md` en una primera sesión con el responsable. Si había documentos de otra estructura, se recuerda que el siguiente paso es `migrar`.

---

# Nivel 2. El área

Solo si el área del dueño no está en `guia.md`.

Antes de crearla se dice en una línea: un área es una capa de propiedad nueva, con un dueño que responde por todo lo que hay dentro, y conviene que lo sepa el responsable de contexto. Si el usuario confirma, se sigue.

## Las tres preguntas

1. ¿Quién es el dueño, la persona que responde por el área? Nombre y apellido. Bloqueante
2. ¿Qué es el área, en dos o tres líneas?
3. ¿Qué tiene entre manos ahora? Tres a cinco prioridades

## Qué escribo y dónde

**1. La carpeta**, con nombre en minúsculas y guiones, en la raíz. Sin número delante.

**2. `area.md`**, con la estructura fija de `convenciones`, sección 2:

```markdown
---
estado: vigente
actualizado: 2026-09-01
---

# Operaciones

## Qué es
[Lo que dijo el usuario, en dos o tres líneas]

## Prioridades ahora
[Tres a cinco líneas]

## Proyectos
[Vacío. Lo escriben esta skill al crear un proyecto y el cierre de sesión]

## Quién participa
Dueño: Marta Ruiz
```

**3. La línea del área en `guia.md`**, en la lista de áreas, con el mismo formato que las demás.

Nada más: ni proyectos vacíos, ni plantillas, ni un `README`.

## Qué respondo al terminar

Dos líneas: qué se creó y quién es el dueño, y el recordatorio de que el dueño necesita permiso de escritura sobre la carpeta en Drive y, si va a manejar material confidencial, acceso a la unidad confidencial. Eso no lo da la skill.

---

# Nivel 3. El proyecto

## Las cinco preguntas

1. ¿Qué problema resuelve y para quién?
2. ¿Cómo sabremos que está terminado?
3. ¿Quién es el dueño, la persona que responde por esto? Nombre y apellido. Bloqueante
4. ¿Quién más va a usar lo que salga de aquí?
5. ¿Qué material ya existe? Documentos, exports, correos, grabaciones, enlaces

Un proyecto a medio encuadrar es mejor que una conversación sin carpeta.

## Qué escribo y dónde

**1. La carpeta**, con nombre en minúsculas y guiones, sin número de fase ni de etapa, dentro del área del dueño.

**2. `proyecto.md`**, con la estructura fija de `convenciones`, sección 3. Se rellena con las respuestas: `Quién participa` lleva al dueño, `Estado actual` queda como "arrancando" y `Siguientes pasos` recoge lo que salga de la conversación de arranque. Las secciones sin respuesta se dejan con el hueco marcado, nunca se borran ni se rellenan con supuestos.

**3. `decisiones.md`**, con cabecera y solo el título. Vacío de entradas: las que haya se registran al cerrar la primera sesión.

**4. `sesiones.md`**, con la entrada de arranque:

```markdown
## 2026-08-29
Trabajamos en: arranque del proyecto.
Avances: encuadre definido con Ana Pérez.
Pendiente: reunir los exports del ERP.
```

**5. Las dos carpetas** `entregables/` y `fuentes/`, vacías.

**6. El material existente** se mueve a `fuentes/` con nombres legibles, si el usuario lo tiene a mano. Si no, queda como siguiente paso. Los enlaces van a `fuentes/enlaces.md`, una fila por enlace; ese archivo solo se crea si hay filas. Antes de guardar cada archivo se mira si trae indicios de información confidencial (nombres con RFC, CURP o NSS, facturación por cliente, contratos, contraseñas, datos de salud, salarios); si los trae, se dice y se propone llevarlo a la unidad confidencial con su fila en `enlaces.md`. El usuario decide.

**7. La línea del proyecto en el bloque `Proyectos` de `area.md`**: `` `nombre-del-proyecto/` — qué es ``, sin entregables debajo porque todavía no hay ninguno vigente. Es lo único que se toca de `area.md`.

## Qué respondo al terminar

El nombre de la carpeta creada y el primer siguiente paso. Dos líneas.

---

## Lo que nunca hago

- Crear una raíz sin responsable de contexto, un área o un proyecto sin dueño, todos con nombre y apellido
- Crear un área sin decir antes que es una decisión organizativa
- Montar la raíz encima de una carpeta con documentos sin avisar de que después toca `migrar`
- Editar `metodo.md` al copiarlo
- Crear `empresa/plantillas/`, una carpeta `metodo/`, un `AGENTS.md`, un índice a mano o una carpeta de borradores
- Rellenar `contexto.md` con lo que parece razonable para una organización de ese tipo
- Crear un cuarto nivel de carpeta, entregables vacíos "para ir rellenando" o `fuentes/enlaces.md` sin filas
- Guardar en `fuentes/` un archivo con indicios de información confidencial sin preguntar antes
- Inventar alcance, plazos o participantes que nadie mencionó
- Crear un proyecto en un área que no es la del dueño
- Tocar de `area.md` o de `guia.md` algo que no sea la línea nueva
- Duplicar un proyecto o un área existente sin avisar antes

## Ejemplo completo

**Usuario:** vamos a arrancar un proyecto para automatizar las órdenes de compra

**Respuesta:**

> En `guia.md` está Compras con Ana Pérez como dueña, y en `compras/area.md` hay dos proyectos que no se parecen, así que solo falta el proyecto. Cinco preguntas y lo creo:
>
> 1. ¿Qué problema resuelve y para quién?
> 2. ¿Cómo sabremos que está terminado?
> 3. ¿Quién es el dueño?
> 4. ¿Quién más va a usar lo que salga?
> 5. ¿Qué material ya existe?

**Usuario:** las aprobaciones manuales tardan días y frenan a operaciones. Terminado cuando las órdenes bajo cierto monto se aprueben solas en el ERP. Dueña Ana Pérez. Lo usarán Finanzas y Sistemas. Tengo un export de órdenes del último año, la grabación de la reunión con Ana, el enlace a la documentación del ERP y un Excel con los sueldos del equipo para calcular el tope.

**Respuesta:**

> Creado `compras/automatizacion-ordenes/` con el paquete completo, y su línea en `compras/area.md`. El enlace del ERP ya está en `fuentes/enlaces.md`.
>
> El Excel de sueldos trae nombres con salario, así que no lo guardo en `fuentes/`. Si lo confirmas, va a `Acme · Confidencial` y dejo su fila en `enlaces.md` con la nota de que a los entregables solo sale el total agregado. ¿Lo tratamos como confidencial?

**Usuario:** sí

**Respuesta:**

> Hecho. Queda por meter el export y la grabación en `fuentes/`; pásamelos cuando puedas y los coloco con nombres legibles.

---

**Usuario:** monta la carpeta para Acme, que empezamos con ellos el lunes

**Respuesta:**

> La carpeta conectada no tiene `guia.md`, así que monto la raíz desde cero. Cuatro preguntas:
>
> 1. ¿El nombre es Acme, o tiene otro nombre completo?
> 2. ¿Quién va a mantener `empresa/`, la parte de quién es Acme y qué usa?
> 3. ¿Qué sistemas usan a diario?
> 4. ¿Hay una primera área con la que empezar, y quién es su dueño?

**Usuario:** Acme Distribución. El contexto lo lleva Jorge Salas. Usan SAP para compras y finanzas, HubSpot en comercial y Google Workspace. Empezamos por Compras, con Ana Pérez.

**Respuesta:**

> Montada la raíz de Acme Distribución: `guia.md` con el texto para Cowork, `metodo.md` en versión 1.2, `empresa/` con contexto, glosario y sistemas (tres filas, con "quién da acceso" como hueco), y `compras/` con Ana Pérez como dueña.
>
> Tres siguientes pasos. Permisos en Drive: lectura de la raíz para todo el equipo, escritura en `empresa/` para Jorge y en `compras/` para Ana. Crear la unidad `Acme Distribución · Confidencial` con acceso para Ana. Y una sesión con Jorge para rellenar `contexto.md`, que ahora mismo son cuatro huecos.
