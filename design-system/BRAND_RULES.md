# SHASEKI — Design System & Brand Rules (LLM Context)

Este documento es la única fuente de verdad visual para **SHASEKI** ("Piedra Oblicua"), sello audiovisual y estudio de diseño generativo. Cualquier pieza gráfica, prompt o componente web generado para `shaseki.pro` debe cumplir estrictamente con estas reglas.

## 1. Concepto y Estética
- **Estética:** Minimalismo brutalista e industrial. Alto contraste, 2D plano, rigor geométrico.
- **Tono visual:** Silencioso, arquitectónico, técnico y de culto. El espacio negativo (aire negro) es un elemento activo de composición, nunca un vacío que haya que rellenar.

## 2. Principio Geométrico ("El Corte Oblicuo")
- **Ángulo maestro:** `45°`. Tanto el tajo diagonal central del isotipo como los chaflanes exteriores opuestos (superior izquierdo e inferior derecho) responden a una lógica de corte seco a 45°.
- **Bordes:** `border-radius: 0px` en todo el sistema.
- **Recurso de forma en UI:** Cuando un contenedor o botón requiera carácter de marca, usar chaflanes a 45° mediante `clip-path`, nunca esquinas redondeadas.

## 3. Paleta de Color (Estrictamente Monocromática)
- **Fondo Principal (`--bg-primary`):** `#000000` (Negro absoluto).
- **Superficie Secundaria (`--bg-surface`):** `#0B0B0B` (Solo para diferenciar bloques o cards sin usar sombras).
- **Tinta Principal (`--fg-primary`):** `#DCDAD0` (Bone White). Evitar `#FFFFFF` puro en grandes masas.
- **Tinta Secundaria (`--fg-muted`):** `#737373` (Metadatos, años, códigos de archivo).
- **Bordes Técnicos (`--border-subtle`):** `#222222` (Líneas divisorias de `1px`).
- **Bordes Activos (`--border-strong`):** `#DCDAD0` (Bone White).

## 4. Sistema Tipográfico
- **Display / Marca:** `Unbounded` (pesos `700` y `800`).
  - Uso: Logotipo, títulos principales (`h1`, `h2`) y placas de video.
  - Regla: Siempre en `UPPERCASE`, `line-height` ajustado (`0.95` a `1.05`).
- **UI / Técnica / Metadatos:** `JetBrains Mono` (pesos `400` y `500`).
  - Uso: Navegación, botones, créditos, códigos de proyecto (`SHK-001`), fechas y pies de foto.
- **Cuerpo de texto largo (solo si es necesario):** `Space Grotesk` o `Inter` en `16px` (`line-height: 1.6`).

## 5. Activos Oficiales (Lockups)
1. **Isotipo solo (`shaseki-iso.svg`):** Dos bloques planos separados por el tajo diagonal. Uso en favicons, avatares (con al menos 20-25% de margen negro) y headers web.
2. **Lockup vertical (`shaseki-vertical.svg`):** Isotipo arriba + `SHA` / `SEKI` apilados en dos líneas abajo. Ambas líneas mantienen exactamente la misma escala y peso de trazo (compensando el ancho con *tracking* en `SHA`, nunca comprimiendo `SEKI`).
3. **Wordmark horizontal (`shaseki-wordmark.svg`):** `SHASEKI` en una sola línea en `Unbounded`.

## 6. Anti-Patterns (PROHIBICIONES ESTRICTAS)
Un LLM o diseñador tiene estrictamente prohibido:
- Usar sombras paralelas (`box-shadow`), brillos (`glow`) o efectos 3D en la identidad base.
- Usar gradientes de color.
- Usar esquinas redondeadas (`border-radius > 0`).
- Estirar o comprimir horizontalmente la tipografía `Unbounded`.
- Usar animaciones elásticas o con rebote (*bounce*, *spring*).
- Decorar con íconos genéricos de librerías estándar (usar texto técnico o flechas vectoriales mínimas).

## 7. Motion y Comportamiento (Web & Video)
- **Curva de animación:** Seca y precisa (`cubic-bezier(0.16, 1, 0.3, 1)` o lineal).
- **Duración UI:** Rápida (`150ms` a `250ms`). En `hover` de botones, inversión instantánea de color (fondo `#DCDAD0`, texto `#000000`).
- **Grano analógico (Opcional):** Textura de ruido sutil al `3% - 5%` de opacidad sobre el fondo negro para unificar la estética de placas de video con la web.
