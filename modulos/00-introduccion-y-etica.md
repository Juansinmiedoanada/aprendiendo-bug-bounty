
# Módulo 0 · Introducción, mentalidad y ética

> ⏱️ Tiempo estimado: 1-2 horas de lectura + reflexión.
> 🎯 Objetivo: entender qué es el bug bounty, qué se espera de ti y cómo no acabar en problemas legales.

---

## 0.1 ¿Qué es el bug bounty?

Un **programa de bug bounty** es un acuerdo en el que una empresa invita a investigadores de seguridad (tú) a buscar vulnerabilidades en sus sistemas a cambio de **recompensas** (dinero, reputación, regalos).

En lugar de esperar a que un atacante malicioso encuentre el fallo, la empresa **paga a los buenos** por encontrarlo primero y reportarlo de forma privada.

Actores principales:

- **La empresa / programa**: define qué se puede atacar (*scope*) y cuánto paga.
- **La plataforma**: intermediario que gestiona los reportes y pagos (HackerOne, Bugcrowd, Intigriti, YesWeHack...).
- **El investigador (tú, el "hunter")**: busca, reporta y cobra.

---

## 0.2 Bug bounty vs. pentesting vs. CTF

| | Bug Bounty | Pentesting | CTF |
|---|---|---|---|
| Quién | Cualquiera registrado | Contratado por la empresa | Competición / juego |
| Pago | Por bug válido encontrado | Salario / por proyecto | Puntos, premios |
| Alcance | Definido en la política | Definido en contrato | El reto/laboratorio |
| Tiempo | Continuo, sin fin | Limitado (ej. 2 semanas) | Limitado al evento |

Los **CTF** (Capture The Flag) y los labs son la mejor forma de **practicar gratis y sin riesgo legal**. Empezarás por ahí.

---

## 0.3 La mentalidad del hacker

El mejor cazador de bugs no es el que sabe más comandos, sino el que **piensa diferente**:

- **"¿Qué pasa si...?"** — ¿Y si cambio este número? ¿Y si mando una letra donde esperan un número? ¿Y si borro este parámetro?
- **Cuestiona las suposiciones del desarrollador.** Cada validación que falta es una oportunidad.
- **Entiende antes de atacar.** No lances herramientas a ciegas; comprende cómo funciona la aplicación.
- **Persistencia.** Vas a fallar mucho. Los duplicados, los "informativo" y los "N/A" son parte del juego.
- **Documenta todo.** Tus notas de hoy son tu metodología de mañana.

---

## 0.4 Ética y legalidad ⚖️ (la parte más importante)

> ⚠️ Esta sección puede ahorrarte una denuncia. No la saltes.

### Lo que SÍ puedes hacer
- Practicar en **laboratorios diseñados para ello** (PortSwigger, DVWA, TryHackMe, HTB, máquinas vulnerables propias).
- Atacar objetivos **dentro del scope** de un programa de bug bounty al que estás inscrito.
- Reportar lo que encuentres por el **canal oficial**.

### Lo que NO puedes hacer
- Atacar una web/empresa **sin un programa o permiso explícito por escrito**, aunque la encuentres "vulnerable de casualidad".
- Salirte del **scope** definido (atacar subdominios, APIs o terceros no incluidos).
- **Acceder, descargar o modificar datos reales** de otros usuarios más allá de lo mínimo para demostrar el fallo (una "prueba de concepto").
- Hacer **DoS / fuerza bruta agresiva** salvo que la política lo permita explícitamente.
- Hacer pública la vulnerabilidad sin autorización (eso es **0-day irresponsable**).

### Marco legal (orientativo)
En la mayoría de países el acceso no autorizado a sistemas informáticos es **delito** (ej. en España, art. 197 bis y 264 del Código Penal; en EE. UU., la CFAA). El "solo estaba probando" **no es una defensa válida**.

> 🔑 **Safe Harbor**: muchos programas serios incluyen una cláusula que te protege legalmente *si* respetas su política. Léela. Si un programa no la tiene y no responde, ten más cuidado.

---

## 0.5 Divulgación responsable (Responsible Disclosure)

Cuando encuentras un fallo:

1. **Para.** No sigas explotando más allá de demostrar el impacto.
2. **Documenta**: pasos para reproducir, captura/petición, impacto.
3. **Reporta** por el canal oficial del programa.
4. **Espera.** Da tiempo a que lo arreglen antes de hablar de ello.
5. **No lo divulgues públicamente** sin permiso o hasta que esté parcheado y el programa lo autorice.

---

## 0.6 Expectativas realistas 💸

Sé honesto/a contigo:

- Tus primeros meses probablemente **no ganarás dinero**. Estarás aprendiendo.
- Muchos reportes serán **duplicados** (alguien lo encontró antes) o **fuera de scope**.
- El primer bug válido puede tardar **semanas o meses**. Es normal.
- La constancia gana. Quien practica 1 hora al día durante un año, llega lejos.

---

## ✓ Tareas del módulo

1. Crea una cuenta (gratis) en [HackerOne](https://hackerone.com) y [Bugcrowd](https://bugcrowd.com). Aún no vas a hackear nada; solo explora.
2. Lee la política de un programa público cualquiera y localiza: el **scope**, el **out-of-scope** y si tiene **Safe Harbor**.
3. Crea tu sistema de notas (Obsidian / Notion / carpeta de `.md`).
4. Escribe con tus palabras: *¿por qué es importante no salirse del scope?*

---

## 📌 Resumen

- El bug bounty es buscar fallos **con permiso** a cambio de recompensa.
- La **ética y la legalidad** son innegociables: sin permiso, no se toca.
- Empezarás practicando en **labs**, no en producción.
- Expectativas realistas + constancia = progreso.

👉 Siguiente: [Módulo 1 · Fundamentos web](01-fundamentos-web.md)
