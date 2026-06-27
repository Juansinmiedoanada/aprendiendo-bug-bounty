# Módulo 04 — Vulnerabilidades web más comunes

> Aquí está la chicha. Vamos a conocer los **fallos de seguridad más habituales** que se reportan en bug bounty, explicados de forma sencilla: qué son, cómo funcionan, un ejemplo y cómo se previenen. Tomaremos como referencia el **OWASP Top 10**, la lista de riesgos web más conocida.

[⬅️ Módulo 03](03-reconocimiento.md) · [Volver al índice](../README.md) · [Siguiente: Módulo 05 ➡️](05-reportar-y-plataformas.md)

---

## ⚠️ Recordatorio legal

Todas estas técnicas se practican **solo** en laboratorios legales (Módulo 02) o en programas autorizados. Aquí explicamos los conceptos para que **entiendas y reportes** fallos, no para atacar a nadie.

---

## 0. ¿Qué es el OWASP Top 10?

**OWASP** es una organización sin ánimo de lucro dedicada a la seguridad del software. Su **Top 10** es una lista, actualizada periódicamente, de los 10 riesgos de seguridad más críticos en aplicaciones web. Es lectura **obligatoria** para cualquier hunter. Vamos a ver los fallos más representativos, en lenguaje llano.

---

## 1. IDOR — Referencia directa a objetos insegura

**Qué es:** cuando puedes acceder a datos de **otra persona** simplemente cambiando un número o identificador.

**Ejemplo:** ves tu factura en:
```
https://tienda.com/factura?id=1001
```
Cambias el número a `1000`... y **ves la factura de otro cliente**. La web no comprobó que esa factura fuera tuya.

**Por qué pasa:** el servidor confía en el ID que envías sin verificar que tengas permiso sobre él.

**Cómo se previene:** el servidor debe comprobar **siempre** que el recurso pertenece al usuario que lo pide.

> 💡 Es uno de los fallos **más fáciles de encontrar** para principiantes y muy frecuente. ¡Empieza por aquí!

---

## 2. XSS — Cross-Site Scripting

**Qué es:** conseguir que una web ejecute **JavaScript malicioso** en el navegador de otros usuarios.

**Ejemplo:** un campo de comentarios no filtra lo que escribes. Tú pones:
```html
<script>alert('XSS')</script>
```
Si la web lo guarda y lo muestra tal cual, ese script se ejecutará en el navegador de **todo el que vea el comentario**. Un atacante real lo usaría para robar cookies de sesión, por ejemplo.

**Tipos principales:**
- **Reflejado:** el script va en la URL/petición y se "refleja" en la respuesta inmediata.
- **Almacenado:** el script se guarda en la web (un comentario, un perfil) y afecta a quien lo vea. El más peligroso.
- **DOM-based:** el fallo ocurre en el JavaScript del propio navegador.

**Cómo se previene:** filtrar y "escapar" todo lo que el usuario envía antes de mostrarlo.

---

## 3. Inyección SQL (SQLi)

**Qué es:** manipular las **consultas a la base de datos** introduciendo código SQL en un campo.

**Ejemplo:** un login que construye la consulta así:
```sql
SELECT * FROM usuarios WHERE usuario='X' AND clave='Y';
```
Si en el campo usuario escribes `' OR '1'='1`, la consulta puede convertirse en algo que siempre es verdadero, y entrar **sin saber la contraseña**.

**Por qué es grave:** puede permitir leer, modificar o borrar **toda la base de datos** (usuarios, contraseñas, tarjetas...).

**Cómo se previene:** usar **consultas parametrizadas** (prepared statements), nunca construir SQL pegando texto del usuario.

---

## 4. Autenticación y gestión de sesiones rota

**Qué es:** fallos en cómo la web verifica quién eres y mantiene tu sesión.

**Ejemplos:**
- Contraseñas débiles permitidas o sin límite de intentos (fuerza bruta).
- Tokens de sesión predecibles o que no caducan.
- Poder saltarse pasos del login.
- Recuperación de contraseña insegura.

**Cómo se previene:** límites de intentos, tokens robustos y aleatorios, doble factor (2FA), caducidad de sesiones, etc.

---

## 5. CSRF — Cross-Site Request Forgery

**Qué es:** engañar al navegador de una víctima para que haga una acción **sin que ella quiera**, aprovechando que ya está logueada.

**Ejemplo:** estás logueado en tu banco. Visitas una web maliciosa que, en secreto, envía una petición a tu banco para transferir dinero. Como tu navegador **adjunta tus cookies automáticamente**, el banco cree que la orden la das tú.

**Cómo se previene:** usar **tokens anti-CSRF** (un valor secreto por formulario) y la propiedad `SameSite` en las cookies.

---

## 6. Configuraciones incorrectas de seguridad

**Qué es:** la web/servidor está mal configurado y expone cosas que no debería.

**Ejemplos:**
- Paneles de administración accesibles sin protección.
- Mensajes de error que revelan rutas internas, versiones o trozos de código.
- Archivos sensibles expuestos (`/.git/`, copias de seguridad, `.env` con contraseñas).
- Servicios con credenciales por defecto (admin/admin).

