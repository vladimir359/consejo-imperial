# 🏛️ El Consejo Imperial — Claude Skill

Una *skill* para Claude que convierte una decisión difícil en una **deliberación de 8
consejeros**: cada uno la analiza desde un frente distinto, se revisan entre sí de forma
anónima, y un **Sintetizador Supremo** funde todo en **un solo veredicto razonado**.

Es la idea del *LLM Council* (popularizada por Andrej Karpathy) en su versión **"solo Claude"**:
no requiere llaves de API de otros modelos ni costos extra. Un único modelo adopta 8 roles
independientes y luego sintetiza.

> **La pieza clave es la síntesis.** Sin un sintetizador final, ocho opiniones sueltas son
> solo ruido. Este protocolo siempre termina en *un* veredicto.

---

## ✨ Qué hace

Cuando lo convocas, Claude ejecuta un protocolo de 7 fases:

1. **Encuadre** — reformula la decisión exacta a deliberar.
2. **Reparto** — el coordinador entrega la pregunta a cada consejero, aislado.
3. **Deliberación independiente** — los 8 opinan sin verse entre sí.
4. **Reunir y anonimizar** los argumentos.
5. **Cónclave de revisión** — se critican entre sí sin saber quién es quién.
6. **Veredicto** — el Sintetizador funde lo mejor y descarta el ruido.
7. **Entrega** — un veredicto claro + voz disidente + nivel de confianza.

### Los 8 consejeros

| Consejero | Frente |
|-----------|--------|
| 🔎 El Inquisidor | Escéptico — busca fallas |
| ⚙️ El Arquitecto de la Flota | Factibilidad técnica |
| 🫡 La Voz del Pueblo | El usuario |
| 🛡️ El Centinela | Riesgos |
| 🔭 El Oráculo | Largo plazo |
| 💠 El Tesorero Imperial | Costo y recursos |
| ⚖️ El Diplomático | Ética y reputación |
| 🔥 El Hereje | Abogado del diablo (defiende lo contrario) |

📊 **Diagrama del flujo:** abre [`assets/organigrama-consejo.html`](assets/organigrama-consejo.html)
en tu navegador.

---

## 🚀 Instalación

### Claude Code
Copia la carpeta a tu directorio de skills:

```bash
# skill global (todos tus proyectos)
mkdir -p ~/.claude/skills
cp -R consejo-imperial ~/.claude/skills/

# o solo para un proyecto
mkdir -p .claude/skills
cp -R consejo-imperial .claude/skills/
```

Reinicia Claude Code y la skill quedará disponible.

### Claude.ai / Cowork
Sube el archivo `SKILL.md` (con la carpeta `assets/`) como skill, o pídele a Claude:
> "Instalá esta skill por mí desde este repo: `<URL de tu repo>`"

---

## 🗣️ Cómo se usa

No hay que recordar nombres. Se activa con frases como:

- `convoco al consejo`
- `eleva esto al consejo`
- `pásalo por el consejo`
- `deliberá` / `delibera esto`
- `council this` / `pressure-test this`

**Ejemplo:**
> "¿Reescribo todo el sitio en React o lo dejo en HTML? **Deliberá.**"

Si **no** usás una frase gatillo, Claude responde con su razonamiento normal. No toda
tarea necesita un consejo.

---

## 🤔 ¿Mejora las respuestas?

**En decisiones difíciles, sí.** Forzar múltiples ángulos + autocrítica atrapa errores que
un solo razonamiento pasaría por alto. **En tareas simples, no** — solo añade demora, por eso
está pensado para activarse a pedido.

Para **independencia real**, la skill corre cada consejero en un contexto aislado cuando hay
sub-agentes disponibles (no se contaminan entre sí). La independencia total entre *modelos
distintos* solo la da la versión multi-modelo de pago, que esta skill no usa.

---

## 📄 Licencia

MIT — ver [`LICENSE`](LICENSE). Homenaje estético de ciencia ficción con nombres y diseño
originales; no afiliado a ninguna franquicia ni marca registrada.
