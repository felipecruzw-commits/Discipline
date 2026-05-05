# Discipline · Habit Tracker

App personal de seguimiento de hábitos diarios. Diseñada para uso individual en móvil, totalmente local (tus datos se guardan en tu dispositivo, no se envían a ningún servidor).

## Hábitos incluidos (lunes a viernes)

- Hacer la cama
- Tomar creatina
- Ir al gym
- No malicia (autocontrol)
- Leer 10 páginas
- Llamar a un amigo
- Tomar 2L de agua
- Pasos (meta: 7.000+)
- Instagram (máx: 150 min / 2.5h)
- Frase motivadora

## Características

- **Vista Hoy** — checkboxes y campos numéricos con progreso del día
- **Vista Semana** — strip de lunes a domingo, días perfectos, % por hábito
- **Estadísticas** — Semana / Mes / Total con comparación vs período anterior
- **Mapa de calor** — visualización de hábito × día
- **Archivo de frases** — todas las frases guardadas con fecha
- **Rachas** — racha global y por hábito individual
- **Fines de semana off** — no penaliza, solo descanso
- **Export/Import JSON** — backup manual de tus datos
- **PWA instalable** — se comporta como app nativa al añadirla a la pantalla de inicio

## Cómo desplegarla en tu teléfono

### Opción 1 — GitHub Pages (recomendada, repo privado)

1. Crea un repositorio **privado** en GitHub.
2. Sube `index.html` y `manifest.webmanifest`.
3. **Settings → Pages → Source: `main` branch / root**.
4. GitHub te dará una URL tipo `https://tu-usuario.github.io/discipline/`.
5. En tu teléfono, abre esa URL en Safari (iOS) o Chrome (Android).
6. **iOS:** botón compartir → "Añadir a pantalla de inicio".
   **Android:** menú ⋮ → "Instalar aplicación" / "Añadir a pantalla principal".

> Nota: GitHub Pages funciona en repos privados solo si tienes una cuenta Pro (o GitHub Free con repos públicos). Si tu cuenta es Free, alternativas privadas están abajo.

### Opción 2 — Netlify (gratis, soporta repos privados)

1. Crea cuenta en netlify.com (gratis).
2. "Add new site" → conecta tu repo privado de GitHub.
3. Build settings: dejar todo vacío. Publish directory: `/` (raíz).
4. Deploy. Te da una URL `*.netlify.app`.
5. (Opcional) Settings → Access control → Password protection.

### Opción 3 — Cloudflare Pages (gratis, repos privados)

1. dash.cloudflare.com → Pages → Create project → Connect Git.
2. Build command: vacío. Build output directory: `/`.
3. Deploy.

### Opción 4 — Sin hosting (uso local)

Abre `index.html` directamente en el navegador del móvil tras transferirlo. Funciona, pero perderás la opción "instalar como app" en algunos navegadores.

## Backup de datos

Los datos viven en `localStorage` del navegador. **Si borras los datos del navegador, pierdes el historial.** Por eso:

- Usa **Exportar JSON** desde la pestaña Stats cada cierto tiempo (semanal o mensual).
- Guarda el `.json` en Drive, iCloud, o donde prefieras.
- Para restaurar: **Importar** desde la misma pestaña.

## Personalizar hábitos

Si quieres añadir / quitar / modificar hábitos, edita el array `HABITS` al inicio del `<script>` en `index.html`. Tipos disponibles:

```js
{ id: 'mi_id', label: 'Mi hábito', type: 'check' }
{ id: 'agua', label: 'Vasos de agua', type: 'numeric', unit: 'vasos', goal: 8, cmp: '>=' }
{ id: 'redes', label: 'TikTok', type: 'numeric', unit: 'min', goal: 60, cmp: '<=' }
{ id: 'frase', label: 'Frase motivadora', type: 'quote' }
```

`cmp: '>='` significa "completado si el valor es mayor o igual a la meta".
`cmp: '<='` significa "completado si el valor es menor o igual al límite".

## Privacidad

- 100% client-side. Nada sale de tu dispositivo.
- Sin tracking, sin analytics, sin servidores externos (excepto Google Fonts para tipografía).
- Si quieres bloquear incluso eso, descarga las fuentes Fraunces y JetBrains Mono y sírvelas localmente.
