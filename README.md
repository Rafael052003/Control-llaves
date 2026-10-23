# Control de Llaves — PWA para GitHub Pages

Paquete listo para publicar como sitio estático de GitHub Pages. Conserva la aplicación HTML existente y agrega manifiesto PWA, iconos, registro del service worker y caché para uso sin conexión después de la primera carga.

## Archivos

- `index.html`: aplicación web.
- `manifest.json`: nombre, colores, modo independiente e iconos de instalación.
- `sw.js`: caché del shell de la aplicación y de recursos utilizados después de cargarlos una vez.
- `icons/`: iconos PNG para instalación normal y maskable.
- `.nojekyll`: evita procesamiento de Jekyll.

## Publicar en GitHub Pages

1. Crea un repositorio en GitHub, por ejemplo `control-de-llaves`.
2. Sube **todos** los archivos y carpetas de este paquete a la raíz del repositorio. El archivo principal debe quedar como `index.html`, no dentro de otra carpeta.
3. En el repositorio entra a **Settings → Pages**.
4. En **Build and deployment**, elige **Deploy from a branch**.
5. Selecciona la rama `main` y la carpeta `/(root)`, y guarda.
6. Espera a que GitHub Pages publique el sitio. Abre la URL HTTPS que GitHub te muestre.
7. En Android, abre esa URL con Chrome. Usa el botón **Instalar app** si aparece o el menú ⋮ → **Instalar aplicación** / **Añadir a pantalla de inicio**.

## Importante sobre el modo sin conexión

- La instalación PWA requiere HTTPS; GitHub Pages lo proporciona automáticamente.
- Abre la app con internet al menos una vez para que el navegador guarde el HTML y las librerías externas en caché. Algunas fuentes y bibliotecas se cargan desde CDN, así que el primer inicio necesita conexión.
- Los registros se guardan en `localStorage` del navegador/dispositivo. No se sincronizan automáticamente entre teléfonos ni oficiales. Usa **Respaldar** regularmente y guarda el JSON en un lugar seguro.
- El inicio de sesión usa contraseñas definidas dentro del JavaScript (`1234` en esta versión). Esto no es autenticación segura para datos sensibles: cualquiera con acceso al código puede verlas. Cambia esas credenciales antes de un uso real y no publiques datos personales en un repositorio público.
- El service worker puede tardar un momento en actualizar la app publicada. Si no ves los cambios, cierra y vuelve a abrir la app o borra los datos del sitio desde Chrome.

## Prueba local

No abras `index.html` mediante `file://` para probar la instalación. Ejecuta un servidor local (por ejemplo `python -m http.server 8000`) y abre `http://localhost:8000`; para instalar en otros dispositivos usa la versión HTTPS de GitHub Pages.
