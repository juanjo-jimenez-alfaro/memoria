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
| `convenciones` | Contrato base: estructura, cabeceras, estados, cómo se lee, qué es público, qué es confidencial |
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

`guia.md` es para personas: qué es la carpeta, quién escribe dónde, qué áreas hay, cómo se avisa entre áreas, cuándo se revisa cada cosa, el texto para pegar en las instrucciones de un proyecto de Cowork y qué hacer si programas. `metodo.md` lo genera el plugin y nadie lo edita: reúne el contrato, el estilo y el índice de skills, para que funcionen también con Gemini o con quien abra la carpeta sin el plugin.

El número de versión vive en el plugin y en la primera línea de `metodo.md`. Al abrir sesión se comparan y se avisa si la raíz se quedó atrás; ponerla al día es regenerar `metodo.md` con `plugins/memoria/build-metodo.sh` y copiarlo a la raíz.

## La unidad confidencial

Toda la raíz la lee todo el equipo y dentro de ella no se restringe ninguna carpeta. Lo que no deba leer todo el equipo (datos personales, facturación, contratos, credenciales) va a una segunda unidad compartida, restringida, con acceso solo para los dueños de área que la necesiten: `<Organización> · Confidencial`. En el proyecto queda una fila en `fuentes/enlaces.md` con qué es, su liga y qué tener presente.

Las skills participan: cuando `donde-va`, `migrar`, `entregable` o el cierre de sesión detectan indicios de información sensible en un material, lo dicen y proponen llevarlo a la unidad confidencial. El usuario decide, y nada se mueve sin su confirmación.

## Versiones

**1.3.3** · Se corrige a quién pertenece el registro de una migración, que 1.3.2 había puesto del lado equivocado. Es de quien migra y va a su raíz, en el proyecto de la relación con esa organización: cuenta el trabajo del proveedor y habla de un sistema de origen que el equipo que estrena el método no usó nunca. En la raíz de la organización entra solo lo que su equipo necesita para operar, y donde se usa: las decisiones recuperadas en el `decisiones.md` de su proyecto, y el material confidencial pendiente en su `fuentes/enlaces.md`. Su raíz no guarda rastro del sistema de origen, ni en rutas ni en vocabulario. `migrar` lo suma a "lo que nunca hago".

**1.3.2** · El contrato dice ahora dónde vive la adopción del método por una organización, que "Independencia entre raíces" dejaba sin resolver: las auditorías, los planes de migración y los manifiestos son de la organización y van a su raíz, como proyecto dentro de un área que ya cruce áreas y que ya sea de su dueño; en la raíz de quien mantiene el método queda un proyecto por organización, nombrado por la organización y no por el trabajo, con solo el registro de la relación (qué se entregó, cuándo, con qué versión, qué falta) y sin entregables propios. `migrar` dice dónde se guarda el reporte y `nuevo` recuerda abrir el proyecto de la relación; los dos lo repiten en su lista de "lo que nunca hago".

**1.3.1** · Nueva sección en el contrato, "Independencia entre raíces": si una sesión tiene conectada más de una raíz a la vez, o una raíz y el repo del plugin, nada que se escriba en una usa hechos de otra; comparar la forma de dos raíces no es tocar su contenido, y lo que una organización guarda sobre otra se limita a lo operativo (qué se entregó y cuándo), nunca al contenido del trabajo. `migrar` y `donde-va` lo repiten en su lista de "lo que nunca hago".

**1.3** · `empresa/` pasa a llamarse `base/`: nombre más general, que sirve igual para una empresa, un equipo o un trabajo personal. Nuevo `base/ajustes.md`, opcional: una organización puede sumar ahí reglas propias (vocabulario adicional, criterios extra para lo confidencial, convenciones de nombres de área) sin tocar el plugin y sin poder contradecir el contrato; sigue el mismo principio que `base/plantillas/`, pero suma en vez de sustituir.

**1.2.1** · Lo migrado puede entrar `vigente` al migrar, sin pasar primero por revisión, si quien migra era el dueño del material en el origen y lo pide de forma explícita; `sesiones.md` deja constancia de por qué. No hay carpeta aparte para binarios: una presentación o una hoja de cálculo sin `.md` detrás va directo a `entregables/` (si es el producto) o a `fuentes/` (si es material de entrada), sin cabecera propia porque el formato no la admite; su estado y procedencia se anotan en `proyecto.md`. La convención venía de un sistema anterior que no podía previsualizar binarios; donde vive la raíz de la organización hoy (Drive, iCloud) ya los previsualiza.

**1.2** · El plugin pasa a llamarse `memoria`. Desaparece la carpeta `metodo/` de la raíz; en su lugar hay un `metodo.md` generado desde el plugin y un `guia.md` para personas que absorbe lo que antes era `mantenimiento.md` y trae el texto de cinco líneas para Cowork. La cabecera baja a tres claves: `estado`, `actualizado` y `basado_en` (antes `construido_a_partir_de`); el dueño vive en `area.md` y `proyecto.md`, no en una clave. `area.md` tiene estructura fija y su bloque Proyectos es el índice del área. Sección nueva en el contrato sobre cómo se lee la raíz por niveles. Formato único de decisiones con `Afecta a` entre áreas: al abrir sesión se barren las decisiones de toda la raíz y al cerrar se recuerda avisar. Lo confidencial va a una unidad compartida restringida, con su fila en `fuentes/enlaces.md`, y las skills lo detectan y proponen. Dentro de un área se citan fuentes de otros proyectos sin copiarlas; entre áreas solo entregables vigentes y decisiones. `empresa/sistemas.md` nuevo; `empresa/plantillas/` solo si la organización personaliza las del plugin. Las altas de organización, área y proyecto se funden en la skill `nuevo`; se añaden `consulta` y `migrar`. En estilo, umbral de guiones largos y cifras con fecha o fuente.

**1.1** · Desaparece la carpeta `borrador/`, que colisionaba con `estado: borrador`. Un entregable a medias vive en `entregables/` con ese estado, y el material sin clasificar en `fuentes/`. El dueño pasa a ser bloqueante al crear un proyecto.

**1.0** · Primera versión.
