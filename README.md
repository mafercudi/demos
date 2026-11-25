# Commerce Demo Studio

Sitio estático para demos de Gupshup. Abre `index.html` o publica con GitHub Pages (Settings > Pages > Deploy from a branch > main / root).

- 🎨: personaliza nombre, logo, colores, catálogo JSON y productos individuales. Exporta el catálogo para reutilizarlo. Los cambios se pierden al recargar; el catálogo inicial es Enviaflores. Aplicar un catálogo reinicia el carrito.
- ⚙️: configura callback, token y customer ID. Se conserva la configuración original en localStorage. No incluyas credenciales en el repositorio.
- Los payloads `addedToCart` y `pagado` conservan sus campos originales. El pago es simulado; no hay backend. CORS del callback debe permitir el origen del sitio. La demo original no comprueba status HTTP ni lee la respuesta.
- El archivo `catalog-example.json` contiene el esquema y los productos iniciales.
