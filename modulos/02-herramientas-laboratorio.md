# Módulo 02 — Herramientas y tu laboratorio seguro

> Antes de cazar bugs necesitas tu "equipo". En este módulo verás las herramientas esenciales (sin agobios) y, lo más importante, cómo montar un **laboratorio legal** para practicar sin riesgo.

[⬅️ Módulo 01](01-fundamentos-web.md) · [Volver al índice](../README.md) · [Siguiente: Módulo 03 ➡️](03-reconocimiento.md)

---

## 1. Lo primero: ¿dónde practico SIN romper la ley?

Repito el mantra del curso: **sin permiso, no se toca.** Por suerte, existen entornos creados **específicamente** para que practiques de forma legal:

### 🧪 Laboratorios y webs vulnerables a propósito

- **PortSwigger Web Security Academy** (gratis): el mejor punto de partida. Laboratorios interactivos con teoría, hechos por los creadores de Burp Suite.
- **OWASP Juice Shop:** una tienda online deliberadamente vulnerable que puedes instalar en tu ordenador.
- **DVWA (Damn Vulnerable Web Application):** clásico para practicar fallos web.
- **TryHackMe** y **Hack The Box:** plataformas con retos guiados (algunos gratuitos) en entornos controlados.
- **bWAPP**, **WebGoat (OWASP):** otras apps vulnerables para entrenar.

> 👉 Estos entornos son **tuyos o están diseñados para atacarse**. Aquí puedes experimentar todo lo que quieras. Empieza por la **Web Security Academy de PortSwigger**.

---

## 2. El navegador: tu primera herramienta

No necesitas nada exótico para empezar. Tu navegador ya trae herramientas potentes:

- **F12 → Herramientas de desarrollador:**
  - **Network (Red):** ver todas las peticiones HTTP.
  - **Console (Consola):** ejecutar y probar JavaScript.
  - **Application/Storage:** ver cookies y datos guardados.
  - **Elements (Elementos):** inspeccionar y modificar el HTML en vivo.

Recomendación: usa **Firefox** o un navegador secundario dedicado solo a tus pruebas, separado de tu navegación personal.

---

## 3. El proxy: la herramienta estrella (Burp Suite)

Esta es **la** herramienta del bug bounty. Un **proxy de interceptación** se coloca "en medio" entre tu navegador y el servidor, y te deja **ver y modificar** cada petición antes de que llegue.

```
[ Tu navegador ] → [ Burp Suite (proxy) ] → [ Servidor ]
                         ↑
                  Aquí ves y editas
                  cada petición
```

### Burp Suite (de PortSwigger)

- **Community Edition (gratis):** suficiente para aprender y para muchísimas tareas. Es la que usarás al principio.
- **Professional (de pago):** añade escáner automático y funciones avanzadas. Ya la valorarás más adelante.

Funciones clave que usarás:
- **Proxy:** interceptar peticiones.
- **Repeater:** reenviar una petición modificándola, una y otra vez (clave para probar fallos).
- **Intruder:** automatizar pruebas con muchos valores (limitado en la versión gratuita).
- **Decoder:** codificar/descodificar datos (Base64, URL, etc.).

### Alternativa: OWASP ZAP

**OWASP ZAP** es un proxy similar, **totalmente gratuito y de código abierto**. Buena opción si prefieres alternativas libres.

---

## 4. Otras herramientas útiles (para más adelante)

No necesitas instalarlas todas hoy. Tenlas en el radar:

| Herramienta | Para qué sirve |
|-------------|----------------|
| **Nmap** | Escanear puertos y servicios de un sistema |
| **ffuf / dirb / gobuster** | Buscar rutas y archivos ocultos (fuzzing) |
| **Subfinder / Amass** | Descubrir subdominios |
| **httpx** | Comprobar qué dominios responden y cómo |
| **Nuclei** | Buscar vulnerabilidades conocidas con plantillas |
| **Wfuzz** | Fuzzing de parámetros y valores |

> Estas son de **línea de comandos** y las verás en el Módulo 03 (Reconocimiento). No te abrumes: con el navegador y Burp ya puedes empezar a aprender muchísimo.

---

## 5. ¿Necesito Linux? ¿Kali?

- **No es obligatorio** para empezar. Puedes aprender los fundamentos en Windows o Mac con el navegador y Burp.
- **Kali Linux** y **Parrot OS** son sistemas con todas las herramientas de seguridad ya instaladas. Son muy cómodos, pero opcionales al principio.
- Una buena opción intermedia: instalar Kali en una **máquina virtual** (con VirtualBox o VMware) para no tocar tu sistema principal.

> Consejo: no pierdas semanas "preparando el setup perfecto". Con navegador + Burp Community + la Web Security Academy ya tienes para meses de aprendizaje.

---

## 6. Tu primer laboratorio paso a paso (recomendado)

Una ruta sencilla para arrancar hoy mismo:

1. **Crea una cuenta gratuita** en la PortSwigger Web Security Academy.
2. **Descarga e instala Burp Suite Community Edition.**
3. **Configura tu navegador** para pasar el tráfico por Burp (PortSwigger ofrece un navegador preconfigurado dentro de Burp, lo más fácil).
4. **Haz el primer laboratorio** de la categoría más sencilla y sigue las instrucciones.
5. Observa en Burp cómo viajan tus peticiones. Juega con el **Repeater**.

Con eso, ya estarás "hackeando" de forma 100% legal en tu primer día. 🎉

---

## 7. Organízate desde el principio

Una costumbre que te diferenciará de la mayoría:

- 📓 **Lleva notas.** Apps como Obsidian, Notion o un simple documento. Anota qué pruebas, qué funciona y qué no.
- 🗂️ **Guarda capturas y peticiones interesantes.** Te servirán para los reportes (Módulo 05).
- 📅 **Sé constante.** Mejor 1 hora al día que 10 horas un domingo y nada el resto del mes.

---

## ✓ Resumen del módulo

- Practica **solo** en laboratorios legales: PortSwigger Academy, Juice Shop, DVWA, TryHackMe, Hack The Box...
- Tu **navegador (F12)** ya es una herramienta potente.
- **Burp Suite Community** (o **OWASP ZAP**) es el proxy estrella: ver y modificar peticiones.
- Hay muchas herramientas de línea de comandos (Nmap, ffuf, subfinder...), pero **no las necesitas todas** para empezar.
- **Kali Linux es opcional.** No te obsesiones con el setup perfecto.
- Empieza HOY: cuenta en PortSwigger + Burp Community + primer laboratorio.
- **Toma notas y sé constante** desde el día uno.

---

## 📝 Ejercicio práctico

1. Crea tu cuenta en la **PortSwigger Web Security Academy** y explora la lista de laboratorios disponibles.
2. Instala **Burp Suite Community Edition** y consigue interceptar una petición de un laboratorio (o de una web tuya). Observa cómo puedes verla y modificarla.
3. Crea tu sistema de notas (una carpeta, un Obsidian, lo que prefieras) y escribe tu primera entrada: "Día 1: configuré Burp y lo conecté con el navegador".

---

[⬅️ Módulo 01](01-fundamentos-web.md) · [Volver al índice](../README.md) · [Siguiente: Módulo 03 — Reconocimiento ➡️](03-reconocimiento.md)
