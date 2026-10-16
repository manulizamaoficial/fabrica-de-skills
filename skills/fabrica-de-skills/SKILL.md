---
name: fabrica-de-skills
description: Convierte lo que /watch (u otra transcripción) ha sacado de un vídeo en una skill nueva y reutilizable para Claude Code. Úsala cuando el usuario diga "usa fabrica-de-skills", "convierte este vídeo/tutorial en una skill", "haz una skill con lo que acabas de ver" o quiera guardar como skill el proceso que enseña un vídeo. No la uses para resumir vídeos ni para editar skills que no vengan de un vídeo.
---

# Fábrica de skills

Tu trabajo: a partir de lo que /watch ha extraído de un vídeo (fotogramas, transcripción y lo que se ve en pantalla), escribir una skill nueva y reutilizable. Nunca instalas nada sin el OK del usuario.

## Antes de empezar

- Si en la conversación no hay nada de un vídeo (ni salida de /watch ni transcripción), pide el enlace y sugiere: `/watch ENLACE ¿qué proceso enseña, paso a paso, con los valores exactos?`
- Si el vídeo no enseña un proceso repetible (es opinión, noticia o entretenimiento), dilo y no fabriques nada.
- Decide primero si esto debe ser una **skill**, un **subagente** o un **comando**, y dilo en dos líneas:
  - Skill: un método o criterio que Claude aplica dentro de la conversación (`~/.claude/skills/`).
  - Subagente: un trabajo largo que se puede delegar y devuelve solo el resultado (`.claude/agents/`).
  - Comando: una receta fija que siempre se hace igual (`.claude/commands/`).
  Si no es una skill, explícalo y pregunta antes de seguir.

## Cómo trabajar

1. **Separa tres cosas**: lo que el vídeo DICE, lo que MUESTRA en pantalla y lo que solo es relleno o promoción. Usa solo las dos primeras.
2. **Si lo dicho y lo mostrado no coinciden**, quédate con lo mostrado y anótalo en la sección «Notas del vídeo».
3. **Escribe el SKILL.md** con esta estructura:
   - Cabecera con `name` (minúsculas y guiones, máximo 64 caracteres) y `description` de una o dos frases que diga QUÉ hace y CUÁNDO usarla, empezando por «Úsala cuando…» o incluyéndolo.
   - Requisitos (programas, cuentas, permisos).
   - Pasos numerados con los comandos y valores exactos, tal como aparecen en el vídeo.
   - Cómo comprobar que ha salido bien.
   - Errores típicos y cómo resolverlos.
   - Notas del vídeo: enlace, autor y contradicciones encontradas.
4. **No inventes nada** que no esté en el vídeo. Si falta un dato (un valor, un menú, una versión), escríbelo como `PENDIENTE: qué falta` y sigue.
5. **No guardes claves, contraseñas, tokens ni datos personales** que aparezcan en pantalla. Sustitúyelos por marcadores como `TU_CLAVE`.
6. **Prueba la descripción antes de instalar**: escribe 3 frases con las que SÍ debería activarse y 3 con las que NO, y comprueba que la descripción las separa bien. Si no, reescríbela.
7. **Enséñale el borrador al usuario** (el SKILL.md completo, la lista de PENDIENTES y las 6 frases de prueba) y espera su OK.
8. Con el OK, instálala en `~/.claude/skills/NOMBRE/SKILL.md`. Si ya existe una carpeta con ese nombre, pregunta antes de sobrescribirla.
9. Al terminar, dile que abra una conversación nueva y pida la tarea **sin nombrar la skill**: si Claude la usa sola, la descripción está bien escrita.

Si la skill `skill-creator` está instalada, úsala para revisar el formato antes del paso 7.

## Plantilla

```markdown
---
name: nombre-de-la-skill
description: Qué hace en una frase. Úsala cuando el usuario quiera… (y no cuando…).
---

# Título

## Requisitos
- …

## Pasos
1. …

## Cómo comprobar que ha salido bien
- …

## Errores típicos
| Lo que pasa | Solución |
| --- | --- |
| … | … |

## Notas del vídeo
- Fuente: ENLACE (autor)
- PENDIENTE: …
```
