# Asteroids

Clon del clásico arcade **Asteroids** implementado en canvas HTML5 puro, sin dependencias ni bundler.

## Descripción

Nave espacial en un campo de asteroides con envolvimiento de bordes (el espacio es toroidal). Destruye asteroides para sumar puntos: los grandes se parten en medianos, los medianos en pequeños. Incluye power-ups especiales y tipos de asteroides únicos como la estrella fugaz.

## Tecnologías

- **HTML5 Canvas** — renderizado 2D
- **JavaScript (ES6+)** — lógica del juego en un solo archivo `game.js`
- Sin frameworks, sin bundler, sin dependencias

## Cómo correr

Abre `index.html` directamente en el navegador (doble clic), o usa un servidor local:

```bash
npx serve .
```

Luego visita `http://localhost:3000`.

## Controles

| Tecla     | Acción     |
| --------- | ---------- |
| `←` `→`   | Rotar nave |
| `↑`       | Propulsar  |
| `Espacio` | Disparar   |

## Puntuación

| Asteroide     | Puntos |
| ------------- | ------ |
| Grande        | 20     |
| Mediano       | 50     |
| Pequeño       | 100    |
| Estrella fugaz| 500    |

## Características

- 3 vidas con invencibilidad temporal al reaparecer (parpadeo)
- Asteroides se parten en fragmentos más pequeños al ser destruidos
- Partículas de explosión al destruir asteroides
- Power-ups al destruir asteroides: **velocidad** (aceleración ×2 por 5 s) y **triple-shot** (3 disparos paralelos por 5 s)
- Estrella fugaz: asteroide veloz que cruza la pantalla y desaparece por sí sola; destruirla da muchos puntos
- Power-ups que sueltan los asteroides al ser destruidos:
  - **Velocidad**: propulsión al doble durante 5 segundos
  - **Escudo**: burbuja que protege la nave de asteroides y estrellas fugaces durante 5 segundos (no acumulable)
