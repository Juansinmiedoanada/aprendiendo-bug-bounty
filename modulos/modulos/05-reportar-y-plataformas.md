# Módulo 05 — Reportar bugs y plataformas

> Encontrar un fallo es la mitad del trabajo; la otra mitad es **reportarlo bien**. Un buen reporte puede ser la diferencia entre cobrar una buena recompensa o que te ignoren. En este módulo aprenderás dónde participar, cómo escribir reportes profesionales y cómo seguir creciendo.

[⬅️ Módulo 04](04-vulnerabilidades-comunes.md) · [Volver al índice](../README.md)

---

## 1. Plataformas de Bug Bounty

La mayoría de los programas se gestionan a través de **plataformas** que conectan a las empresas con los investigadores. Las principales:

| Plataforma | Características |
|------------|----------------|
| **HackerOne** | La más grande y conocida. Muchos programas, buena para empezar. |
| **Bugcrowd** | Otra de las grandes. Amplia variedad de programas. |
| **Intigriti** | Plataforma europea, muy activa y con buena comunidad. |
| **YesWeHack** | Plataforma europea (origen francés), en crecimiento. |
| **Open Bug Bounty** | Enfocada en ciertos tipos de fallos, modelo abierto. |

También hay empresas con su **propio programa** (sin plataforma intermediaria): suelen tener una página `/.well-known/security.txt` o un apartado de "Security" donde explican cómo reportar.

---

## 2. Programas: VDP vs Bug Bounty de pago

Antes de lanzarte, entiende los dos tipos:

- **VDP (Vulnerability Disclosure Program):** aceptan reportes pero **no pagan** dinero; suelen dar reconocimiento (aparecer en un "Hall of Fame"). Ideales para **practicar y ganar reputación** sin tanta competencia.
- **Bug Bounty (de pago):** ofrecen **recompensas económicas**. Más competidos, especialmente los de empresas famosas.

> 💡 Consejo para novatos: empieza en **VDP** o en programas pequeños/nuevos. Hay menos hunters expertos compitiendo y es más fácil conseguir tu primer hallazgo válido.

---

## 3. Entender el SCOPE (otra vez, porque es crucial)

Cada programa tiene una página con sus reglas. **Léela entera antes de empezar.** Fíjate en:

- **In scope:** qué dominios, apps y sistemas SÍ puedes probar.
- **Out of scope:** qué NO. Reportar algo fuera del scope no se paga y puede sancionarte.
- **Vulnerabilidades aceptadas y excluidas:** algunos programas no aceptan ciertos tipos (p. ej., reportes automáticos sin impacto).
- **Reglas de prueba:** límites de velocidad, prohibición de ataques de denegación de servicio (DoS), no usar datos reales de otros usuarios, etc.

> 🚫 Salirte del scope o romper las reglas puede costarte la expulsión de la plataforma... o algo peor. Respétalo siempre.

---

## 4. Anatomía de un buen reporte

Un reporte profesional tiene esta estructura. Imagina que se lo explicas a alguien que no estaba ahí:

### 1) Título claro
Resume el fallo y dónde está.
> ✗ "Encontré un bug"
> ✓ "IDOR en /api/facturas permite leer facturas de otros usuarios"

### 2) Resumen
Una o dos frases: qué es el fallo y por qué importa.

### 3) Pasos para reproducir (lo más importante)
Una lista **numerada y exacta** para que cualquiera reproduzca el fallo:
```
1. Inicia sesión como usuario A.
2. Ve a https://objetivo.com/api/facturas?id=1001
3. Cambia el parámetro id a 1000.
4. Observa que se muestra la factura del usuario B.
```

### 4) Impacto
Explica **qué puede conseguir un atacante**. Esto define la gravedad y la recompensa.
> "Un atacante puede acceder a datos personales y financieros de cualquier cliente iterando el parámetro id."

### 5) Pruebas (evidencias)
Capturas de pantalla, vídeo corto, peticiones HTTP. Demuestra el fallo sin lugar a dudas.

### 6) Sugerencia de solución (suma puntos)
Una recomendación de cómo arreglarlo.
> "Verificar en el servidor que la factura solicitada pertenece al usuario autenticado."

---

## 5. Severidad: CVSS y triage

- Las recompensas dependen de la **gravedad** del fallo. Se suele medir con el sistema **CVSS** (una puntuación de 0 a 10).
- Categorías típicas: **Crítica, Alta, Media, Baja, Informativa.**
- Cuando envías un reporte, un equipo lo **revisa (triage)**: confirma si es válido, pide más datos si hace falta y asigna la severidad.
- Sé **paciente y educado** en esta fase. La comunicación clara y respetuosa importa mucho.

