# 🧠 CEREBRO: Marea Studio

**Última actualización:** 2026-11-13 21:56 (America/Santo_Domingo)

**Estado general:** En progreso

## 1. IDENTIDAD DEL PROYECTO

- Objetivo: crear Marea Studio, una aplicación propia basada en Sloth para producir videos verticales asistidos por agentes de IA.
- Resultado esperado / criterio de "terminado": proyecto instalado, ejecutable en este entorno y personalizado como aplicación propia; funciones y límites documentados tras inspeccionar el código.
- Público o cliente: usuario solicitante.
- Fecha límite: no indicada.

## 2. CONTEXTO CLAVE

- Información de fondo imprescindible: el usuario autorizó elegir el nombre (“sorpréndeme”) y pidió aplicar este protocolo de cerebro al proyecto.
- Herramientas, tecnologías o recursos usados: repo clonado desde `https://github.com/Vancci-sloth/sloth` en `main`; Electron, React/Vite, Node, Claude Agent SDK, Remotion, Python y servicios Cloudflare.
- Enlaces, rutas de archivos y credenciales de referencia: https://github.com/Vancci-sloth/sloth
- Personas involucradas y su rol: usuario, propietario del proyecto; Codex, asistente de implementación.

## 3. DECISIONES TOMADAS

| Fecha | Decisión | Motivo | Alternativas descartadas |
|-------|----------|--------|--------------------------|
| 2026-11-13 | ~~Usar “Sloth Clone” como nombre provisional.~~ Obsoleto: el usuario dijo “sorpréndeme”. | Nombre inicial solo provisional. | — |
| 2026-11-13 | Nombrar la aplicación “Marea Studio”. | Elección creativa autorizada por el usuario; alude al flujo de creación que toma una idea y la convierte en video. | No se descartan alternativas. |
| 2026-11-13 | Basar la implementación en el repositorio existente y conservar su arquitectura inicialmente. | El usuario pidió sus funciones; el README describe una app de escritorio completa. | Rehacerla desde cero antes de conocer el código. |
| 2026-11-13 | Publicar una página estática de Marea Studio con el instalador en un subdominio Hostinger gratuito nuevo. | El usuario pidió desplegarlo; evita tocar 27 sitios existentes y permite descargar la app mientras el servidor siga siendo solo local. | Exponer el servidor Electron/local tal cual. |
| 2026-11-13 | Quitar marca visible e integraciones de los servicios de Sloth, conservando `LICENSE` y `NOTICE` requeridos. | Decisión explícita del usuario tras explicar el conflicto con la atribución MIT. | Reescritura completa independiente; borrar avisos legales. |
| 2026-11-13 | El usuario pide instalar las dependencias descargadas dentro de la carpeta de Marea Studio y elegir individualmente cuáles conservar al desinstalar. | Evitar archivos dispersos y permitir conservar dependencias elegidas. | Mantenerlas en `%APPDATA%` sin opción individual. |

## 4. PLAN DE PASOS

