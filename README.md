# Brand Factory 🏭

Automatización completa para creación de marcas usando n8n + Claude AI.

## 🔗 URLs

- **n8n Dashboard:** https://n8n-production-cf6d.up.railway.app
- **Webhook URL:** `POST https://n8n-production-cf6d.up.railway.app/webhook/brand-factory`
- **Credenciales:** junior@intechchain.com / JuniorClaw2026!

## 📥 Importar Workflow

1. Ir a n8n Dashboard
2. Click en "Add new item" → "Import from file"
3. Seleccionar `workflow.json`
4. Configurar credenciales de Anthropic (Claude API)
5. Activar el workflow

## 🎯 Campos del Brief (JSON Body)

```json
{
  "brand_name": "Nombre de la marca",
  "industry": "Industria/sector",
  "mission": "Misión de la empresa",
  "vision": "Visión a futuro",
  "target_audience": "Descripción del público objetivo",
  "competitors": "Competidores principales",
  "values": "Valores de la marca",
  "tone": "Tono de comunicación deseado",
  "differentiators": "Qué hace única a la marca",
  "budget": "Presupuesto aproximado",
  "timeline": "Timeline del proyecto"
}
```

## 🧪 Test con cURL

```bash
curl -X POST https://n8n-production-cf6d.up.railway.app/webhook/brand-factory \
  -H "Content-Type: application/json" \
  -d '{
    "brand_name": "Café Origen",
    "industry": "Cafetería especializada",
    "mission": "Conectar a las personas con el café de origen colombiano",
    "vision": "Ser referente de café de especialidad en LATAM",
    "target_audience": "Profesionales 25-45 años, amantes del café de calidad",
    "competitors": "Juan Valdez, Starbucks, cafeterías locales",
    "values": "Calidad, Sostenibilidad, Comunidad, Autenticidad",
    "tone": "Cálido, conocedor, accesible pero premium",
    "differentiators": "Café directo de fincas colombianas, trazabilidad completa",
    "budget": "$5,000 USD",
    "timeline": "2 meses"
  }'
```

## 📤 Output

El workflow genera un JSON con 3 secciones:

1. **strategy**: Posicionamiento, voz de marca, buyer personas, keywords
2. **visual_identity**: Paleta de colores, tipografía, estilo visual, prompts para logo
3. **digital_strategy**: Plataformas, pilares de contenido, calendario 30 días, hashtags, KPIs

## 🔧 Personalización

### Agregar generación de imágenes

Después del nodo de Visual Identity, agregar:
- **Nodo HTTP Request** → DALL-E 3 API
- **Nodo HTTP Request** → Midjourney API (si tienes acceso)

### Guardar en Google Drive

Agregar nodo **Google Drive** después de Consolidate Results para guardar el JSON como documento.

### Notificación por email

Agregar nodo **Gmail** o **SMTP** para enviar el resultado al cliente.

## 📋 Formulario Tally (pendiente)

Para crear el formulario en Tally:
1. Ir a https://tally.so
2. Crear nuevo formulario con los campos del brief
3. En integraciones, agregar webhook: `https://n8n-production-cf6d.up.railway.app/webhook/brand-factory`

---

*Creado por Junior Claw para IntechChain* 🦞
