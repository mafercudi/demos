[README.md](https://github.com/user-attachments/files/35438669/README.md)
# Commerce Demo Studio

Sitio estático para demos de Gupshup. Abre `index.html` o publica con GitHub Pages (Settings > Pages > Deploy from a branch > main / root).

- 🎨: personaliza nombre, logo, colores, catálogo JSON y productos individuales. Exporta el catálogo para reutilizarlo. Los cambios se pierden al recargar; el catálogo inicial es Enviaflores. Aplicar un catálogo reinicia el carrito.
- ⚙️: configura callback, token y customer ID. Se conserva la configuración original en localStorage. No incluyas credenciales en el repositorio.
- Los payloads `addedToCart` y `pagado` conservan sus campos originales. El pago es simulado; no hay backend. CORS del callback debe permitir el origen del sitio. La demo original no comprueba status HTTP ni lee la respuesta.
- El archivo `catalog-example.json` contiene el esquema y los productos iniciales.

## V2 — Gupshup Retail
Identidad visual genérica inspirada en Gupshup (no es un kit oficial de marca). Integración incluye ejemplos dinámicos de ambos eventos, copia del JSON y último evento generado con estado HTTP o error de red. Se mantiene el contrato de datos original; ahora se comprueba el estado HTTP, pero el checkout sigue siendo simulado y no depende de la respuesta. Las credenciales se guardan localmente: solo para demos controladas.

## V3 — Recuperación de carrito
Ambos eventos incluyen `cart_url` además de los campos anteriores. El enlace guarda una instantánea de los productos seleccionados, cantidades y apariencia en el fragmento URL; funciona sin backend en otro navegador y abre directamente el carrito. No incluye token, callback ni customer ID. La tienda recuperada muestra solamente los productos seleccionados. El enlace representa la instantánea al generar el evento, no se actualiza tras eliminar o cambiar cantidades. URLs extensas pueden superar límites de canales o proveedores; para producción usar un ID de carrito corto con almacenamiento servidor y validación de precios. El checkout en otro navegador requiere configurar la integración localmente; no hay pago real.

## V4 — Simulación de comprador
Configura solo callback y Authorization. Pulsa Simular para iniciar un carrito nuevo y mostrar el banner de bienvenida. El número internacional se normaliza a dígitos y se usa como customer_id en ambos eventos; permanece en memoria de la sesión y no se incluye en cart_url. Si se intenta agregar o pagar sin número, se solicita primero y luego se reanuda la acción. DEMO10 es un código visual simulado, sin envío de WhatsApp ni descuento real; el registro no genera un evento nuevo. Los ejemplos del visor usan un número ficticio hasta capturar uno.

## V5 — Imágenes públicas
El catálogo conserva `img` como URL HTTPS directa, pública y sin credenciales. Los 13 productos originales conservan sus URLs CloudFront. `addedToCart` incluye `product_image_url`; `pagado` incluye el mismo campo dentro de cada objeto de `items`. El visor refleja ambos cambios. La validación comprueba formato, no disponibilidad pública efectiva.

## V6 — Enlaces cortos
El catálogo y tema originales usan `#c=1.2-4.1` (IDs y cantidades en base 36), recuperable en otro dispositivo con esta versión publicada. Para catálogos o temas personalizados se genera `#r=<id>` y la instantánea se guarda en localStorage; solo se recupera en el mismo navegador, perfil y origen. En Integración se puede activar «Enlace portable» para mantener la recuperación entre dispositivos de catálogos personalizados, con la URL larga anterior. Los enlaces `#cart=` de V5 siguen siendo compatibles. Los ejemplos de referencias locales no crean carritos. No se guardan credenciales ni número en los enlaces. Para referencias cortas universales de catálogos personalizados se necesita almacenamiento compartido.