- [x] Paso 1: buscar un BRAIN.md existente; no se encontró ninguno (2026-11-13).
- [x] Paso 2: elegir nombre: Marea Studio; revisar descripción y pasos de instalación del README (2026-11-13).
- [x] Paso 3: integrar rama `main` del repo y leer `AGENTS.md` (2026-11-13).
- [x] Paso 4: instalar dependencias y comprobar HTTP 200 del servidor local (2026-11-13).
- [x] Paso 5: personalizar marca, iconos, paquete y desactivar actualizaciones upstream por defecto (2026-11-13).
- [x] Paso 6: verificar typecheck y tests; confirmar arranque con nombre Marea Studio (2026-11-13).
- [x] Paso 7: resolver metadatos npm y compilar el instalador Windows; artefacto de 222 MB (2026-11-13).
- [x] Paso 8: completar requisitos locales; Torch 2.8 CUDA importó y reportó CUDA disponible; faltantes de modelos: ninguno (2026-11-13).
- [x] Paso 9: revisar y documentar servicios externos que requieren configuración propia (2026-11-13).
- [x] Paso 10: revisar compatibilidad de la app con Hostinger; confirmar plan Cloud activo y que el servidor está diseñado para localhost, no para usuarios públicos (2026-11-13).
- [x] Paso 11: publicar página de presentación y descarga en subdominio gratuito nuevo de Hostinger; comprobados HTTP 200 y tamaño del instalador (2026-11-13).
- [ ] **Paso 12 (ACTUAL):** diseñar/adaptar una versión web segura para navegador; la app actual sigue siendo de escritorio.
- [x] Paso 13: definir el alcance: quitar marca visible e integraciones de Sloth, conservar avisos requeridos (2026-11-13).
- [x] Paso 14: retirar marca visible, desconectar integraciones upstream por defecto y compilar/validar el instalador Marea 0.4.0; 436/436 tests, typecheck y prueba NSIS correctos (2026-11-13).
- [x] Paso 15: reemplazar en Hostinger la descarga anterior por el instalador limpio, con aprobación del usuario; portada y descarga verificadas (2026-11-13).
- [x] Paso 16: limpiar rastros visibles restantes en novedades, iconos de voces, instalador y selección de estilos; typecheck y 436/436 tests correctos (2026-11-13).
- [x] Paso 17: reconstruir el instalador limpio y desplegar la versión actualizada en Hostinger; portada y descarga responden 200 (2026-11-13).
- [x] Paso 18: reubicar dependencias descargadas bajo la instalación, migrar las existentes y añadir opciones individuales de conservación al desinstalar; typecheck y 436 pruebas aprobadas (2026-11-13).
- [x] Paso 19: reconstruir y publicar el instalador con dependencias locales; portada y descarga HTTP 200, tamaño remoto coincide (2026-11-13).

## 5. PASO ACTUAL EN DETALLE

- Qué estoy haciendo: planear la adaptación web segura; Marea Studio sigue siendo una aplicación de escritorio.
- Qué ya se avanzó: destino local en `app/ia` (IA de transcripción), `app/piezas` (Python, FFmpeg y agentes), `app/modulos` y `app/modulos-diff` (paquetes Node). El arranque migra rutas anteriores y deja alias de compatibilidad. «Cambiar de disco» mueve solo videos. El desinstalador pregunta por separado si borrar o conservar IA, Python/paquetes, FFmpeg, programas de agentes y módulos Node; videos e hilos mantienen su pregunta. Typecheck OK, suite completa 436/436, NSIS compiló. Instalador publicado con SHA-256 `EB284004ECAA4C0A26B2B9AD99C081EED01580FA35BDD9FDFD2B0EB89845391D`, tamaño 222343592 bytes; Hostinger API y descarga HTTP 200 reportan ese tamaño. Página HTTP 200.
- Qué falta exactamente: adaptar la aplicación de escritorio a navegador con autenticación, almacenamiento aislado y procesamiento remoto.
- Siguiente acción concreta: diseñar arquitectura y alcance de la versión web multiusuario antes de exponer servicios locales.

## 6. BLOQUEOS Y PREGUNTAS ABIERTAS

- ❓ “Aplicar el prompt del cerebro” se interpreta como mantener BRAIN.md para Marea Studio; confirmar luego si también significa integrar una función de memoria dentro de la app.
- ❓ “Que funcione 100%” requiere convertir las funciones del repositorio en criterios verificables tras inspeccionarlo.
- ~~❓ La orden actual entra en conflicto con conservar avisos MIT/NOTICE.~~ Resuelto (2026-11-13): quitar marca e integraciones upstream, conservar avisos de licencia y copyright requeridos.

## 7. APRENDIZAJES Y ERRORES (para no repetirlos)

- Lo que funcionó: no se encontró una memoria previa que pudiera contradecir esta solicitud.
- Lo que NO funcionó y por qué: la primera compilación usó `publish: "never"`, que electron-builder interpretó como proveedor inválido; se corrigió omitiendo `publish` cuando no hay URL propia.

## 8. REGLAS Y PREFERENCIAS DEL PROYECTO

- Mantener este archivo como memoria persistente; nunca borrar historial, solo agregar o marcar obsoleto con motivo.
- No inventar datos ausentes; documentar dudas y pedir aclaración cuando haga falta.
- Tras cada paso importante, actualizar BRAIN.md y confirmar en una línea qué cambió.
- Responder en español, de forma concisa.

## 9. BITÁCORA DE SESIONES

### Sesión 2026-11-13

- Hecho: repo integrado; dependencias instaladas; servidor contestó HTTP 200; marca Marea Studio aplicada a interfaz, iconos, metadatos y README.
- Pendiente: verificar `koffi`, completar Python/modelos; Comunidad, licencias/clonación de voz y publicación en nube requieren configuración propia.
- Próximo paso: probar importación de `koffi` desde el artefacto compilado.