---

## 6. Errores típicos de los novatos (evítalos)

- ✗ **Reportar sin impacto real:** "la web no tiene cabecera X" sin demostrar daño. Suele rechazarse.
- ✗ **Spam de escáneres automáticos:** mandar resultados de herramientas sin verificar ni entender. Genera mala reputación.
- ✗ **Duplicados:** alguien ya lo reportó antes. Es normal y frustrante; sigue buscando.
- ✗ **Salirse del scope.**
- ✗ **Reportes pobres:** sin pasos claros ni evidencias. Aunque el fallo sea real, si no se entiende, lo rechazan.
- ✗ **Impaciencia:** presionar o ser grosero con el equipo de triage.

---

## 7. Qué esperar (realismo, parte 2)

- Tus primeros reportes pueden ser **duplicados** o marcados como "informativos". **Es normal.**
- Puede pasar **tiempo** hasta tu primera recompensa válida. Cada intento es aprendizaje.
- La constancia y la mejora continua son lo que separan a quien lo consigue de quien lo deja.

> El primer bug válido es el más difícil. Después, todo va ganando sentido.

---

## 8. Tu plan de acción para empezar (resumen del curso)

1. **Domina los fundamentos** (Módulos 00-01): ética, legalidad y cómo funciona la web.
2. **Monta tu laboratorio** (Módulo 02): Burp Community + PortSwigger Academy.
3. **Aprende practicando**: completa laboratorios de la Web Security Academy (IDOR, XSS, etc.).
4. **Aprende recon** (Módulo 03) en objetivos propios o autorizados.
5. **Crea cuenta en una plataforma** (HackerOne, Intigriti...) y lee programas.
6. **Elige un programa con scope amplio** (mejor VDP o uno nuevo) y empieza con calma.
7. **Reporta bien** lo que encuentres, siguiendo la estructura de este módulo.
8. **Sé constante.** Repite, aprende de cada reporte y mejora.

---

## 9. Recursos para seguir aprendiendo

- **PortSwigger Web Security Academy:** teoría + laboratorios gratis (imprescindible).
- **OWASP:** Top 10, guías de testing y *cheat sheets*.
- **HackerOne Hacktivity / informes públicos (*disclosed reports*):** lee reportes reales ya publicados para aprender cómo lo hacen los buenos.
- **TryHackMe / Hack The Box:** retos prácticos.
- **Libros:** *The Web Application Hacker's Handbook*, *Real-World Bug Hunting* (Peter Yaworski), *Bug Bounty Bootcamp* (Vickie Li).
- **Comunidad:** sigue a hunters en redes, lee writeups, únete a comunidades. Compartir acelera el aprendizaje.

---

## ✓ Resumen del módulo

- Las **plataformas** (HackerOne, Bugcrowd, Intigriti, YesWeHack) conectan empresas y hunters.
- Diferencia **VDP** (reconocimiento, sin pago) de **bug bounty de pago**. Empieza por VDP o programas pequeños.
- **Lee siempre el scope y las reglas** antes de probar nada.
- Un **buen reporte** lleva: título claro, resumen, pasos exactos, impacto, evidencias y sugerencia de solución.
- La **severidad** (CVSS) determina la recompensa; hay una fase de **triage**.
- Evita los **errores típicos**: reportes sin impacto, spam de escáneres, salirse del scope.
- Ten **expectativas realistas**: los primeros bugs cuestan. La clave es la **constancia**.

---

## 📝 Ejercicio práctico

1. Crea una cuenta en **HackerOne** o **Intigriti** y explora 3 programas. Lee sus **scopes** y compara qué permiten y qué no.
2. Lee 2 o 3 **reportes públicos** (*disclosed*) en HackerOne Hacktivity. Fíjate en cómo estructuran los pasos y el impacto.
3. **Redacta un reporte de práctica** (sin enviarlo) sobre un fallo que hayas resuelto en la PortSwigger Academy, usando la estructura del punto 4 de este módulo.

---

## 🎓 ¡Enhorabuena!

Has completado el **Curso de Bug Bounty para Novatos**. Ahora tienes una base sólida: entiendes la ética y la ley, cómo funciona la web, qué herramientas usar, cómo hacer recon, qué vulnerabilidades buscar y cómo reportarlas.

El siguiente paso depende de ti: **practica, sé constante y mantente siempre dentro de la ley.** El camino es largo, pero apasionante. ¡Buena caza ética! 🐛🔍

[⬅️ Módulo 04](04-vulnerabilidades-comunes.md) · [Volver al índice](../README.md)
