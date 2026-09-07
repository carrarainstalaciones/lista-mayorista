# Lista mayorista Carrara - Septiembre 2026

Archivos principales:

- `index.html`: lista HTML para navegador e impresión en A4 apaisado.
- `Lista de Precio MAYORISTA - Base de Datos.xls`: única fuente externa para actualizar precios automáticamente.
- `datos-carrara.json`: datos estructurados de referencia del catálogo; no se utiliza para actualizar precios automáticamente.

Flujo de actualización:

1. Trabajar siempre sobre esta misma carpeta y mantener el HTML y el Excel juntos.
2. Cada mes, reemplazar `Lista de Precio MAYORISTA - Base de Datos.xls` conservando nombre y estructura.
3. Abrir o recargar el HTML desde hosting o servidor local. Lee el Excel automáticamente, sin usar la caché.
4. El cruce es por SKU: columna A (`Código`), columna K (`Precio de Venta($)`, neto) y columna L (`Precio De Venta Con IVA($)`, final con IVA).
5. Revisar el estado de lectura de precios antes de imprimir o exportar a PDF.

Se eliminó el botón de actualización manual y el CSV. No se buscan archivos alternativos XLSX o CSV.

Si se abre el HTML directamente como archivo local (`file://`), no se actualizan los precios desde el Excel: se muestran guiones (—) en lugar de precios y el estado indica que debe abrirse en hosting o servidor local. Si falla la lectura del Excel, se muestran guiones (—) y se informa el error.

Mantener imágenes, productos, secciones y diseño salvo pedido explícito.

El HTML no contiene importes de precios guardados. Los campos Neto y Final se completan únicamente al leer el Excel; los SKU sin coincidencia quedan con guiones. Guardar el Excel y recargar la página para ver los cambios.

## Git y publicación

Esta misma carpeta es el repositorio local. El remoto `origin` es https://github.com/carrarainstalaciones/lista-mayorista.git y la rama principal es `main`.

El HTML de trabajo es `index.html`. Mantener el Excel a su lado. Para publicar cambios, revisar `git diff`, agregar los archivos modificados con `git add`, crear un commit con `git commit` y subir con `git push -u origin main` la primera vez (luego `git push`). Git necesita autenticación con GitHub independiente de la sesión del navegador.

Cambiar el Excel local no actualiza la web hasta subirlo y completar el despliegue del hosting.
