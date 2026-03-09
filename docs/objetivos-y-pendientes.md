# Separa Residuos - Objetivos y Pendientes

## Estado Actual

### Versiones del juego
- **1 Jugador** (`juego/index.html`) — Portrait (1080x1920), totem vertical
- ~~**2 Jugadores** (`juego/2jugadores.html`)~~ — **DESCARTADA**. Solo se usa version 1 jugador.

### Lo que ya funciona
- Drag & drop con soporte touch + mouse (deteccion por overlap-area)
- 4 categorias de residuos: Azul (Papel), Amarillo (Plasticos), Verde (Vidrio), Negro (No Reciclable)
- Imagen real de tacho (`bin.png`) recolorizada con CSS filters para los 4 colores
- Tacho negro usa `bin-nopet.png` (sin simbolo PET)
- 20 fichas por partida, 60 segundos, +1 acierto / -1 error (configurable en CONFIG)
- 3 pantallas: Inicio → Juego → Resultados
- Animaciones: entrada/salida de tokens, flash correcto/incorrecto, popup de puntaje, timer warning, shake en bins
- Paleta de colores ludica estilo Duolingo (fondo verde, panel crema, colores brillantes)
- Iconos PNG de residuos (Flaticon) con sistema de sizing (`icon-md`, `icon-lg`, `icon-outlined`)
- Panel contenedor con glow negro y fondo mosaico con logo del Gobierno de Funes
- HUD con logo centrado, Tiempo y Puntaje a los lados, Fichas debajo de progress bar
- Game wrapper fullscreen (100% del body)
- Contenido kid-friendly (publico objetivo: ninos)

### Filtros CSS de los tachos (bin.png base verde)
| Tacho     | Filtro CSS |
|-----------|-----------|
| Azul      | `hue-rotate(60deg) saturate(1.5) brightness(1.1)` |
| Amarillo  | `saturate(0) sepia(1) hue-rotate(15deg) saturate(5) brightness(1.3)` |
| Verde     | `none` (color original) |
| Negro     | `saturate(0) brightness(0.7)` (usa `bin-nopet.png`) |

### Items de residuos actuales (20)
| Categoria | Items |
|-----------|-------|
| Papel (8) | Periodico, Caja de carton, Hoja de papel, Libro, Rollo de carton, Cuaderno viejo, Sobre de carta, Carton de huevos |
| Plastico (5) | Botella plastica, Lata de gaseosa, Bolsa plastica, Envase de shampoo, Lata de atun |
| Vidrio (3) | Botella de vidrio, Frasco de vidrio, Vaso de vidrio roto |
| No Reciclable (4) | Cascara de banana, Restos de comida, Esponja vieja, Cepillo de dientes |

---

## Pendientes / A Implementar

### Iconos faltantes
- [ ] Envase de yogurt (plastico)
- [ ] Tapa plastica (plastico)
- [ ] Botella de jugo (vidrio)
- [ ] Panal usado (no reciclable)
- [ ] Servilleta sucia (no reciclable)
- [ ] Sticker pegado (no reciclable)

### Bloqueado (esperando assets/definicion del cliente)
- [ ] Sistema de ranking — Esperando definicion del cliente
- [ ] Video idle loop — Esperando video del Intendente/patrocinio
- [ ] Video post-juego — Esperando video de patrocinio
- [ ] Fondo personalizado branding 1080x1920 — Esperando asset

### Por hacer
- [ ] 1 solo logo en pantalla de juego
- [ ] Optimizar para touchscreen (parcialmente hecho)
- [ ] Agregar sonidos (acierto, error, fin de juego, countdown)
- [ ] Pantalla de instrucciones/tutorial

### Ultimo paso
- [ ] Empaquetar como .exe con Electron

---

## Estructura de Archivos
```
Ternium Separa V3/
├── juego/
│   ├── index.html          # Version 1 jugador (portrait) - archivo principal
│   ├── bin.png             # Imagen del tacho (verde, se recoloriza con CSS)
│   ├── bin-nopet.png       # Imagen del tacho sin simbolo PET (para negro)
│   ├── logo-funes.png      # Logo Gobierno de Funes (HUD + mosaico fondo)
│   └── icons/              # Iconos PNG de residuos (Flaticon)
├── docs/
│   ├── plans/              # Documentos de diseno y changelog
│   ├── icons/              # Iconos originales descargados
│   └── objetivos-y-pendientes.md  # Este archivo
├── Ternium Separa/         # Build original Unity (referencia, gitignored)
└── _old_prototype/         # Primer prototipo (descartado, gitignored)
```

## Tech Stack
- HTML5 / CSS3 / JavaScript vanilla (sin dependencias)
- Google Fonts: Lilita One + Outfit
- Servidor local: `npx http-server -p 8765` desde carpeta `juego/`
- Imagenes: PNG con fondo transparente + CSS filters para recolorizar
- Iconos: PNG de Flaticon con sistema de clases CSS para sizing
