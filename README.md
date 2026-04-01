# cut.studio

Editor de video con IA para creadores de contenido.

## Módulos
- **Fase 1** — Editor de video: cortes, texto, timeline
- **Fase 2** — Limpieza de audio: eliminar ruido con Web Audio API
- **Fase 3** — IA: subtítulos automáticos, guiones, voiceover
- **Fase 4** — Reel Engine: generador automático con beat sync
- **Fase 5** — PWA instalable en iPhone y Android

## Deploy en Netlify

1. Conectar repo en netlify.com → New site from Git
2. Build settings: dejar vacíos (publish dir = `.`)
3. Variables de entorno:
   - `ANTHROPIC_API_KEY` = tu key de Anthropic

## Desarrollo local

Necesitas Netlify CLI para probar las Functions localmente:

```bash
npm install -g netlify-cli
netlify dev
```

Abre http://localhost:8888

## Llamar a Claude desde el frontend

```javascript
const response = await fetch('/.netlify/functions/claude', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    messages: [{ role: 'user', content: 'Tu prompt aquí' }],
    system: 'Instrucciones del sistema',
    max_tokens: 1024,
  }),
});
const data = await response.json();
const texto = data.content[0].text;
```

## Por De la Garza Studio
