# Mi lector RSS

Lector web de fuentes RSS 2.0 y Atom. Interfaz en español, diseño adaptable y almacenamiento local en IndexedDB.

## Funciones
- Suscripciones RSS/Atom, categorías, búsqueda, favoritos y leído/no leído.
- Importación y exportación de OPML.
- Actualización al abrir y al pulsar **Actualizar**.
- Datos guardados en el navegador: no hay cuenta ni base de datos remota y no se sincronizan entre dispositivos.

## Publicación
1. En Cloudflare, creá un Worker llamado `mi-lector-rss-proxy`.
2. Pegá el contenido de `worker.js`, guardá y desplegá.
3. Copiá la URL `.workers.dev` del Worker.
4. Editá `config.js` y reemplazá el valor de `RSS_API_BASE` por esa URL.
5. En el Worker, configurá opcionalmente la variable `ALLOWED_ORIGINS` con `https://EzequielEsposito.github.io` para limitar los sitios que pueden usar el proxy.
6. En GitHub, abrí Settings > Pages y elegí **GitHub Actions** como método de publicación. El workflow de `.github/workflows/pages.yml` publicará automáticamente cada commit en `main`.

La dirección esperada será `https://EzequielEsposito.github.io/mi-lector-rss/`.

## Límites y privacidad
Los artículos, suscripciones, categorías y estados se guardan localmente en el navegador. Exportá OPML para respaldar las suscripciones (no incluye favoritos ni estados de lectura). La actualización no ocurre cuando el navegador está cerrado. Algunos sitios bloquean lectores externos o tienen feeds incompletos. Cloudflare Workers tiene límites de uso según el plan. El proxy permite HTTP/HTTPS y bloquea algunos destinos locales; restringí `ALLOWED_ORIGINS` al dominio de GitHub Pages.
