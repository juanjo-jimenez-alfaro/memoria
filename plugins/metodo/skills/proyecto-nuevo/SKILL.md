---
name: proyecto-nuevo
description: Crea el paquete completo de un proyecto nuevo. Usala cuando digan 'nuevo proyecto', 'arranca un proyecto para...', 'necesito documentar esto como proyecto', o cuando se trabaje en algo que todavia no tiene carpeta.
---

# Proyecto nuevo

Crear el paquete completo de un proyecto. Reglas de estructura, cabecera y nombres: `metodo/convenciones.md`.

## Cuándo

"Nuevo proyecto", "arranca un proyecto para X", "necesito documentar esto como proyecto", o cuando alguien empieza a trabajar en algo que todavía no tiene carpeta.

También cuando una conversación de trabajo lleva veinte minutos sobre algo que no existe en ninguna carpeta. En ese caso se propone crear el proyecto, no se crea sin avisar.

## Qué leo antes de escribir nada

1. `empresa/contexto.md` y `empresa/glosario.md`
2. `<area>/area.md`, si el área ya existe
3. Los nombres de los proyectos que ya hay en esa área, para no duplicar

Si el proyecto se parece a uno existente, se dice antes de crear nada. Dos proyectos sobre el mismo tema son la forma más rápida de romper el sistema.

## Las cinco preguntas

Se hacen todas juntas, en una sola tanda, en lenguaje llano. Nadie tiene que saber qué es un alcance ni un entregable para responderlas.

1. ¿Qué problema resuelve y para quién?
2. ¿Cómo sabremos que está terminado?
3. ¿Quién es el dueño, la persona que responde por esto?
4. ¿Quién más va a usar lo que salga de aquí?
5. ¿Qué material ya existe? Documentos, exports, correos, grabaciones.

Si el usuario responde a medias, se crea igual con lo que haya y se anota lo que falta en los siguientes pasos. Un proyecto a medio encuadrar es mejor que una conversación sin carpeta.

La excepción es la pregunta 3. Sin un dueño con nombre y apellido no se crea el proyecto, se pide el nombre y se espera.

Si el área no existe todavía, se pregunta aparte antes de crearla. Crear un área es una decisión organizativa del cliente, no del proyecto.

## Qué escribo y dónde

**1. La carpeta**, con nombre en minúsculas y guiones, dentro del área del dueño.

**2. `proyecto.md`**, con la estructura fija de `metodo/convenciones.md`, sección 3. Se rellena con las respuestas a las cinco preguntas: `Estado actual` queda como "arrancando" y `Siguientes pasos` recoge lo que salga de la conversación de arranque.

Las secciones que no se hayan podido responder se dejan escritas con el hueco marcado, nunca se borran ni se rellenan con supuestos.

**3. `decisiones.md`**, con cabecera y solo el título. Vacío de entradas: en el arranque casi nunca hay decisiones todavía, y las que hay se registran al cerrar la primera sesión.

**4. `sesiones.md`**, con la entrada de arranque:

```markdown
## 2026-08-29
Trabajamos en: arranque del proyecto.
Avances: encuadre definido con Ana Pérez.
Pendiente: reunir los exports del ERP.
```

**5. Las dos carpetas** `entregables/` y `fuentes/`, vacías.

**6. El material existente** se mueve a `fuentes/` con nombres legibles, si el usuario lo tiene a mano. Si no, queda como siguiente paso.

## Qué respondo al terminar

El nombre de la carpeta creada y el primer siguiente paso. Dos líneas.

## Lo que nunca hago

- Crear un proyecto sin dueño con nombre y apellido
- Crear un cuarto nivel de carpeta
- Crear una carpeta de borradores
- Crear entregables vacíos "para ir rellenando"
- Inventar alcance, plazos o participantes que nadie mencionó
- Crear un proyecto en un área que no es la del dueño
- Crear un área sin preguntar
- Duplicar un proyecto existente sin avisar antes

## Ejemplo completo

**Usuario:** vamos a arrancar un proyecto para automatizar las órdenes de compra

**Respuesta:**

> En `compras/` no hay nada parecido, así que arrancamos limpio. Cinco preguntas y lo creo:
>
> 1. ¿Qué problema resuelve y para quién?
> 2. ¿Cómo sabremos que está terminado?
> 3. ¿Quién es el dueño?
> 4. ¿Quién más va a usar lo que salga?
> 5. ¿Qué material ya existe?

**Usuario:** las aprobaciones manuales tardan días y frenan a operaciones. Terminado cuando las órdenes bajo cierto monto se aprueben solas en el ERP. Dueña Ana Pérez. Lo usarán Finanzas y Sistemas. Tengo un export de órdenes del último año y la grabación de la reunión con Ana.

**Respuesta:**

> Creado `compras/automatizacion-ordenes/` con el paquete completo.
>
> El primer siguiente paso es meter el export y la grabación en `fuentes/`. Pásamelos cuando puedas y los coloco con nombres legibles.
