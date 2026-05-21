# 🐾 FIRULAIS - API Client

**Firulais** es un cliente de API ligero, potente y moderno diseñado para desarrolladores que buscan una alternativa rápida y eficiente para probar y organizar sus peticiones HTTP. Inspirado en herramientas líderes como Postman y Bruno, Firulais ofrece una experiencia fluida con soporte nativo para los estándares de la industria.

---

## ✨ Características Principales

### 📁 Organización Jerárquica
No más listas infinitas de peticiones. Firulais permite organizar tu trabajo mediante **carpetas y subcarpetas anidadas**, facilitando la gestión de proyectos grandes y complejos.

### 🔄 Compatibilidad Total (Bidireccional)
Firulais actúa como un puente perfecto entre tus herramientas favoritas:
*   **Importación**: Soporta archivos JSON de Postman (v2.1) y exportaciones de Bruno (ZIP, archivos `.bru`, YAML y el nuevo estándar OpenCollection).
*   **Exportación**: Lleva tus datos de vuelta a Postman o Bruno en cualquier momento con un solo clic.

### 🌍 Gestión de Entornos
Gestiona variables globales y de entorno fácilmente. Cambia entre contextos (Desarrollo, QA, Producción) y Firulais sustituirá automáticamente tus variables `{{variable_name}}` en URLs, cabeceras y cuerpos de mensaje.

### 🛠️ Herramientas de Desarrollador
*   **Generador de cURL**: Obtén el comando cURL equivalente de cualquier petición al instante.
*   **Beautifier JSON**: Formatea automáticamente tus cuerpos de petición con un solo botón.
*   **Resaltado de Sintaxis**: Visualización clara de variables y resaltado de código.

---

## 📜 El Poder de los Scripts (JavaScript Engine)

Firulais incluye un motor de JavaScript integrado que permite automatizar tareas complejas antes y después de cada petición. Es compatible con los estándares de **Bruno** y **Postman**, lo que facilita la migración de tus flujos de trabajo.

### 🛠 Objetos Globales Disponibles

| Objeto | Descripción | Compatibilidad |
| :--- | :--- | :--- |
| `firu` | **Nativo de Firulais**. Control preciso sobre entornos y colección. | Nativo |
| `bru` | Acceso a variables y entorno al estilo Bruno. | Bruno |
| `pm` | Acceso a variables, entorno y tests al estilo Postman. | Postman |
| `res` | Acceso rápido a los datos de la respuesta (`res.body`, `res.status`). | Bruno |
| `req` | Acceso a los datos de la petición saliente. | Bruno |
| `console` | Salida de mensajes a la consola integrada de Firulais. | Estándar |

---

### 🐾 Scripts Nativos de Firulais (Objeto `firu`)

Firulais permite elegir exactamente dónde persistir tus datos para un control total:

```javascript
// 1. Guardar en el ENTORNO activo (ideal para Tokens, Cookies, SessionIDs)
firu.setEnvVar("mi_token", "abc-123");

// 2. Guardar en la COLECCIÓN (ideal para configuraciones fijas o globales)
firu.setCollectionVar("api_version", "v2");

// 3. Obtener variable (prioridad: Entorno > Colección)
let val = firu.getVar("mi_token");
console.log("El valor es: " + val);
```

---

### 📝 Ejemplos de Scripts de Pre-request (Antes de enviar)

Úsalos para configurar autenticación dinámica, generar timestamps o hashes.

#### 1. Generar un Header de Autenticación Dinámico
```javascript
// Genera un ID único para la petición
let requestId = Math.random().toString(36).substring(7);
req.headers.add("X-Request-ID", requestId);

// Generar un Timestamp
let timestamp = new Date().getTime();
bru.setVar("current_timestamp", timestamp);
```

#### 2. HMAC o Firmas Digitales
```javascript
// Firulais expone utilidades de hashing (MD5 y SHA256)
let dataToSign = "user_id:123";
let signature = firu.utils.hash(dataToSign, "sha256");
req.headers.add("X-Signature", signature);
```

---

### 🧪 Ejemplos de Scripts de Post-response (Al recibir respuesta)

Úsalos para extraer datos de la respuesta, encadenar peticiones o validar resultados.

#### 1. Extraer y Guardar un Token (Encadenamiento de APIs)
```javascript
// Acceso directo a la respuesta parseada como JSON
let data = res.getBody();

if (res.getStatus() === 200 && data.access_token) {
    // Guarda el token en el entorno activo para usarlo como {{token}}
    bru.setEnvVar("token", data.access_token);
    console.log("✅ Token actualizado correctamente");
} else {
    console.log("❌ No se pudo obtener el token");
}
```

#### 2. Pruebas Automatizadas (Estilo Postman)
```javascript
pm.test("Status code es 200", function () {
    pm.response.to.have.status(200);
});

pm.test("El cuerpo tiene un ID válido", function () {
    let jsonData = pm.response.json();
    pm.expect(jsonData.id).to.be.a("number");
});
```

#### 3. Depuración Compleja en Consola
```javascript
let headers = res.getHeaders();
console.log("Headers recibidos:");
console.log(headers);

// Ver el tiempo de expiración de una cookie
if (headers['set-cookie']) {
    console.log("Cookies detectadas: " + headers['set-cookie']);
}
```

---

## 🚀 Guía Rápida de Inicio

1.  **Importar**: Haz clic en el botón de descarga y selecciona tu ZIP de Bruno o JSON de Postman.
2.  **Entorno**: Crea un entorno en la pestaña "Entornos" y añade una variable `baseUrl`.
3.  **Petición**: Crea una nueva petición, pon la URL `{{baseUrl}}/api/status`.
4.  **Ejecutar**: Pulsa **Send**. Si el servidor responde un JSON, Firulais lo formateará automáticamente.
5.  **Automatizar**: Ve a la pestaña **Scripts**, pega un `console.log(res.body)` en Post-response y vuelve a enviar. ¡Mira los resultados en la pestaña **Console**!

---

## 🔒 Seguridad y Privacidad
Firulais es **offline-first**. Tus datos, variables de entorno y scripts se guardan localmente en una base de datos segura. Nada se envía a servidores externos a menos que tú decidas exportar manualmente tus colecciones.

Para más detalles, consulta nuestra [Política de Privacidad](./PRIVACY_POLICY.md).

---

**¡Domina tus APIs con Firulais!** 🐾
