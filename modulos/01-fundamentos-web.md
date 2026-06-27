# Módulo 01 — Fundamentos: cómo funciona la web

> Para encontrar fallos en aplicaciones web, primero hay que entender **cómo funcionan**. En este módulo aprenderás, desde cero y con analogías, qué pasa cuando escribes una dirección en tu navegador y pulsas Enter.

[⬅️ Módulo 00](00-introduccion.md) · [Volver al índice](../README.md) · [Siguiente: Módulo 02 ➡️](02-herramientas-laboratorio.md)

---

## 1. La idea básica: cliente y servidor

Internet funciona como un restaurante:

- **Tú (el cliente)** = tu navegador (Chrome, Firefox...). Haces **peticiones** ("quiero ver esta página").
- **La cocina (el servidor)** = el ordenador remoto donde vive la web. **Responde** a tus peticiones ("aquí tienes la página").
- **El camarero (la red/internet)** = lleva tu pedido a la cocina y te trae la respuesta.

Cada vez que visitas una web, tu navegador (cliente) **pide** algo a un servidor, y el servidor **responde**. A esa conversación la gobierna un idioma común: **HTTP**.

---

## 2. ¿Qué pasa al escribir una URL? (paso a paso)

Cuando escribes `https://www.ejemplo.com` y pulsas Enter:

1. **DNS:** tu navegador pregunta *"¿qué dirección IP tiene ejemplo.com?"*. El DNS es como la **agenda de contactos de internet**: traduce nombres (ejemplo.com) en direcciones IP (como 93.184.216.34).
2. **Conexión:** tu navegador se conecta a esa IP.
3. **Petición HTTP:** tu navegador envía una petición: *"dame la página principal"*.
4. **Respuesta HTTP:** el servidor responde con el código HTML, imágenes, estilos, etc.
5. **Renderizado:** tu navegador "dibuja" todo eso y ves la web.

Todo esto ocurre en **milisegundos**.

---

## 3. Las partes de una URL

Vamos a diseccionar una dirección web, porque cada parte importa:

```
https://blog.ejemplo.com:443/articulos/seguridad?id=10&orden=asc#comentarios
└─┬─┘   └──────┬───────┘└┬┘ └───────┬────────┘ └──────┬───────┘ └────┬────┘
 esquema      host      puerto      ruta            parámetros      fragmento
```

- **Esquema (`https`):** el protocolo. `http` es sin cifrar; `https` es cifrado (seguro). Hoy casi todo es `https`.
- **Host (`blog.ejemplo.com`):** el dominio. `blog` es un **subdominio** de `ejemplo.com`.
- **Puerto (`443`):** la "puerta" por la que entra la conexión. 80 = HTTP, 443 = HTTPS (normalmente no se ve).
- **Ruta (`/articulos/seguridad`):** qué recurso concreto pides dentro del servidor.
- **Parámetros (`?id=10&orden=asc`):** datos extra que envías. ¡Aquí se esconden MUCHOS fallos!
- **Fragmento (`#comentarios`):** un punto concreto de la página. No se envía al servidor.

> 🔎 Para un cazador de bugs, los **parámetros** (`id=10`) son oro: muchos fallos aparecen al manipularlos. Lo veremos en el Módulo 04.

---

## 4. El protocolo HTTP: peticiones y respuestas

### Una petición HTTP tiene esta forma:

```http
GET /articulos/seguridad?id=10 HTTP/1.1
Host: blog.ejemplo.com
User-Agent: Mozilla/5.0 ...
Cookie: sesion=abc123
Accept: text/html
```

- **Línea de petición:** el método (`GET`), la ruta y la versión.
- **Cabeceras (headers):** información extra (qué navegador eres, qué idioma prefieres, tus cookies...).
- **Cuerpo (body):** datos que envías (en peticiones `POST`, por ejemplo, un formulario).

### Una respuesta HTTP tiene esta forma:

```http
HTTP/1.1 200 OK
Content-Type: text/html
Set-Cookie: sesion=abc123

<html> ... el contenido de la página ... </html>
```

- **Código de estado** (`200 OK`): te dice cómo fue.
- **Cabeceras de respuesta:** información sobre lo que te devuelve.
- **Cuerpo:** el contenido real (el HTML, el JSON de una API, etc.).

---

## 5. Métodos HTTP (los "verbos")

Cada petición usa un **método** que indica qué quieres hacer:

