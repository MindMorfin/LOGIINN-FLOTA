# Control de flotilla LOGIINN — paquete para publicar

Aplicación web instalable (PWA). Una vez publicada, se abre desde el navegador
del celular y se agrega a la pantalla de inicio: queda con icono propio, abre a
pantalla completa y funciona sin internet.

## Contenido

| Archivo | Para qué sirve |
|---|---|
| `index.html` | La aplicación completa (interfaz, lógica y tutorial). |
| `manifest.json` | Nombre, colores e iconos con los que se instala. |
| `sw.js` | Permite que abra sin conexión. |
| `` | Iconos de la app en los tamaños que piden Android y iPhone. |

Los datos se guardan en el `localStorage` del propio teléfono. No se envía nada
a ningún servidor.

## Publicarla (opción recomendada: Netlify Drop, sin cuenta ni configuración)

1. Comprime esta carpeta o tenla lista en el escritorio.
2. Entra a https://app.netlify.com/drop
3. Arrastra la carpeta completa (no el zip abierto, la carpeta con los cuatro
   elementos de arriba).
4. Te devuelve una liga tipo `https://algo-al-azar.netlify.app`. Esa es la app.
5. Si haces cuenta gratuita puedes renombrarla a algo como
   `flotilla-loginn.netlify.app` o conectarle un dominio propio.

**Importante:** tiene que ser una liga `https://`. Abrir el `index.html` con
doble clic desde el escritorio funciona, pero ahí no se instala como app ni
trabaja sin conexión.

### Alternativas

- **GitHub Pages:** sube los archivos a un repositorio, entra a Settings →
  Pages y selecciona la rama `main`, carpeta raíz.
- **Vercel:** https://vercel.com → Add New → Project → arrastra la carpeta.

## Instalarla en los teléfonos

**Android (Chrome):** abre la liga → menú de tres puntos → *Instalar aplicación*
o *Agregar a pantalla principal*.

**iPhone (Safari, tiene que ser Safari):** abre la liga → botón de compartir →
*Agregar a pantalla de inicio*.

Después se abre desde el icono como cualquier otra app.

## Actualizarla después

Cuando cambies `index.html`, abre `sw.js` y sube el número de versión
(`flotilla-v1` → `flotilla-v2`). Vuelve a publicar. Los teléfonos toman la
versión nueva la siguiente vez que la abran con internet; sin ese cambio se
pueden quedar con la copia vieja en caché.

## Si más adelante la quieren como APK

El mismo paquete se envuelve con https://www.pwabuilder.com (pegas la liga y te
genera el instalador para Google Play) o con Capacitor. No hay que reescribir
nada.

## Lo que sigue, cuando lo necesiten

- **Datos compartidos:** hoy cada teléfono tiene su propia lista. Para que
  tráfico y gerencia vean el mismo tablero hace falta una base de datos en línea
  (Supabase o Firebase alcanzan de sobra y son gratis a esta escala).
- **Enviar el reporte:** un botón para mandarlo por WhatsApp o exportarlo a PDF.
- **Historial:** guardar el corte de cada día para consultar días anteriores.