### Sesión 2026-11-13 (continuación)

- Hecho: se verificó que el instalador existe (222 MB) y que `koffi` importa desde el artefacto extraído. Se encontró un proceso Python activo bajando/instalando Torch CUDA; la caché de pip ya ocupa aproximadamente 3,56 GB. La ventana aún marca Python y los paquetes de Python como faltantes.
- Pendiente: esperar a que finalice la instalación local, confirmar paquetes/modelos y revisar con precisión las dependencias de servicios externos.
- Próximo paso: volver a consultar el estado del proceso y la pantalla de requisitos; no cerrar la app mientras instala Torch.

### Sesión 2026-11-13 (verificación del runtime)

- Hecho: la API `/api/requisitos?fresco` confirmó FFmpeg 9.0.2, Python 3.14.7, paquetes de Python y Codex conectados. Se abrió la pantalla principal de Marea Studio. El proceso que instala Torch continúa con conexión HTTPS.
- Pendiente: termina la instalación de Torch CUDA y sus modelos; la lectura visual del panel de requisitos no se refrescó con Ctrl+R.
- Próximo paso: consultar la API local y verificar los modelos cuando `python-sloth` deje de estar `instalando`; después intentar el flujo local de video sin gastar llamadas pagadas.

### Sesión 2026-11-13 (descarga de Torch)

- Hecho: Torch CUDA (3,46 GB) y sus dos ruedas pequeñas se descargaron correctamente; la API pasó a «Instalando los paquetes». FFmpeg, Python general, paquetes Python y Codex figuran listos.
- Pendiente: terminar la instalación de dependencias y bajar/verificar modelos; la API sigue indicando `python-sloth: instalando`.
- Próximo paso: seguir consultando `/api/requisitos?fresco`; al completar, probar que Torch importa y que el transcriptor reconoce sus modelos.

### Sesión 2026-11-13 (modelos)

- Hecho: pip instaló Torch CUDA, torchaudio, torchvision y dependencias; se descargaron Whisper `large-v3-turbo`, `voxpopuli-es` y `multilingual-e5-small`. La API local informa todos los requisitos listos.
- Pendiente: configurar servicios propios de Comunidad, licencias/clonación de voz y publicación cloud; generar un video real con el agente/voz que el usuario elija.
- Próximo paso: preparar configuración de esos servicios y acordar el primer tema/voz antes de gastar créditos de producción.

### Sesión 2026-11-13 (validación del runtime)

- Hecho: import de `torch`, `torchaudio` y `torchvision` exitoso: `2.8.0+cu128`, CUDA disponible (`True`); `modelos_transcripcion.check()` devolvió sin faltantes ni mejoras pendientes.
- Pendiente: integraciones externas y validación de un video final de principio a fin.
- Próximo paso: conectar servicios propios; hacer una producción de prueba con tema y voz definidos.

### Sesión 2026-11-13 (Hostinger)

- Hecho: confirmé un plan `cloud_economy_v3`, 27 sitios existentes (10 detectados Node.js) y el diseño local del servidor (loopback + guardia de origen para la ventana propia).
- Pendiente: elegir si publicar una landing/descarga de escritorio o construir una versión web segura; elegir un dominio/subdominio concreto.
- Próximo paso: esperar el destino/formato elegido; no desplegar sobre uno de los sitios existentes sin ese dato porque reemplazaría sus contenidos.

### Sesión 2026-11-13 (publicación Hostinger)

- Hecho: construí `publicacion-hostinger/` con página de presentación, marca visual y enlace al instalador Windows; aprovisioné un sitio gratuito nuevo `mediumspringgreen-lyrebird-279467.hostingersite.com` en la orden Cloud activa; desplegué la página e instalador.
- Verificación: portada HTTP 200, título “Marea Studio — de la idea al video”; instalador HTTP 200, Content-Length 222343425.
- Pendiente: esta página distribuye la aplicación Windows, pero no ofrece la app completa en navegador; para eso se requiere una adaptación segura y multiusuario.
- Próximo paso: diseñar el backend web multiusuario (autenticación, almacenamiento aislado, permisos y agentes/procesamiento cloud) antes de exponer endpoints de la app local.

### Sesión 2026-11-13 (limpieza de marca)

