# Separa Residuos - Objetivos y Pendientes

## Estado Actual

### Versiones del juego
- **1 Jugador** (`juego/index.html`) — Portrait (1080x1920), totem vertical
- ~~**2 Jugadores** (`juego/2jugadores.html`)~~ — **DESCARTADA**. Solo se usa version 1 jugador.

### Lo que ya funciona
- Drag & drop con soporte touch + mouse
- 4 categorías de residuos: Azul (Papel), Amarillo (Plásticos), Verde (Vidrio), Negro (No Reciclable)
- Imagen real de tacho (`bin.png`) recolorizada con CSS filters para los 4 colores
- 20 fichas por partida, 60 segundos, +1 acierto / -1 error (configurable en CONFIG)
- 3 pantallas: Inicio → Juego → Resultados
- Animaciones: entrada/salida de tokens, flash correcto/incorrecto, popup de puntaje, timer warning
- Contenido kid-friendly (público objetivo: niños)
- Labels blancos en todos los tachos

### ~~Versión 2 Jugadores~~ (DESCARTADA)
> Esta version ya no se usa. El proyecto continua solo con 1 jugador en totem vertical.

### Filtros CSS de los tachos (bin.png base verde)
| Tacho     | Filtro CSS |
|-----------|-----------|
| Azul      | `hue-rotate(60deg) saturate(1.5) brightness(1.1)` |
| Amarillo  | `saturate(0) sepia(1) hue-rotate(15deg) saturate(5) brightness(1.3)` |
| Verde     | `none` (color original) |
| Negro     | `saturate(0) brightness(0.7)` |

---

## Pendientes / A Implementar

### Alta Prioridad
- [ ] Aplicar efecto shake de hover-drag a la versión 1 jugador (ya está en 2 jugadores)
- [ ] Mejorar emojis/iconos de residuos — usar representaciones más realistas de basura cotidiana
- [ ] Testing completo de versión 2 jugadores en pantalla táctil real

### Media Prioridad
- [ ] Soporte orientación landscape en versión 1 jugador
- [ ] Agregar sonidos (acierto, error, fin de juego, countdown)
- [ ] Animaciones adicionales (confetti al ganar, partículas de fondo, efectos de entrada a pantallas)
- [ ] Pantalla de instrucciones/tutorial antes de empezar
- [ ] Ajustes visuales después de comparar lado a lado con el Ternium Separa original

### Baja Prioridad / Futuro
- [ ] Sistema de niveles o dificultad progresiva
- [ ] Más categorías de residuos (orgánico, electrónico, etc.)
- [ ] Tabla de puntajes / leaderboard local
- [ ] Modo práctica sin timer
- [ ] Personalización visual (logos corporativos, colores de marca)
- [ ] Exportar como PWA para instalar en totem sin navegador visible

---

## Estructura de Archivos
```
Ternium Separa V3/
├── juego/
│   ├── index.html          # Versión 1 jugador (portrait)
│   ├── 2jugadores.html     # Versión 2 jugadores (landscape)
│   └── bin.png             # Imagen del tacho (verde, se recoloriza con CSS)
├── docs/
│   ├── plans/              # Documentos de diseño
│   ├── bin-image.png       # Imagen original del tacho
│   ├── contenedores-colores-696x425.jpg  # Referencia visual
│   └── objetivos-y-pendientes.md         # Este archivo
├── Ternium Separa/         # Build original Unity (referencia)
└── _old_prototype/         # Primer prototipo (5 tachos, descartado)
```

## Tech Stack
- HTML5 / CSS3 / JavaScript vanilla (sin dependencias)
- Google Fonts: Lilita One + Outfit
- Servidor local: `npx http-server -p 8765` desde carpeta `juego/`
- Imágenes: PNG con fondo transparente + CSS filters para recolorizar