| Método | Para qué sirve | Analogía |
|--------|----------------|----------|
| `GET` | Pedir/leer datos | Mirar el menú |
| `POST` | Enviar/crear datos | Hacer un pedido nuevo |
| `PUT` | Actualizar/reemplazar | Cambiar tu pedido entero |
| `PATCH` | Actualizar una parte | Cambiar solo la bebida |
| `DELETE` | Borrar | Cancelar el pedido |

> 💡 Probar qué pasa al cambiar un `GET` por un `POST`, o al usar `DELETE` donde no deberías, es una técnica habitual en bug bounty.

---

## 6. Códigos de estado HTTP (memoriza las familias)

No memorices todos, solo el **primer dígito**:

- **2xx — Éxito:** `200 OK` (todo bien).
- **3xx — Redirección:** `301`/`302` (te mandan a otra URL).
- **4xx — Error del cliente (tú):** `403 Forbidden` (prohibido), `404 Not Found` (no existe), `401 Unauthorized` (necesitas identificarte).
- **5xx — Error del servidor:** `500 Internal Server Error` (la web "petó"). ¡Estos errores a veces revelan información útil!

---

## 7. Cookies y sesiones: cómo te "recuerda" la web

HTTP no tiene memoria: cada petición es independiente. Entonces, ¿cómo sabe la web que ya iniciaste sesión?

- Cuando te logueas, el servidor te da una **cookie** (un pequeño texto, como `sesion=abc123`).
- Tu navegador **guarda** esa cookie y la **envía** en cada petición siguiente.
- Así el servidor te reconoce: *"ah, eres el usuario de la cookie abc123"*.

> 🔑 Las cookies de sesión son como la **pulsera de un festival**: demuestran que ya pagaste la entrada. Si alguien te roba la pulsera (la cookie), puede hacerse pasar por ti. Por eso muchos ataques van dirigidos a robar o falsificar cookies.

---

## 8. Front-end vs Back-end

- **Front-end:** lo que ves y se ejecuta **en tu navegador** (HTML, CSS, JavaScript). Es el escaparate.
- **Back-end:** lo que ocurre **en el servidor**, donde no ves nada (bases de datos, lógica, validaciones). Es la trastienda.

Una regla clave de seguridad: **nunca te fíes del front-end.** Todo lo que se valida solo en el navegador, un atacante puede saltárselo. La seguridad de verdad vive en el **back-end**. Muchos bugs nacen de back-ends que confían demasiado en lo que llega del cliente.

---

## 9. APIs y JSON (rápido)

Muchas webs y apps hablan con el servidor a través de **APIs** (interfaces para intercambiar datos). En lugar de devolver una página HTML, devuelven datos en formato **JSON**:

```json
{
  "usuario": "ana",
  "rol": "cliente",
  "saldo": 100
}
```

> 🔎 Las APIs son una **mina de bugs** en el bug bounty moderno, porque a veces tienen menos protección que la web "bonita". Manipular estos campos (por ejemplo, cambiar `"rol": "cliente"` por `"rol": "admin"`) es un clásico.

---

## ✓ Resumen del módulo

- La web funciona con **cliente (navegador)** y **servidor**, hablando por **HTTP**.
- El **DNS** traduce nombres de dominio en direcciones IP.
- Una **URL** tiene partes (esquema, host, puerto, ruta, parámetros): los **parámetros** son zona caliente para bugs.
- HTTP usa **métodos** (GET, POST...) y **códigos de estado** (2xx, 3xx, 4xx, 5xx).
- Las **cookies** mantienen tu sesión: son un objetivo frecuente de ataque.
- **Nunca confíes en el front-end:** la seguridad real está en el back-end.
- Las **APIs (JSON)** son objetivos muy jugosos hoy en día.

---

## 📝 Ejercicio práctico

1. Abre tu navegador, pulsa **F12** (herramientas de desarrollador) y ve a la pestaña **"Red" / "Network"**. Recarga una web cualquiera y observa todas las peticiones HTTP que se hacen. Fíjate en los métodos y los códigos de estado.
2. En esa misma pestaña, haz clic en una petición y mira sus **cabeceras (headers)**. ¿Encuentras alguna cookie?
3. Identifica los parámetros (`?algo=valor`) en la URL de alguna web que uses. ¿Qué crees que controla cada uno?

> ⚠️ Recuerda: **solo observa**. Mirar tus propias peticiones es legal; manipular sistemas ajenos no.

---

[⬅️ Módulo 00](00-introduccion.md) · [Volver al índice](../README.md) · [Siguiente: Módulo 02 — Herramientas ➡️](02-herramientas-laboratorio.md)