- Hecho: auditoría local encontró más de 2.400 referencias a Sloth; la página pública no tiene esas referencias, pero el instalador sí incluye el código derivado. `LICENSE` y `NOTICE` contienen el aviso MIT y copyright de Vancci.
- Hecho: el usuario decidió quitar la marca visible y las integraciones de Sloth conservando avisos legales requeridos.
- Pendiente: limpiar textos de producto, desactivar integraciones con servicios originales, reconstruir instalador y revisar contenido publicado.
- Próximo paso: auditar endpoints/URLs upstream, hacer cambios compatibles y validar que Marea Studio siga iniciando.

### Sesión 2026-11-13 (limpieza y paquete)

- Hecho: se quitó la marca visible, se desactivaron conexiones upstream por defecto, se retiraron workflows de publicación y el remote Git original. `LICENSE` y `NOTICE` se conservaron. Typecheck OK; tests 436/436 OK; prueba NSIS OK. Instalador `Marea-Studio-Setup-0.4.0.exe`, SHA-256 `772A021AF9334DCCD43DD8AA5642ACAED70A8324A2031A0A54ACE5906CF8D05F`.
- Pendiente: confirmar antes de sobrescribir en Hostinger el archivo público actual.
- Próximo paso: recibir confirmación y desplegar el artefacto preparado; verificar descarga pública.

### Sesión 2026-11-13 (despliegue rebrandeado)

- Hecho: con la autorización del usuario se sustituyó el contenido del sitio Hostinger. Portada 200 con título “Marea Studio — de la idea al video”, sin coincidencias de marca anterior; descarga 200, MIME ejecutable, tamaño coincide con el artefacto local (222342703 bytes).
- Pendiente: hash remoto no confirmado porque el entorno bloqueó la descarga del ejecutable; el hash local se conserva arriba.
- Próximo paso: diseñar la adaptación web segura para navegador si el usuario quiere continuar con la modalidad online.

### Sesión 2026-11-13 (limpieza final de interfaz e instalador)

- Hecho: se eliminó la palabra y mascota Sloth de la guía animada de novedades; los iconos de voces y su ancla usan identidad Marea; el selector de archivos solo ofrece `.marea-estilo`; instalaciones nuevas usan la carpeta Marea Studio y se conserva reconocimiento de instalaciones antiguas para no perder datos. Typecheck OK; tests 436/436.
- Hecho: instalador reconstruido y publicado en el mismo sitio Hostinger ya aprobado. SHA-256 `18255E6AF7D3A5F0CBAA857C55B92ED59BAA10A661F1005613209D826FE63EB3`, 222342793 bytes; landing y descarga responden HTTP 200 y sus tamaños coinciden. Se comprobó que el HTML de la portada no menciona la marca anterior.
- Pendiente: adaptar la aplicación de escritorio a navegador seguro y multiusuario.
- Próximo paso: diseñar el backend web (autenticación, datos aislados y procesamiento remoto).

### Sesión 2026-11-13 (dependencias portables)

- Hecho: el usuario pidió que las dependencias descargadas vivan bajo la carpeta de instalación y poder conservarlas individualmente al desinstalar.
- Pendiente: rastrear rutas de Python, modelos, FFmpeg, agentes y módulos; definir migración y menú de conservación.
- Próximo paso: terminar el mapa de consumidores y diseñar directorios locales compatibles con el uso actual.

### Sesión 2026-11-13 (implementación de dependencias locales)

- Hecho: se implementaron rutas relativas a la instalación para IA, Python/FFmpeg, agentes y módulos Node; migración desde ubicaciones antiguas con enlaces de compatibilidad; la función «Cambiar de disco» conserva solo el movimiento de videos; el desinstalador pregunta por IA, Python, FFmpeg, agentes y módulos de video por separado.
- Hecho: typecheck OK; pruebas focalizadas 20/20 y suite completa 436/436; NSIS generó correctamente el instalador con los diálogos de conservación. Instalador publicado; SHA-256 `EB284004ECAA4C0A26B2B9AD99C081EED01580FA35BDD9FDFD2B0EB89845391D`, 222343592 bytes. Hostinger API confirma tamaño; portada y descarga HTTP 200.
- Pendiente: adaptar la app de escritorio a navegador seguro multiusuario.
- Próximo paso: diseñar backend web (autenticación, datos aislados y procesamiento remoto).

