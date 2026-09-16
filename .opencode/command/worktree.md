---
description: Crea un worktree de git en `.worktrees/<nombre>` usando el argumento dado.
---
Crea un worktree de git ejecutando **exclusivamente** este comando y nada más:

1. Toma el argumento recibido (`$ARGUMENTS`) como nombre del worktree.
2. Normaliza el nombre al contexto del proyecto:
   - Trim de espacios al inicio y final.
   - Reemplaza espacios (y otros caracteres no seguros para carpetas/ramas) por guiones `-`.
   - Convierte a minúsculas.
3. Ejecuta solo: `git worktree add .worktrees/<nombre-normalizado>`

Reglas estrictas:

- No hagas nada más: no cambies de directorio, no crees archivos, no edites nada, no agregues flags adicionales (`-b`, etc.).
- Si no recibes argumento, responde con el uso esperado sin ejecutar nada.