[README.md](https://github.com/user-attachments/files/31341109/README.md)
# Sembrando Futuro

Sistema web de gestión de plantaciones de árboles para la **Subdirección de Gestión Social, Alcaldía de Panamá**. Permite registrar sitios de siembra en un mapa, dar seguimiento a su mantenimiento y compartir la ficha de cada plantación mediante código QR.

Es una aplicación de una sola página (HTML + CSS + JavaScript), sin backend ni build step: todo corre en el navegador.

## Funcionalidades

- **Mapa público** con los sitios de plantación, filtrable por corregimiento, tipo de árbol y estado (plantado / por plantar).
- **Panel de administración** con:
  - KPIs generales (árboles plantados, sitios registrados, etc.)
  - Gráficas de árboles plantados por corregimiento y por especie
  - Alertas de próximos mantenimientos (vencidos, próximos 5 días, programados)
  - Tabla de todas las plantaciones con búsqueda, edición y eliminación
  - Íconos personalizados: además de un catálogo de emojis, se pueden subir imágenes PNG para representar tipos de árbol
- **Formulario de plantación** con:
  - Selección de ubicación en un mini-mapa
  - Especies y cantidades, cada una con su propio ícono
  - Historial de mantenimiento (al editar) y alerta configurable para el próximo mantenimiento
- **Ficha pública por QR**: cada plantación tiene una vista de solo lectura accesible escaneando su código QR.

## Cómo usarlo

No requiere instalación. Basta con abrir `index.html` en un navegador, o servirlo con cualquier servidor estático:

```bash
npx serve .
# o
python3 -m http.server
```

### Publicarlo con GitHub Pages

1. Sube este repositorio a GitHub.
2. Ve a **Settings → Pages**.
3. En "Source", selecciona la rama `main` y la carpeta `/ (root)`.
4. Guarda. GitHub publicará el sitio en `https://<tu-usuario>.github.io/<nombre-del-repo>/`.

## Almacenamiento de datos

Los datos (plantaciones e íconos personalizados) se guardan mediante la API de almacenamiento persistente del entorno donde corre la app (`window.storage`). Si se despliega fuera de ese entorno (por ejemplo, en GitHub Pages), esta API no estará disponible y será necesario reemplazar `loadSites`/`saveSites`/`loadCustomIcons`/`saveCustomIcons` por otro mecanismo de persistencia (por ejemplo, `localStorage`, o un backend propio).

## Tecnologías

- [Leaflet](https://leafletjs.com/) para el mapa
- [Chart.js](https://www.chartjs.org/) para las gráficas
- [qrcode.js](https://github.com/davidshimjs/qrcodejs) para generar los códigos QR
- Sin frameworks de frontend: HTML, CSS y JavaScript nativo
