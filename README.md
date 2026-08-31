# Método

Marketplace con el plugin `metodo`: el método de trabajo y documentación por proyecto.

Siete skills que escriben y mantienen una estructura de carpetas compartida en Drive, con sesiones, decisiones y entregables en Markdown.

## Instalación

En Claude Code, Claude Desktop o Cowork:

```
/plugin marketplace add <usuario>/<repo>
/plugin install metodo@metodo-marketplace
```

Para probar en local antes de publicar, desde la carpeta del repo:

```
/plugin marketplace add .
/plugin install metodo@metodo-marketplace
```

En una organización de Claude Team o Enterprise, el propietario puede distribuir el plugin a todos los usuarios sin que cada uno lo instale.

## Qué incluye

| Skill | Para qué |
|---|---|
| `convenciones` | Contrato base: estructura, cabeceras, estados, qué es público |
| `sesion` | Abrir y cerrar sesión de trabajo sobre un proyecto |
| `proyecto-nuevo` | Crear el paquete completo de un proyecto |
| `entregable` | Crear o actualizar un entregable |
| `revisar` | Revisar, detectar desfase y publicar |
| `donde-va` | Colocar material que llega en el sitio correcto |
| `estilo` | Normas de redacción, siempre activas |

## Cómo se usa con un cliente

Cada cliente tiene una raíz sincronizada en Drive, autocontenida, con `guia.md`, `metodo/` y `empresa/`. La carpeta `metodo/` lleva los mismos siete archivos que este plugin, en Markdown legible, para que funcionen también con Gemini o para quien abra la carpeta sin IA delante.

El número de versión vive en `convenciones.md`. Al abrir sesión se compara con la versión del cliente y se avisa si se quedó atrás.

## Versiones

**1.1** · Desaparece la carpeta `borrador/`, que colisionaba con `estado: borrador`. Un entregable a medias vive en `entregables/` con ese estado, y el material sin clasificar en `fuentes/`. El dueño pasa a ser bloqueante al crear un proyecto.

**1.0** · Primera versión.
