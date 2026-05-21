# Política de Privacidad de Firulais

**Última actualización: 21 de mayo de 2026**

Firulais es un cliente de API diseñado con la privacidad y la seguridad como prioridades fundamentales. Esta Política de Privacidad describe cómo se maneja la información dentro de la aplicación.

## 1. Filosofía "Offline-First"
Firulais es una aplicación **offline-first**. Esto significa que:
- No requerimos la creación de una cuenta para utilizar la aplicación.
- No almacenamos sus datos en nuestros propios servidores.
- No rastreamos su comportamiento ni recopilamos telemetría de uso.

## 2. Recopilación y Uso de la Información
Toda la información que usted introduce en Firulais se almacena exclusivamente en su dispositivo local. Esto incluye:
- **Colecciones y Peticiones:** URLs, cabeceras, cuerpos de mensaje y configuraciones de peticiones HTTP.
- **Variables de Entorno:** Incluyendo claves de API, tokens y otros datos sensibles.
- **Scripts:** Código JavaScript escrito para pre-solicitudes o post-respuestas.
- **Historial de Respuestas:** Datos devueltos por los servidores de las APIs a las que usted llama.

## 3. Seguridad de los Datos
- **Almacenamiento Local:** Los datos se guardan localmente utilizando bases de datos seguras (Hive) en el espacio de almacenamiento privado de la aplicación en su sistema operativo.
- **Cifrado:** Firulais utiliza librerías de cifrado para proteger la integridad de sus datos locales cuando es necesario.
- **Control Total:** Usted tiene el control total sobre sus datos. Puede eliminar colecciones, entornos o borrar todos los datos de la aplicación en cualquier momento.

## 4. Comunicaciones Externas
Firulais solo realiza comunicaciones externas en los siguientes casos:
- **Peticiones HTTP Iniciadas por el Usuario:** La aplicación envía peticiones a los servidores de las APIs que usted especifique. Firulais actúa únicamente como un intermediario técnico; el contenido y el destino de estas peticiones son responsabilidad exclusiva del usuario.
- **Exportación Manual:** Si decide exportar sus colecciones o entornos, el archivo resultante se genera localmente para que usted lo comparta a través de los medios que prefiera.

## 5. Servicios de Terceros
Firulais no integra servicios de terceros que recopilen su información personal, como redes de anuncios o servicios de analítica.

## 6. Cambios en esta Política
Podemos actualizar nuestra Política de Privacidad de vez en cuando. Cualquier cambio se verá reflejado en la fecha de "Última actualización" en la parte superior de este documento.

## 7. Contacto
Al ser un proyecto de código abierto/local, si tiene dudas sobre la privacidad, puede revisar el código fuente directamente o abrir un issue en el repositorio del proyecto.

---
**Nota:** Firulais no se hace responsable de las prácticas de privacidad de los servicios de API de terceros con los que usted interactúa a través de la aplicación.
