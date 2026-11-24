# Marea Studio

Aplicación de escritorio para crear videos verticales con agentes de IA. Permite investigar una idea, escribir el guion,
preparar la voz, componer y renderizar el video en el equipo.

## Desarrollo

Requiere Node.js 24. Instala las dependencias con `npm ci` y ejecuta `npm start`. La aplicación local abre el servidor en
`http://localhost:4848`. Conecta el proveedor de IA desde **Opciones → Agentes**. Para compilar el instalador de esta
plataforma, ejecuta `npm run compilar`.

La cuenta, la comunidad en línea, el catálogo remoto de voces y las actualizaciones remotas están apagados por defecto.
La integración de servicios propios solo se activa al configurar `MAREA_SERVICES_URL`. Marea Studio no envía claves,
archivos ni datos a los servicios del proyecto de origen.

## Licencia y avisos

El proyecto se distribuye bajo MIT. Se conservan los avisos de copyright y permisos de `LICENSE` y `NOTICE`, incluidos
los de los componentes de terceros.
