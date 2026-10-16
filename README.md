# Fábrica de skills

Convierte cualquier tutorial en vídeo en una **skill para Claude Code**.

Tú le pasas un vídeo a [Watch](https://github.com/bradautomates/claude-video) (`/watch`), y la fábrica separa lo que el vídeo enseña del relleno, escribe el `SKILL.md` con los pasos y valores exactos, marca como **PENDIENTE** lo que falte y te enseña el borrador antes de instalar nada.

Guía completa, paso a paso: **[manulizama.com/skill](https://manulizama.com/skill)**

## Qué necesitas

- [Claude Code](https://code.claude.com/docs) instalado.
- [Watch](https://github.com/bradautomates/claude-video) para que Claude pueda ver vídeos (la guía explica cómo instalarlo en Windows y Mac).

## Instalación

Dentro de Claude Code, pega:

```text
/plugin marketplace add manulizamaoficial/fabrica-de-skills
/plugin install fabrica-de-skills@fabrica-de-skills
```

Abre una sesión nueva de Claude Code y ya está.

### Sin plugins (copiando la carpeta)

Si prefieres no usar el sistema de plugins, copia la carpeta `skills/fabrica-de-skills` dentro de `~/.claude/skills/`:

```bash
git clone https://github.com/manulizamaoficial/fabrica-de-skills.git
mkdir -p ~/.claude/skills
cp -r fabrica-de-skills/skills/fabrica-de-skills ~/.claude/skills/
```

En Windows (PowerShell):

```powershell
git clone https://github.com/manulizamaoficial/fabrica-de-skills.git
New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
Copy-Item -Recurse fabrica-de-skills\skills\fabrica-de-skills "$HOME\.claude\skills\"
```

## Cómo se usa

1. `/watch ENLACE ¿qué proceso enseña, paso a paso, con los valores exactos?`
2. `Usa fabrica-de-skills con lo que acabas de ver.`
3. Lee el borrador, corrige lo que no cuadre y rellena lo que haya quedado PENDIENTE.
4. Da el OK y Claude la instala en `~/.claude/skills/`.
5. Abre una conversación nueva y pide la tarea sin nombrar la skill. Si Claude la usa sola, la descripción está bien escrita.

## Qué hace (y qué no)

- ✅ Usa solo lo que el vídeo dice y muestra. Si no coinciden, manda lo que se ve en pantalla.
- ✅ Marca como PENDIENTE lo que falte en lugar de inventarlo.
- ✅ Prueba la descripción con 3 frases que deberían activarla y 3 que no.
- ✅ Te pide el OK antes de instalar y antes de sobrescribir.
- ❌ No guarda claves, contraseñas ni datos personales que salgan en el vídeo.
- ❌ No fabrica skills de vídeos que no enseñan un proceso repetible.

## Licencia

[MIT](LICENSE) © 2026 Manu Lizama · [@manulizamaes](https://www.instagram.com/manulizamaes/)
