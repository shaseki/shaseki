# SHASEKI // `shaseki.pro`

![Status](https://img.shields.io/badge/STATUS-ONLINE-DCDAD0?style=flat-square&labelColor=000000)
![Architecture](https://img.shields.io/badge/ARCHITECTURE-ZERO__BLOAT_VANILLA-DCDAD0?style=flat-square&labelColor=000000)
![UI Paradigm](https://img.shields.io/badge/UI-WAYLAND__TILING-DCDAD0?style=flat-square&labelColor=000000)
![Automation](https://img.shields.io/badge/STACK-N8N_%2B_LLM_AGENTS-DCDAD0?style=flat-square&labelColor=000000)
![Location](https://img.shields.io/badge/BASE-PATAGONIA_AR-737373?style=flat-square&labelColor=000000)

Repositorio oficial del frontend y sistema de diseño de **SHASEKI** (*"Piedra Oblicua"*), estudio de **ingeniería creativa, producción audiovisual generativa y automatización con agentes IA** con base en la Patagonia Argentina.

---

## 01 // Filosofía e Ingeniería

`shaseki.pro` está diseñado bajo una premisa estricta: **máximo impacto visual y precisión técnica con cero sobreingeniería**. En lugar de depender de *bundlers* pesados o frameworks innecesarios para una landing de conversión y portfolio, toda la aplicación corre sobre un único documento HTML semántico, CSS moderno con *Custom Properties* y JavaScript nativo.

* **Zero-Build / Carga Instantánea:** Sin tiempos de compilación, sin hidratación pesada y con rendimiento óptimo tanto en desktop como en dispositivos móviles.
* **Estética Wayland Tiling (Hyprland / Omarchy):** Interfaz 2D estrictamente plana que traslada la lógica de los gestores de ventanas en mosaico (*tiling window managers*) y barras de estado (`waybar` + `tmux`) al navegador.
* **Design System Machine-Readable:** Toda la identidad está codificada en tokens exactos para garantizar consistencia matemática tanto en código frontend como al operar con LLMs.

---

## 02 // Arquitectura de Interfaz y Navegación Híbrida

El motor de navegación resuelve el problema clásico de usabilidad del scroll horizontal mediante un enfoque **adaptativo por viewport**:

```text
┌─────────────────────────────────────────────────────────────────────────┐
│ WAYBAR (38px) // SHASEKI │ [01:INICIO] ... [05:CONTACTO] │ [GRAIN] 00%  │
├──────────────────────────────────────────────────────────────┬──────────┤
│                                                              │          │
│              WORKSPACE ACTIVO (92vw en Desktop)              │  PEEK    │
│           [ Tile A ]                  [ Tile B ]             │ (8vw)    │
│                                                              │ SIGUIENTE│
│                                                              │          │
├──────────────────────────────────────────────────────────────┴──────────┤
│ TMUX BAR (38px) // [← ANTERIOR]  │ 01/05 ■ □ □ □ □ │ [SIGUIENTE: ... →] │
└─────────────────────────────────────────────────────────────────────────┘
```

### Comportamiento por Dispositivo
| Viewport | Modo de Navegación | Características Técnicas |
| :--- | :--- | :--- |
| **Desktop (`>= 1024px`)** | **Horizontal Tiling + Peek** | Workspaces de `92vw` (el siguiente asoma a la derecha a `opacity: 0.42` y es clickeable), `scroll-snap-type: x proximity`, mapeo directo de rueda vertical a eje X sin bloqueos internos, arrastre (*click-and-drag*), atajos `← / →` y barra inferior `tmux` con destinos explícitos. |
| **Mobile (`< 1024px`)** | **Vertical Nativo** | Fallback automático a columna vertical con scroll táctil nativo (`-webkit-overflow-scrolling: touch`), manteniendo sincronizada la barra superior y el indicador porcentual de avance. |

### Componentes Interactivos Integrados
* **Visor en Vivo + Simulador de Pipeline n8n (`[02:AGENTE_WA]`):** Ventana con pestañas internas aisladas que combina un `<iframe>` del proyecto en producción (`AI-Automation-Final`) y una simulación paso a paso del flujo de ingesta de clientes (`WEBHOOK_WHATSAPP → AI_AGENT_NODE → CRM_JSON_SYNC → AUTO_REPLY_WA`) con salida JSON en tiempo real.
* **Overlay de Grano Analógico (`#grain-overlay`):** Filtro SVG procedural `<feTurbulence type="fractalNoise">` en escala de grises al `4%` de opacidad, activable/desactivable desde la Waybar (`[GRAIN: ON/OFF]`).
* **Terminal Intake (`[05:CONTACTO]`):** Formulario estructurado listo para conectarse directamente a un **Webhook de n8n** y disparar respuestas automáticas en WhatsApp/Telegram.

---

## 03 // Design System (Tokens)

El sistema de diseño prohíbe explícitamente sombras (`box-shadow: none`), gradientes decorativos y esquinas redondeadas (`border-radius: 0px`), reemplazándolas por **chaflanes oblicuos a 45°** generados vía `clip-path`.

| Categoría | Token CSS | Valor | Uso |
| :--- | :--- | :--- | :--- |
| **Fondo Base** | `--bg-primary` | `#000000` | Lienzo principal, barras de sistema y placas. |
| **Superficie** | `--bg-surface` | `#0B0B0B` | Contenedores `.tile` y ventanas. |
| **Tinta Principal** | `--fg-primary` | `#DCDAD0` | *Bone White* — Tipografía principal, bordes activos e inversión en hover. |
| **Tinta Secundaria** | `--fg-muted` | `#737373` | Metadatos técnicos, descripciones y estados inactivos. |
| **Borde Técnico** | `--border-subtle` | `#222222` | Líneas divisorias estructurales de `1px`. |
| **Display** | `--font-display` | `Unbounded` (`700–900`) | Marca y titulares en `UPPERCASE`. |
| **UI / Técnica** | `--font-mono` | `JetBrains Mono` (`400–500`) | Navegación, botones, logs JSON y metadatos. |
| **Geometría** | `--chamfer-sm / md` | `10px / 16px` (`45°`) | Cortes oblicuos en botones primarios y paneles de confirmación. |

---

## 04 // Ecosistema y Proyectos Integrados

| Código | Proyecto | Stack / Disciplina | Acceso |
| :--- | :--- | :--- | :--- |
| **`SHK-001`** | **KOPROLITOS** | Stop-motion, Hydra live-coding, composición 2.5D & Web | [shaseki.github.io/koprolitos](https://shaseki.github.io/koprolitos/) |
| **`SHK-002`** | **AI-AUTOMATION-FINAL** | Orquestación n8n, agentes IA & dashboard operativo | [shaseki.github.io/AI-Automation-Final](https://shaseki.github.io/AI-Automation-Final/) |
| **`SHK-003`** | **ESCALERA CIRCULAR** | Co-producción audiovisual & identidad visual | *En archivo* |
| **`SHK-004`** | **LIVE VISUAL SYSTEMS** | Motion de gran formato & visuales generativos en vivo | *En archivo* |

---

## 05 // Estructura del Repositorio

```text
shaseki.pro/
├── index.html                  # Aplicación completa autocontenida
├── logo.png                    # Lockup vertical máster (WIN_01)
├── favicon.ico                 # Favicon multi-resolución
├── favicon-16x16.png
├── favicon-32x32.png
├── apple-touch-icon.png        # iOS home screen (180x180)
├── android-chrome-192x192.png  # Android / PWA
├── android-chrome-512x512.png
├── design-system/              # (Opcional) Fuente de verdad para LLMs
│   ├── BRAND_RULES.md
│   ├── tokens.css
│   └── tokens.json
└── README.md
```

---

## 06 // Despliegue Local y Producción

### Desarrollo Local
Al no requerir compilación ni dependencias de `node_modules`, podés levantar un servidor estático inmediato desde la raíz del proyecto:

```bash
# Con Python 3
python3 -m http.server 8080

# O con Node / npx
npx serve .
```

Abrir `http://localhost:8080` en el navegador.

### Producción (GitHub Pages + Dominio Personalizado)
1. Subir los archivos a la rama `main` del repositorio.
2. En **Settings → Pages**, configurar el origen en `Deploy from a branch` (`main` / `/root`).
3. Añadir un archivo `CNAME` en la raíz con el dominio `shaseki.pro` y apuntar los registros DNS (`A` / `CNAME`) hacia GitHub Pages con HTTPS forzado.

### Integración con Webhook de n8n (Próximo Paso)
Para conectar el formulario `#deploy-form` (`WIN_09`) con un flujo real en tu servidor self-hosted de **n8n**, reemplazá el handler de `submit` por un `fetch()` `POST` hacia tu endpoint de producción:

```javascript
await fetch('https://n8n.shaseki.pro/webhook/client-intake', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify(receipt)
});
```

---

## 07 // Entorno y Contacto

* **Entorno de producción:** Arch Linux (*Omarchy*), Inkscape, Figma, n8n self-hosted, Blender & Hydra.
* **Contacto directo:** [hola@shaseki.pro](mailto:hola@shaseki.pro)
* **Base:** Trelew, Chubut — Patagonia Argentina // Operación remota global.
