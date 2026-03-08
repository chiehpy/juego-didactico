# Separa Residuos - Documento de Diseno

## Resumen

Juego educativo de separacion de residuos tipo drag & drop para totem vertical (1 jugador).
Tecnologia: Web (HTML5/CSS/JS) en un solo archivo. Sin dependencias externas.
Orientacion: Vertical (portrait, 1080x1920).

---

## 1. Flujo de Pantallas

```
[Pantalla de Inicio] --> [Pantalla de Juego] --> [Pantalla de Resultados]
       ^                                              |
       +---------------- "Jugar de nuevo" <-----------+
```

**Pantalla de Inicio:**
- Logo/titulo del juego
- Boton "JUGAR" grande y tactil
- Instrucciones breves: "Arrastra cada residuo al contenedor correcto"

**Pantalla de Juego:**
- Timer cuenta regresiva en la parte superior
- Score (aciertos/errores) visible
- Ficha de residuo actual en el centro (con imagen + nombre)
- 5 contenedores en la parte inferior (con colores e iconos)
- Drag & drop de la ficha hacia el contenedor

**Pantalla de Resultados:**
- Puntaje final (aciertos vs errores)
- Mensaje segun rendimiento ("Excelente!", "Buen trabajo!", "Sigue practicando!")
- Boton "JUGAR DE NUEVO"

---

## 2. Mecanicas de Juego

- **20 fichas** por partida (configurable)
- **60 segundos** de tiempo (configurable)
- Clasificacion correcta: **+1 punto**
- Clasificacion incorrecta: **-1 punto** (con feedback visual rojo)
- La partida termina cuando se acaba el tiempo O se clasifican todas las fichas
- Las fichas aparecen una a la vez en el centro de la pantalla
- Animacion de la ficha entrando al contenedor (correcta = verde, incorrecta = rojo + shake)

---

## 3. Los 5 Contenedores

| Color    | Categoria       | Ejemplos de residuos                          |
|----------|-----------------|-----------------------------------------------|
| Verde    | Organico        | Cascara de banana, restos de comida, hojas    |
| Azul     | Papel/Carton    | Periodico, caja de carton, hoja de papel      |
| Amarillo | Plastico/Metal  | Botella plastica, lata de aluminio, envase    |
| Blanco   | Vidrio          | Botella de vidrio, frasco, vaso roto          |
| Negro    | No Reciclable   | Panal, colilla, chicle, ceramica              |

---

## 4. Configuracion

Al inicio del archivo JS, un objeto configurable:

```js
const CONFIG = {
  totalTokens: 20,      // fichas por partida
  gameTime: 60,          // segundos
  correctPoints: 1,      // puntos por acierto
  penaltyPoints: -1,     // penalizacion por error
};
```

---

## 5. Layout Vertical (Portrait 1080x1920)

```
+------------------------+
|     (timer) 00:45      |
|     Score: 12          |
|                        |
|                        |
|    +--------------+    |
|    |  [imagen]    |    |
|    |  Cascara     |    |
|    |  de banana   |    |
|    +--------------+    |
|      (arrastrar)       |
|                        |
|  [ORG] [PAP] [PLA]    |
|     [VID]  [NOR]       |
|                        |
+------------------------+
```

Contenedores distribuidos en 2 filas:
- Fila 1: Organico, Papel/Carton, Plastico/Metal (3 contenedores)
- Fila 2: Vidrio, No Reciclable (2 contenedores centrados)

---

## 6. Aspectos Tecnicos

- **Rendering**: HTML/CSS con divs (no Canvas) - mejor para drag & drop touch
- **Touch**: touchstart, touchmove, touchend + fallback mouse para desarrollo
- **Drag & drop**: La ficha sigue el dedo/cursor, al soltar sobre un contenedor se evalua
- **Animaciones**: CSS transitions/animations para feedback visual
- **Responsive**: Escala proporcional al viewport manteniendo aspect ratio vertical
- **Sin dependencias externas**: Todo vanilla HTML/CSS/JS
- **Despliegue**: Abrir index.html en Chrome kiosk mode en el totem

---

## 7. Arquitectura: Single HTML File

Todo en un solo archivo `index.html` organizado en secciones:

1. `<style>` - Todos los estilos CSS
2. `<body>` - Estructura HTML de las 3 pantallas
3. `<script>` - Logica del juego:
   - CONFIG (parametros)
   - WASTE_DATA (fichas y sus categorias)
   - GameState (estado del juego)
   - Screen management (inicio/juego/resultados)
   - Drag & drop handlers (touch + mouse)
   - Timer & scoring
   - Animations & feedback