**Cómo se previene:** desactivar lo innecesario, ocultar errores detallados al usuario, revisar permisos y configuraciones.

---

## 7. Exposición de datos sensibles

**Qué es:** la web filtra información que debería estar protegida.

**Ejemplos:** datos personales en respuestas de API, contraseñas guardadas sin cifrar, tráfico sin HTTPS, claves de API en el código JavaScript del front-end.

**Cómo se previene:** cifrar datos en tránsito (HTTPS) y en reposo, no exponer más datos de los necesarios, nunca poner secretos en el front-end.

---

## 8. SSRF — Server-Side Request Forgery

**Qué es:** conseguir que **el servidor** haga peticiones a donde tú le digas, incluso a sistemas internos a los que tú no llegarías.

**Ejemplo:** una función que "trae" una imagen desde una URL que tú indicas. Si pones la dirección de un sistema interno (`http://localhost/admin` o servicios internos en la nube), el servidor podría acceder y devolverte información que no debería ser pública.

**Cómo se previene:** validar y restringir a qué direcciones puede conectarse el servidor.

---

## 9. Control de acceso roto

**Qué es:** un usuario puede hacer cosas que **no le corresponden** por su rol.

**Ejemplos:**
- Un usuario normal accede a funciones de administrador cambiando una URL o un parámetro (`?admin=true`).
- Acceder a `/admin/panel` directamente sin ser admin.
- IDOR (visto antes) es un tipo de control de acceso roto.

**Cómo se previene:** comprobar permisos en el **servidor** para cada acción, no fiarse de lo que oculta el front-end.

---

## 10. Componentes con vulnerabilidades conocidas

**Qué es:** la web usa librerías, plugins o software **desactualizados** con fallos ya públicos.

**Ejemplo:** un WordPress con un plugin viejo que tiene una vulnerabilidad conocida y documentada (con su CVE). Cualquiera puede buscar el exploit público.

**Cómo se previene:** mantener todo actualizado y vigilar los avisos de seguridad (CVE).

> 🔎 Herramientas como **Nuclei** automatizan la búsqueda de muchos de estos fallos conocidos.

---

## 11. Otros fallos que verás a menudo

- **Open Redirect:** la web te redirige a cualquier URL que pongas en un parámetro, útil para engaños/phishing.
- **Subdomain Takeover:** un subdominio apunta a un servicio externo abandonado que tú puedes reclamar (recuerda el recon del Módulo 03).
- **Fuga de información (Information Disclosure):** mensajes de error, comentarios en el código, cabeceras... que revelan datos internos.
- **Carga de archivos insegura:** subir un archivo malicioso porque no se valida el tipo.

---

## 🧭 ¿Por dónde empiezo como novato?

No intentes aprenderlos todos a la vez. Una ruta recomendada para tus primeros pasos:

1. **IDOR** → fácil de entender y encontrar.
2. **XSS** → muy común y didáctico.
3. **Control de acceso roto** → conceptualmente sencillo.
4. **Open Redirect** y **fugas de información** → buenos primeros hallazgos.
5. Luego ya: **SQLi**, **CSRF**, **SSRF**...

> 🎯 Practica cada uno en la **PortSwigger Web Security Academy**: tiene laboratorios dedicados a cada vulnerabilidad, con teoría y práctica guiada.

---

## ✓ Resumen del módulo

- El **OWASP Top 10** es la referencia de los riesgos web más críticos. Lectura obligatoria.
- **IDOR:** acceder a datos ajenos cambiando un ID. Ideal para empezar.
- **XSS:** inyectar JavaScript que se ejecuta en otros usuarios (reflejado, almacenado, DOM).
- **SQLi:** manipular consultas a la base de datos; muy grave.
- **CSRF:** forzar acciones aprovechando la sesión de la víctima.
- **SSRF:** hacer que el servidor pida recursos por ti, incluso internos.
- **Control de acceso roto** y **malas configuraciones**: muy frecuentes y a menudo fáciles.
- **Componentes desactualizados:** fallos conocidos (CVE) listos para encontrar.
- Empieza por los **fáciles** (IDOR, XSS, open redirect) y practica en laboratorios.

---

## 📝 Ejercicio práctico

1. Entra en la **PortSwigger Web Security Academy** y completa **un laboratorio de IDOR** (lo llaman "access control") y **uno de XSS reflejado**. Sigue las pistas si te atascas: aprender el proceso es lo importante.
2. Lee la página oficial del **OWASP Top 10** y resume con tus palabras 3 de los riesgos.
3. Para cada vulnerabilidad de este módulo, escribe en tus notas **una frase** que explique cómo la reconocerías "en el mundo real".

---

[⬅️ Módulo 03](03-reconocimiento.md) · [Volver al índice](../README.md) · [Siguiente: Módulo 05 — Reportar y plataformas ➡️](05-reportar-y-plataformas.md)
