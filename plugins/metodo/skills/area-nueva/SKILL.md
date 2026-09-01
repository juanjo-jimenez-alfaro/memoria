---
name: area-nueva
description: Crea un area nueva en la raiz con su area.md y la anota en guia.md. Usala cuando digan 'nueva area', 'crea el area de...', 'necesitamos una carpeta para el equipo de...' o cuando un proyecto nuevo no tenga area donde vivir.
---

# Área nueva

Crear un área en la raíz: su carpeta, su `area.md` con la estructura fija y su línea en `guia.md`. Reglas de estructura y nombres: la skill `convenciones`.

## Cuándo

"Nueva área", "crea el área de operaciones", "necesitamos una carpeta para el equipo de marketing", o cuando `proyecto-nuevo` detecta que el área del dueño no existe.

Crear un área es una decisión organizativa, no una comodidad de archivo. Antes de crearla se dice en una línea: esto añade una capa de propiedad, con un dueño que responde por todo lo que hay dentro, y conviene que lo sepa el responsable de contexto. Si el usuario confirma, se sigue.

## Qué leo antes de escribir nada

1. `guia.md`: qué áreas hay ya. Si existe una parecida, se dice antes de crear nada
2. `empresa/contexto.md`: cómo se organiza la empresa, para que el área nueva encaje con cómo se llaman las cosas en la casa
3. `empresa/glosario.md`, para el nombre

## Las tres preguntas

Juntas, en una tanda:

1. ¿Quién es el dueño, la persona que responde por el área? Nombre y apellido
2. ¿Qué es el área, en dos o tres líneas?
3. ¿Qué tiene entre manos ahora? Tres a cinco prioridades

La pregunta 1 es bloqueante. Sin dueño con nombre y apellido no se crea el área. Las otras dos se rellenan con lo que haya y lo que falte queda marcado como hueco.

## Qué escribo y dónde

**1. La carpeta**, con nombre en minúsculas y guiones, en la raíz. Sin número delante.

**2. `area.md`**, con la estructura fija de `convenciones`, sección 2:

```markdown
---
estado: vigente
dueno: Marta Ruiz
actualizado: 2026-09-01
---

# Operaciones

## Qué es
[Lo que dijo el usuario, en dos o tres líneas]

## Prioridades ahora
[Tres a cinco líneas]

## Proyectos
[Vacío. Lo escriben proyecto-nuevo y el cierre de sesión]

## Quién participa
Dueño: Marta Ruiz
```

El bloque `Proyectos` queda vacío. No se crean proyectos al crear el área; eso lo hace `proyecto-nuevo` cuando haya uno.

**3. La línea del área en `guia.md`**, en la lista de áreas, con el mismo formato que las demás: nombre de la carpeta, qué es en media línea, y el dueño.

Nada más. Ni carpetas de proyecto vacías, ni plantillas, ni un `README`.

## Qué respondo al terminar

Dos líneas: qué se creó y quién es el dueño, y el recordatorio de que el dueño necesita permiso de escritura sobre la carpeta en Drive, porque eso no lo da la skill.

## Lo que nunca hago

- Crear un área sin dueño con nombre y apellido
- Crear un área sin decir antes que es una decisión organizativa
- Crear un área parecida a una que ya existe sin avisar
- Crear proyectos, carpetas o entregables dentro del área nueva
- Escribir en `guia.md` algo que no sea la línea del área en la lista
- Escribir en `empresa/`
- Poner en el nombre un número, una fecha o el nombre de una persona

## Ejemplo completo

**Usuario:** crea el área de operaciones, que vamos a arrancar el proyecto de logística ahí

**Respuesta:**

> Antes de crearla: un área es una capa de propiedad nueva, con un dueño que responde por todo lo que hay dentro, y conviene que el responsable de contexto lo sepa. Si sigues adelante, tres preguntas:
>
> 1. ¿Quién es el dueño?
> 2. ¿Qué es Operaciones, en dos o tres líneas?
> 3. ¿Qué tiene entre manos ahora?

**Usuario:** Marta Ruiz. Operaciones lleva almacén, transporte y la relación con los proveedores de logística. Ahora mismo: renegociar el contrato de transporte, reducir las roturas de stock y elegir proveedor de última milla.

**Respuesta:**

> Creada `operaciones/` con su `area.md`, dueña Marta Ruiz, y su línea en `guia.md`.
>
> Marta necesita permiso de escritura sobre `operaciones/` en Drive; eso lo da quien administra la carpeta. Cuando quieras, arrancamos el proyecto de logística con `proyecto-nuevo`.
