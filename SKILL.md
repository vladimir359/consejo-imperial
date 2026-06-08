---
name: consejo-imperial
description: >-
  Consejo Imperial de deliberación (LLM Council, versión "solo Claude"). Convoca a 8
  consejeros con perspectivas independientes —escéptico, factibilidad, usuario, riesgos,
  largo plazo, costo, ética y abogado del diablo—, los hace deliberar por separado,
  revisarse entre sí de forma anónima, y un Sintetizador Supremo funde todo en UN solo
  veredicto razonado. Úsalo para decisiones difíciles con incertidumbre real (estrategia,
  arquitectura, trade-offs, elegir entre caminos), NO para tareas mecánicas simples.
  Se activa cuando el usuario dice "convoco al consejo", "eleva esto al consejo",
  "pásalo por el consejo", "deliberá", "delibera esto", "council this" o "pressure-test this".
---

# El Consejo Imperial

Un protocolo de deliberación multi-perspectiva. En vez de responder con un solo ángulo,
convocas a un consejo de 8 asesores que analizan la decisión de forma independiente, se
critican entre sí, y un sintetizador final entrega un único veredicto coherente.

> **Por qué existe:** una sola línea de razonamiento ancla en su primera idea. Forzar
> 8 frentes distintos + autocrítica reduce puntos ciegos y errores. El paso final de
> síntesis es obligatorio: sin él solo quedarían 8 opiniones sueltas = ruido.

## Cuándo activarlo

- **Sí:** decisiones con incertidumbre genuina y trade-offs reales — estrategia,
  arquitectura técnica, "¿qué enfoque conviene?", revisar si una idea tiene fallas,
  decisiones difíciles de revertir.
- **No:** tareas concretas y mecánicas (renombrar, editar un texto, un cálculo directo,
  buscar un dato). Ahí, responde normal: un consejo solo añade demora.

Si el usuario no usó una frase gatillo, **no** convoques el consejo; usa razonamiento normal.

## El roster (8 consejeros)

Cada consejero tiene UN mandato. No deben ablandar su postura para "quedar bien" con los demás.

| # | Consejero | Frente | Pregunta que persigue |
|---|-----------|--------|------------------------|
| 1 | El Inquisidor | Escéptico | ¿Dónde están las grietas, fallas y supuestos no probados? |
| 2 | El Arquitecto de la Flota | Factibilidad | ¿Se puede construir realmente? ¿Cómo, con qué, en qué orden? |
| 3 | La Voz del Pueblo | Usuario | ¿Qué siente y necesita quien lo usará? ¿Le resuelve algo? |
| 4 | El Centinela | Riesgos | ¿Qué amenazas, efectos colaterales o modos de fallo acechan? |
| 5 | El Oráculo | Largo plazo | ¿Cómo envejece esta decisión en 1–5 años? ¿Qué deuda crea? |
| 6 | El Tesorero Imperial | Costo y recursos | ¿Cuánto cuesta en tiempo/dinero/esfuerzo? ¿Vale la pena? |
| 7 | El Diplomático | Ética y reputación | ¿Es correcto? ¿Cómo se verá ante usuarios, equipo y terceros? |
| 8 | El Hereje | Abogado del diablo | Defiende a propósito la opción contraria; ataca el consenso. |

Para preguntas pequeñas puedes convocar solo a un subconjunto relevante (mínimo 3),
pero **siempre incluye al menos un crítico (Inquisidor o Hereje)** para evitar la cámara de eco.

## El protocolo (7 fases)

**Fase 1 — Encuadre.** Reformula en 1–2 líneas la decisión exacta a deliberar. Si falta
contexto crítico, pídelo antes de convocar.

**Fase 2 — El Gran Visir (coordinador) reparte.** Entrega la misma pregunta a cada consejero
de forma aislada. El coordinador organiza, no opina.

**Fase 3 — Deliberación independiente.** Cada consejero produce su juicio SIN ver el de los
demás. Para máxima independencia real:
- **Si tienes herramienta de sub-agentes** (Task / Agent / Workflow): lanza cada consejero
  en su propio contexto aislado, en paralelo. Es la forma rigurosa: no pueden contaminarse.
- **Si no:** redacta cada juicio en un bloque separado, comprometiéndote de verdad con ese
  rol antes de pasar al siguiente. No mires hacia adelante ni armonices todavía.

  Cada consejero devuelve, en ≤120 palabras: **postura** (a favor / en contra / matizada),
  **2–3 razones**, y **el mayor riesgo o supuesto** de su análisis.

**Fase 4 — Reunir.** El coordinador junta los juicios y los **anonimiza** (quita los nombres,
quedan "Argumento A, B, C…").

**Fase 5 — Cónclave de revisión (anónimo).** Revisa los argumentos agrupados sin saber quién
escribió cada uno: marca dónde coinciden, dónde se contradicen, qué argumento es más fuerte
y cuál es débil o equivocado. Esto depura errores antes de la síntesis.

**Fase 6 — El Emperador (Sintetizador Supremo) dicta veredicto.** Funde lo mejor, descarta el
ruido y las posturas débiles, y resuelve las contradicciones. Produce:
- **Veredicto:** la recomendación, en una frase.
- **Por qué:** las 2–4 razones que más pesaron.
- **Trade-offs:** qué se sacrifica al elegir esto.
- **Voz disidente:** la objeción más fuerte que vale la pena conservar (normalmente del
  Hereje o el Inquisidor).
- **Confianza:** alta / media / baja, y qué la subiría.

**Fase 7 — Entrega.** Presenta al usuario el veredicto primero. Abajo, opcionalmente, un
resumen plegado de las voces del consejo (1 línea por consejero) por transparencia.

## Formato de salida sugerido

```
🏛️ VEREDICTO DEL CONSEJO
Decisión deliberada: <reformulación en 1 línea>

⚖️ Veredicto: <recomendación en una frase>
Por qué: <2–4 razones>
Trade-offs: <qué se sacrifica>
Voz disidente: <la mejor objeción a tener presente>
Confianza: <alta/media/baja — qué la mejoraría>

— Voces del consejo (resumen) —
🔎 Inquisidor: …    ⚙️ Arquitecto: …    🫡 Voz del Pueblo: …
🛡️ Centinela: …     🔭 Oráculo: …       💠 Tesorero: …
⚖️ Diplomático: …   🔥 Hereje: …
```

## Reglas

- El paso de síntesis (Fase 6) es **obligatorio**. Nunca entregues las 8 opiniones sin fundirlas.
- Mantén la independencia: en la Fase 3 ningún consejero ve a los otros.
- No infles. Sé conciso; un veredicto claro vale más que ocho párrafos.
- El tono imperial/épico de los nombres es decorativo y opcional: si el usuario prefiere
  etiquetas neutras (Escéptico, Factibilidad, etc.), úsalas.
- Tras el veredicto, ofrece profundizar en cualquiera de las voces si el usuario lo pide.

## Diagrama

Hay un organigrama visual del flujo en `assets/organigrama-consejo.html` (abrir en el navegador).
