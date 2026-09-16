# Reglas de triaje de issues

Cuando trias un issue recién abierto de este repositorio (Asteroids, canvas HTML5 en un solo `game.js`), cumple estas reglas exactamente.

## Reglas obligatorias

- NO edites el cuerpo del issue ni el título. Todo lo que escribió la persona se mantiene tal cual.
- NO modifiques archivos del repositorio, no crees ramas ni PR. Si dejas cambios sin commitear, el action podría generar un PR: evítalo.
- No borres ni reescribas texto del autor.
- Tu mensaje final de texto se publica automáticamente como comentario de triaje. Haz que ese mensaje sea el comentario completo.

## 1. Etiquetas

Aplica un mínimo justificado, sin sobrecargar el issue.

- **Tipo (elige 1, rara vez 2)**: `bug` | `feature` | `enhancement` | `question` | `documentation` | `good-first-issue`
- **Prioridad (elige 1)**: `priority:high` | `priority:medium` | `priority:low`. Solo `high` si bloquea gameplay, renderizado o input crítico.
- **Área del juego (todas las que apliquen)**: `audio`, `gameplay`, `powerup`, `skin`, `rendering`, `input`, `scoring`, `visual`
- **Extra (solo si aporta valor claro)**: p. ej. `estrella-fugaz`. No inventes etiquetas genéricas que repitan una existente.

Crea las etiquetas que falten y aplícalas. No dependes de `GITHUB_TOKEN`: el token del App ya está en la configuración de git. Si `gh` no está autenticado, extrae el token así:

```bash
# Si gh no está autenticado, extrae el token del App desde la config de git:
gh auth status 2>/dev/null || export GH_TOKEN="$(
  git config --local --get http.https://github.com/.extraheader \
  | sed 's/^AUTHORIZATION: basic //' \
  | base64 -d \
  | sed 's/^x-access-token://'
)"

gh label create "bug" --force
gh issue edit <N> --add-label "bug" --add-label "gameplay"
```

El número `<N>` se obtiene de la rama actual (el action crea `opencode/issueN-<marca>`):

```bash
git branch --show-current
```

o, si lo prefieres, con `gh issue list --state open`.

## 2. Comentario de triaje (tu respuesta final)

En español y conciso, con estas secciones:

- **Etiquetas**: lista de etiquetas aplicadas.
- **Contexto en el código**: archivos y símbolos relevantes con ubicación `archivo:línea`, p. ej. la clase `Asteroid` (game.js), `split()`, constantes `RADII`/`SPEEDS`/`POINTS`, `Bullet`, `Ship`, el manejador de teclas (`keydown`), power-ups (escudo, velocidad, triple-shot), skins y `wrap()`. Cita solo lo que el issue menciona o afecta.
- **Severidad / prioridad**: sugerencia y justificación breve.
- **Para reproducir** (solo si es bug): pasos claros. Recuerda que no hay tests: la verificación es manual abriendo `index.html` o con `npx serve .` y visitando `http://localhost:3000`.
- **Criterios de aceptación** (opcional, breve).

No agregues advertencias sobre tokens, permisos ni flujos automáticos del action.