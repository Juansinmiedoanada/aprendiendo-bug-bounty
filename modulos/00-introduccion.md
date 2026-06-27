# Módulo 00 — Introducción al Bug Bounty

> En este módulo entenderás **qué es** el bug bounty de verdad, por qué existe, cómo hacerlo **sin meterte en problemas legales**, y qué mentalidad necesitas. Nada de tecnicismos todavía: primero las bases.

[⬅️ Volver al índice](../README.md) · [Siguiente: Módulo 01 ➡️](01-fundamentos-web.md)

---

## 1. ¿Qué es realmente el bug bounty?

Imagina que tienes una casa y, en lugar de esperar a que un ladrón encuentre la ventana mal cerrada, **contratas a gente honesta** para que intente "colarse" y luego te diga: *"oye, la ventana de la cocina no cierra bien"*. Tú les pagas por avisarte, arreglas la ventana, y tu casa queda más segura.

Eso es el bug bounty, pero con aplicaciones web, apps móviles, APIs y sistemas informáticos.

- Las **empresas** (Google, PayPal, Spotify, gobiernos, startups...) publican **programas** donde dicen: *"si encuentras un fallo de seguridad en estos sistemas y nos avisas de forma responsable, te recompensamos"*.
- Los **investigadores** (tú, en el futuro) buscan esos fallos y los reportan.
- La empresa paga una **recompensa** (en inglés, *bounty*), que puede ir desde una mención de agradecimiento hasta **miles de euros/dólares** por un fallo crítico.

### ¿Por qué las empresas hacen esto?

Porque tener miles de ojos buscando fallos es más barato y eficaz que esperar a sufrir un ataque real. Un fallo descubierto por un *hunter* honesto cuesta una recompensa; el mismo fallo explotado por un criminal puede costar millones y la confianza de los clientes.

---

## 2. Hacking ético: el bueno de la película

Existen, de forma muy simplificada, tres tipos de "sombreros":

- 🤍 **White hat (sombrero blanco):** hacker ético. Actúa **con permiso**, reporta los fallos y ayuda a arreglarlos. **Esto es lo que serás tú.**
- 🖤 **Black hat (sombrero negro):** delincuente. Ataca **sin permiso** para robar, extorsionar o destruir. Esto es ilegal y este curso **no** va de eso.
- 🩶 **Grey hat (sombrero gris):** zona ambigua, a veces actúa sin permiso "con buenas intenciones". **Evítalo:** aunque tu intención sea buena, sin permiso sigue siendo ilegal.

> En bug bounty siempre eres **white hat**. La autorización lo es todo.

---

## 3. ⚖️ Lo legal: la parte más importante del curso

Voy a ser muy directo porque esto te puede ahorrar problemas serios:

### La regla de oro

> **Si no tienes permiso explícito, NO lo toques.**

No importa lo curioso que sea un sitio web. No importa que el fallo sea "obvio". Sin autorización, probar la seguridad de un sistema ajeno es **delito**.

### ¿Qué te da permiso?

1. **Que sea tuyo:** tus propias webs, tus servidores, tus apps de prueba.
2. **Un laboratorio diseñado para practicar:** existen entornos legales pensados para esto (los veremos en el Módulo 02).
3. **Un programa de bug bounty con su *scope*:** cuando una empresa publica un programa, define exactamente **qué** puedes probar (el *scope* o alcance) y **qué no** (*out of scope*). Salirte de ahí = problema legal.

### Marco legal (referencia)

- **España:** Código Penal, artículos 197 bis (acceso ilícito a sistemas) y 264 (daños informáticos).
- **EE. UU.:** *Computer Fraud and Abuse Act (CFAA)*.
- **Unión Europea:** Directiva 2013/40/UE sobre ataques a sistemas de información.

No necesitas memorizar las leyes, solo interiorizar la idea: **acceder o probar sin permiso tiene consecuencias penales reales.**

---

## 4. Divulgación responsable (Responsible Disclosure)

Cuando encuentras un fallo, **no** lo publicas en redes sociales ni lo usas. El proceso correcto es:

1. **Avisas en privado** a la empresa (a través del programa o de un contacto de seguridad).
2. Le das **tiempo** para arreglarlo.
3. Solo cuando está arreglado (y a veces con su permiso) se puede hablar públicamente del fallo.

Esto se llama **divulgación responsable**, y es lo que separa a un profesional de un irresponsable.

---

## 5. La mentalidad del cazador de bugs

El bug bounty no va de "ser un genio". Va de:

- 🔍 **Curiosidad:** preguntarte siempre *"¿y qué pasa si...?"*.
- 🧩 **Paciencia:** puedes pasar horas sin encontrar nada. Es normal.
- 📝 **Método:** ser ordenado y sistemático gana a la suerte.
- 🔁 **Constancia:** los buenos hunters no son los más listos, son los que no se rinden.
- 🧠 **Pensar diferente:** los desarrolladores piensan *"cómo hago que funcione"*; tú piensas *"cómo hago que falle"*.

> Spoiler: tus primeros días (o semanas) probablemente no encuentres nada. **Es parte del proceso.** Todos los grandes hunters empezaron igual.

---

## 6. Expectativas realistas (sé honesto contigo mismo)

- **No te vas a hacer rico la primera semana.** Ni el primer mes, probablemente.
- Hay mucha **competencia**: miles de personas buscan en los mismos programas.
- El aprendizaje es **largo**, pero cada paso cuenta.
- Las primeras recompensas suelen ser pequeñas o incluso solo "reconocimiento". **Está bien:** son experiencia y currículum.

Lo bueno: las habilidades que aprendas aquí sirven para **toda una carrera** en ciberseguridad, no solo para el bug bounty.

---

## ✓ Resumen del módulo

- El bug bounty es buscar fallos de seguridad **con permiso** a cambio de recompensa.
- Tú serás siempre un **hacker ético (white hat)**.
- **Sin permiso = delito.** La autorización (scope) lo es todo.
- Practica solo en sistemas propios, laboratorios legales o programas autorizados.
- Usa **divulgación responsable**: avisa en privado, da tiempo, no lo hagas público sin permiso.
- La clave del éxito es **curiosidad + método + constancia**, no ser un genio.

---

## 📝 Ejercicio práctico

1. Busca en internet el término **"responsible disclosure policy"** de una empresa grande (por ejemplo, Google o GitHub) y léela. Fíjate en cómo definen qué se puede y qué no se puede hacer.
2. Escribe con tus propias palabras (en 3 líneas) la diferencia entre un *white hat* y un *grey hat*.
3. Reflexiona: ¿por qué crees que una empresa preferiría pagar a un hunter antes que ignorar el problema?

---

[⬅️ Volver al índice](../README.md) · [Siguiente: Módulo 01 — Fundamentos web ➡️](01-fundamentos-web.md)
