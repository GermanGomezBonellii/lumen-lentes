# Lumen · Lentes inteligentes de alfabetización (prototipo)

Prototipo web de unos lentes inteligentes (Diseño de Futuros, Educación, escenario 2060). Es un asistente de voz que acompaña la práctica de **lectura** y de **matemáticas y números**, estima atención, fatiga, frustración y confusión con la cámara, y da diagnósticos y recomendaciones **hablados**. Un único archivo: `index.html`.

## Cómo abrirlo (importante para el micrófono)
Chrome **bloquea el reconocimiento de voz** si abrís el HTML con doble clic (`file://`). Opciones:
1. **Windows:** doble clic en `abrir-lumen.bat` (levanta `http://localhost:8000` con Python y lo abre en Chrome o Edge).
2. **GitHub Pages:** subí `index.html` a un repo → Settings → Pages → `main` / root → `https://<usuario>.github.io/<repo>/`.

Usá **Chrome o Edge de verdad** (no el navegador integrado de la app de escritorio, que no trae el motor de voz) con internet (el reconocimiento de voz y los modelos de MediaPipe se descargan de la red). En el panel hay un botón **Probar micrófono** que prueba en dos pasos (1: el micrófono capta sonido; 2: el reconocedor de voz devuelve texto) y muestra una línea de diagnóstico (inició / audio / sonido / voz / texto). Si el paso 1 anda y el 2 no, cambiá el *idioma de voz* (es-ES, es-MX) o el micrófono predeterminado de Windows, y cerrá apps que lo usen (Teams, Zoom, Discord). Lumen no mantiene el micrófono abierto mientras reconoce, porque en algunos equipos eso deja sordo al reconocedor.

## Flujo
1. Iniciar (con cámara o modo demo). Por defecto entra en **pantalla completa** (también con el botón ⛶ o la tecla **F**; **Esc** sale).
2. El asistente pregunta con voz: **“¿Hoy qué querés practicar?”**. Se responde diciendo *matemáticas y números* o *lectura*, tocando la opción, o con la mano (pellizco o mantener 1 s sobre un botón).
3. **Lectura:** aparece el texto y el micrófono evalúa en vivo: palabras bien, reintentos, omisiones, pausas (>2 s) y trabas (>4,5 s). Si se traba, el asistente dice la palabra por sílabas.
4. **Matemáticas:** 6 cuentas que se adaptan al nivel; se responde en voz alta o tocando. Si se traba más de 9 s da una pista hablada.
5. Al terminar: **diagnóstico y recomendaciones habladas**, y pregunta si repetir, cambiar de actividad o terminar (también por voz).

En pantalla completa no se muestran las métricas: solo la cámara, el asistente (subtítulos + voz) y los diagnósticos. Las métricas completas, el gráfico y los CSV quedan en el panel de la página.

## Para el test de usabilidad
ID de participante y tarea (T1–T6) en el panel; exportación de **sesión** (1 fila por segundo) y de **práctica** (1 fila por palabra o cuenta).

## Límites
- Métricas heurísticas, sin validación clínica ni cultural.
- El reconocedor de voz tiende a autocorregir: detecta bien silencios, omisiones y trabas, no tanto errores finos de pronunciación.
- La voz del asistente usa las voces en español instaladas en el navegador/sistema (en Chrome, las “Google español” suenan mejor).


## Novedades v4
- **Estado inicial:** al ponerte los lentes la cámara muestra en vivo tu estado (concentrado, distraído, fatigado, frustrado, confundido), el ánimo y las emociones básicas. Tocá **Iniciar actividad** o decí «iniciar actividad» para que la asistente ofrezca **matemáticas y números** o **lectura**.
- **Micrófono:** por defecto se pausa mientras la asistente habla (más estable). Con auriculares podés tildar «Escuchar mientras la asistente habla» en el panel.
- **Diagnóstico:** al terminar, además del desempeño, se muestra y se dice un análisis de atención, frustración, confusión, fatiga y ánimo predominante, con una línea de tiempo.
- La lectura se ayuda del volumen de voz cuando el reconocedor se atrasa; las respuestas numéricas toleran errores de transcripción.

## Novedades v5
- Nuevo estilo: aura de color en el borde según tu estado, caras que marcan la emoción, filamentos y arcos de atención/fatiga/frustración/confusión, botones con íconos y menos texto.
- Emociones: puntajes relativos a tu cara neutra, suavizados y sin parpadeo de etiquetas.
