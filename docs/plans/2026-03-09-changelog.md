# Changelog - 2026-03-09

## Cambios realizados en esta sesion

### UI / Visual
- **Paleta de colores Duolingo**: Fondo verde (`#22c55e`), panel crema semitransparente, colores ludicos y kid-friendly
- **Screen panel**: Contenedor con fondo crema (`rgba(255,250,240,0.88)`), backdrop blur, glow negro (`box-shadow`)
- **Fondo mosaico**: Reemplazo de particulas flotantes por mosaico repetido con logo del Gobierno de Funes (180x180px, opacidad 100%)
- **Textos oscurecidos**: `--text-primary: #1A1A1A`, `--text-secondary: #2D2D2D`, `--text-muted: #2D2D2D`
- **Bins mas visibles**: Background de tachos subido a `rgba(0.18)`, bordes a `rgba(0.4)`
- **Bins responsive**: Padding, gap, imagen y label con `clamp()` para adaptarse a cualquier resolucion
- **Game wrapper fullscreen**: Sin max-width/max-height, ocupa 100% del body

### HUD (barra superior)
- **Logo Gobierno de Funes**: Centrado en el HUD entre Tiempo y Puntaje
- **Fichas**: Movido debajo de la progress bar, centrado
- **Tiempo y Puntaje agrandados**: `clamp(52px, 7vh, 72px)`
- **HUD items con min-width fijo**: Evita que el logo se mueva al cambiar los numeros del timer

### Iconos de residuos
- **Sistema de iconos PNG**: Cada item puede tener `icon` (ruta PNG) e `iconClass` para sizing custom
- **Clases de tamaño**: `icon-md` (30% mas grande), `icon-lg` (frasco de vidrio)
- **Clase `icon-outlined`**: Contorno negro con `drop-shadow` 2px, se mantiene al dragear
- **Caja de carton**: Icono cambiado a `open-box.png`
- **Libro**: Renombrado de "Revista" a "Libro"
- **Cuaderno viejo**: Icono `notebook.png` agregado
- **Items sin icono removidos temporalmente**: Envase de yogurt, Tapa plastica, Botella de jugo, Panal usado, Servilleta sucia, Sticker pegado

### Drag & Drop
- **Ghost con outline**: Si el item tiene `icon-outlined`, el ghost de drag tambien lo muestra
- **Deteccion por overlap-area**: Hit detection basado en area de solapamiento (min 400px²)
- **Shake en bins al hover**: Animacion binShake al arrastrar sobre un tacho

---

## Pendientes

### Iconos faltantes (6-7)
- [ ] Envase de yogurt → "yogurt cup"
- [ ] Tapa plastica → "bottle cap"
- [ ] Botella de jugo (vidrio) → "juice bottle"
- [ ] Panal usado → "diaper"
- [ ] Servilleta sucia → "napkin"
- [ ] Sticker pegado → "sticker"
- [ ] Cuaderno viejo → ya tiene icono

### Bloqueado (esperando assets/definicion del cliente)
- [ ] **Sistema de ranking** — Esperando definicion del cliente (premios, cantidad de ganadores)
- [ ] **Video idle (loop)** — Esperando video del Intendente/patrocinio
- [ ] **Video post-juego** — Esperando video de patrocinio/felicitaciones
- [ ] **Fondo personalizado branding** — Esperando asset 1080x1920

### Por hacer
- [ ] Punto 6: 1 solo logo en pantalla de juego (actualmente logo en HUD + mosaico fondo)
- [ ] Punto 9: Optimizar para touchscreen (parcialmente hecho)
- [ ] Agregar sonidos (acierto, error, fin de juego, countdown)
- [ ] Pantalla de instrucciones/tutorial

### Ultimo paso
- [ ] **Empaquetar como .exe con Electron** — Hacer cuando todo lo demas este listo
