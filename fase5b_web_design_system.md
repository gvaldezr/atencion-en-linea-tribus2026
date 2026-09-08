# Fase 5b — Web Design System
# *"La Línea Invisible"* — Scroll-Driven Storytelling

> **Versión**: 1.0 | **Fecha**: Septiembre 2026  
> **Proyecto**: Pitch web publicable — Semana de Innovación, Anáhuac Mayab  
> **Uso**: Blueprint para implementación HTML/CSS/JS estático  
> **Skills aplicados**: `color-system`, `type-system`, `design-screen`, `responsive-audit`, `tokenize`, `scroll-animation`, `design-interaction`

---

## Tabla de Contenidos

1. [Design Tokens](#1-design-tokens)
2. [Estructura de Secciones](#2-estructura-de-secciones)
3. [Componentes](#3-componentes)
4. [Guía de Animaciones / Transiciones](#4-guía-de-animaciones--transiciones)
5. [Responsive Breakpoints](#5-responsive-breakpoints)
6. [Mapa de Contenido](#6-mapa-de-contenido)
7. [CSS Custom Properties](#7-css-custom-properties)
8. [Guía de Implementación](#8-guía-de-implementación)
9. [Assets Requeridos](#9-assets-requeridos)

---

## 1. Design Tokens

### 1.1 Paleta de Color — "Dark Immersive"

Esta experiencia web invierte la proporción del brand book estándar de Anáhuac: aquí el fondo oscuro domina (60%) y el naranja es protagonista dramático (15%). Esto crea el mood cinematográfico que el guión coral requiere.

#### Colores Primarios

| Token | Hex | Uso |
|-------|-----|-----|
| `--li-bg-primary` | `#0D0D0D` | Fondo principal del body |
| `--li-bg-section` | `#1A1A1A` | Fondo de secciones alternas |
| `--li-bg-elevated` | `#242424` | Cards, bloques elevados |
| `--li-bg-glass` | `rgba(26, 26, 26, 0.85)` | Superficies con backdrop-blur |
| `--li-accent` | `#FF5900` | Naranja institucional — acentos, datos, CTAs |
| `--li-accent-hover` | `#FF7900` | Hover del naranja (más claro, per brand book) |
| `--li-accent-glow` | `rgba(255, 89, 0, 0.15)` | Glow sutil detrás de stats |
| `--li-accent-gradient` | `linear-gradient(135deg, #FF5900, #FF7900)` | Gradiente para emphasis |
| `--li-purple` | `#432F64` | Púrpura institucional — acentos secundarios |

#### Colores de Texto

| Token | Hex | Uso |
|-------|-----|-----|
| `--li-text-primary` | `#F3F3F1` | Texto principal sobre fondo oscuro |
| `--li-text-secondary` | `#A0A0A0` | Texto secundario, subtítulos, captions |
| `--li-text-muted` | `#6F6F6F` | Labels, metadata, texto terciario |
| `--li-text-accent` | `#FF5900` | Texto naranja — nombres propios, datos clave |
| `--li-text-inverse` | `#0D0D0D` | Texto sobre fondo naranja |

#### Colores Funcionales

| Token | Hex | Uso |
|-------|-----|-----|
| `--li-divider` | `rgba(255, 255, 255, 0.08)` | Líneas divisoras sutiles |
| `--li-divider-accent` | `rgba(255, 89, 0, 0.3)` | Líneas de acento naranja |
| `--li-overlay-dark` | `rgba(0, 0, 0, 0.6)` | Overlay sobre imágenes |
| `--li-overlay-gradient` | `linear-gradient(to bottom, transparent, #0D0D0D)` | Fade de imagen a fondo |

#### Proporción de Color

| Proporción | Elemento | Color |
|-----------|----------|-------|
| **60%** | Fondos oscuros | `#0D0D0D`, `#1A1A1A`, `#242424` |
| **20%** | Texto claro | `#F3F3F1`, `#A0A0A0` |
| **15%** | Acentos naranja | `#FF5900` (datos, líneas, highlights) |
| **5%** | Negro puro + púrpura | `#000000`, `#432F64` |

### 1.2 Tipografía

La experiencia web usa fuentes de Google Fonts para zero-dependency deployment.

#### Font Stack

```html
<link href="https://fonts.googleapis.com/css2?family=Manrope:wght@300;400;500;600;700;800&display=swap" rel="stylesheet">
```

**Manrope** como fuente única (alternativa oficial aprobada en brand book cuando Sharp-Bold no está disponible). Razón: geométrica, limpia, excelente en tamaños grandes, excelente rendering en pantalla.

#### Escala Tipográfica

| Token | Tamaño | Peso | Line-Height | Uso |
|-------|--------|------|-------------|-----|
| `--li-font-hero` | `clamp(3.5rem, 8vw, 7rem)` | 800 | 1.0 | Números gigantes de stats (6,000; 150) |
| `--li-font-display` | `clamp(2.5rem, 5vw, 4.5rem)` | 800 | 1.1 | Títulos de acto |
| `--li-font-headline` | `clamp(1.75rem, 3.5vw, 2.5rem)` | 700 | 1.2 | Frases de impacto |
| `--li-font-subhead` | `clamp(1.25rem, 2vw, 1.5rem)` | 600 | 1.3 | Subtítulos de sección |
| `--li-font-body` | `clamp(1rem, 1.2vw, 1.25rem)` | 400 | 1.7 | Párrafos narrativos |
| `--li-font-body-lg` | `clamp(1.125rem, 1.5vw, 1.375rem)` | 400 | 1.6 | Citas textuales del guión |
| `--li-font-caption` | `0.875rem` | 300 | 1.5 | Labels, fechas, metadata |
| `--li-font-overline` | `0.75rem` | 700 | 1.2 | Overlines (ACTO I, ACTO II...) — tracking: 0.15em, uppercase |

#### Regla Tipográfica Clave

> Los **números dramáticos** (6,000 · 150 · 300 · 2,000 · 60) siempre usan `--li-font-hero` en color `--li-accent` (#FF5900). Son el elemento visual más grande de cada sección donde aparecen.

### 1.3 Spacing

Escala basada en 8px con extensiones para secciones de storytelling.

| Token | Valor | Uso |
|-------|-------|-----|
| `--li-space-xs` | `4px` | Separación mínima |
| `--li-space-sm` | `8px` | Gap entre chips, padding compacto |
| `--li-space-md` | `16px` | Padding estándar |
| `--li-space-lg` | `24px` | Padding de componentes |
| `--li-space-xl` | `32px` | Gap entre elementos de sección |
| `--li-space-2xl` | `48px` | Separación entre bloques |
| `--li-space-3xl` | `64px` | Padding vertical de sección (mobile) |
| `--li-space-4xl` | `96px` | Padding vertical de sección (tablet) |
| `--li-space-5xl` | `128px` | Padding vertical de sección (desktop) |
| `--li-space-6xl` | `160px` | Espacio entre actos (breathing room) |

### 1.4 Sombras y Efectos

| Token | Valor | Uso |
|-------|-------|-----|
| `--li-shadow-sm` | `0 2px 8px rgba(0, 0, 0, 0.3)` | Cards sutiles |
| `--li-shadow-md` | `0 8px 32px rgba(0, 0, 0, 0.4)` | Cards elevadas |
| `--li-shadow-glow` | `0 0 60px rgba(255, 89, 0, 0.15)` | Glow naranja detrás de stats |
| `--li-shadow-text` | `0 2px 40px rgba(0, 0, 0, 0.5)` | Sombra en texto sobre imagen |
| `--li-blur-glass` | `blur(20px)` | Backdrop-filter para superficies glass |

### 1.5 Bordes y Radios

| Token | Valor | Uso |
|-------|-------|-----|
| `--li-radius-sm` | `8px` | Chips, badges |
| `--li-radius-md` | `12px` | Cards pequeñas |
| `--li-radius-lg` | `16px` | Cards grandes, bloques |
| `--li-radius-xl` | `24px` | Contenedores hero |
| `--li-radius-full` | `9999px` | Píldoras, indicadores |
| `--li-border-subtle` | `1px solid rgba(255, 255, 255, 0.08)` | Bordes casi invisibles |
| `--li-border-accent` | `1px solid rgba(255, 89, 0, 0.3)` | Bordes con acento |
| `--li-border-accent-strong` | `2px solid #FF5900` | Bordes de énfasis |

---

## 2. Estructura de Secciones

La experiencia web es un **scroll-driven longform** dividido en 5 secciones (actos) + header + footer. Cada sección ocupa mínimo `100vh` y tiene su propia identidad visual dentro del sistema.

### 2.1 Mapa de Secciones

```
┌─────────────────────────────────────────────────┐
│  HEADER — Navegación flotante + Logo            │ ← fixed, aparece después de hero
├─────────────────────────────────────────────────┤
│                                                  │
│  HERO — Apertura cinemática                     │ ← 100vh, fullscreen
│  "La Línea Invisible"                           │
│                                                  │
├─────────────────────────────────────────────────┤
│                                                  │
│  ACTO I — "El Mundo Conocido"                   │ ← min 100vh, bg: #0D0D0D
│  Marzo 2020. Campus en silencio.                │    Mood: sombrío, B/N
│  Stat: 6,000 alumnos                            │
│                                                  │
├─────────────────────────────────────────────────┤
│                                                  │
│  ACTO II — "El Caos"                            │ ← min 100vh, bg: #0D0D0D → #1A1A1A
│  WhatsApp personal. Sin protocolo.              │    Mood: urgencia, tensión
│  Stats: 150 conversaciones · 11 PM              │
│                                                  │
├─────────────────────────────────────────────────┤
│                                                  │
│  ACTO III — "El Pacto"                          │ ← min 150vh, bg: #1A1A1A
│  Timeline: Sep 2020 → Dic 2020 → 2022 → 2024  │    Mood: construir, crecer
│  Hitos + Efecto dominó + GLPI nacional          │    Color naranja empieza a dominar
│                                                  │
├─────────────────────────────────────────────────┤
│                                                  │
│  ACTO IV — "El Ecosistema"                      │ ← min 150vh, bg: #1A1A1A → #0D0D0D
│  Diagrama ecosistema · Stats en cascada         │    Mood: poder, acumulación
│  Contraste antes/después                        │    Máximo impacto visual
│                                                  │
├─────────────────────────────────────────────────┤
│                                                  │
│  ACTO V — "El Legado"                           │ ← min 100vh, bg: #0D0D0D
│  Reconocimiento · Frase de cierre               │    Mood: solemne, cálido
│  "60 personas que eligieron no soltar"          │    Naranja cálido + tipografía grande
│                                                  │
├─────────────────────────────────────────────────┤
│                                                  │
│  FOOTER — Créditos + Logo Anáhuac Mayab         │ ← bg: #000000
│  "La Línea Invisible · 6 años"                 │
│                                                  │
└─────────────────────────────────────────────────┘
```

### 2.2 Detalle por Sección

#### HERO (Preámbulo)

| Propiedad | Valor |
|-----------|-------|
| **Altura** | `100vh` exacto |
| **Fondo** | Imagen desaturada del campus + overlay gradient oscuro |
| **Layout** | Centrado vertical y horizontal |
| **Contenido** | Título "La Línea Invisible" + subtítulo + indicador scroll |
| **Animación** | Título aparece con fade + slide up. Indicador scroll pulsa. |

#### ACTO I — El Mundo Conocido

| Propiedad | Valor |
|-----------|-------|
| **Altura** | `min-height: 100vh` |
| **Fondo** | `#0D0D0D` sólido |
| **Layout** | Texto centrado en columna estrecha (max 680px) |
| **Mood visual** | Penumbra, austeridad. Casi solo texto blanco sobre negro. |
| **Componentes** | `stat-hero` (6,000), `quote-block`, `dramatic-pause` (pantalla negra) |

#### ACTO II — El Caos

| Propiedad | Valor |
|-----------|-------|
| **Altura** | `min-height: 100vh` |
| **Fondo** | Gradiente de `#0D0D0D` a `#1A1A1A` |
| **Layout** | Columna narrativa (max 680px) + stat cards anchos |
| **Mood visual** | Tensión. El naranja empieza a aparecer en los datos. |
| **Componentes** | `stat-hero` (150), `icon-badge` (WhatsApp), `text-reveal`, `quote-block` |

#### ACTO III — El Pacto

| Propiedad | Valor |
|-----------|-------|
| **Altura** | `min-height: 150vh` (sección más larga) |
| **Fondo** | `#1A1A1A` |
| **Layout** | Timeline vertical + columna narrativa |
| **Mood visual** | Construcción, acumulación. El naranja crece progresivamente. |
| **Componentes** | `timeline`, `milestone-card`, `expansion-grid`, `map-mexico`, `stat-inline` |

#### ACTO IV — El Ecosistema

| Propiedad | Valor |
|-----------|-------|
| **Altura** | `min-height: 150vh` |
| **Fondo** | `#1A1A1A` transitando a `#0D0D0D` |
| **Layout** | Diagrama ecosistema full-width + stats cascada + antes/después split |
| **Mood visual** | Power. Máxima densidad de datos. Naranja en su máxima expresión. |
| **Componentes** | `ecosystem-diagram`, `stat-cascade`, `team-equation`, `before-after-split`, `differentiator-card` |

#### ACTO V — El Legado

| Propiedad | Valor |
|-----------|-------|
| **Altura** | `min-height: 100vh` |
| **Fondo** | `#0D0D0D` |
| **Layout** | Centrado, tipografía grande, máximo breathing room |
| **Mood visual** | Solemne, cálido. Volver a la simpleza. Solo texto y emoción. |
| **Componentes** | `team-mosaic`, `quote-monument`, `closing-phrase`, `final-title` |

---

## 3. Componentes

### 3.1 Catálogo de Componentes

#### `nav-floating` — Navegación Flotante

```
┌─────────────────────────────────────────────────────────┐
│  [Logo Anáhuac]    I · II · III · IV · V    [↑ Inicio]  │
└─────────────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Posición** | `position: fixed; top: 0` — aparece después de hacer scroll past hero |
| **Fondo** | `rgba(13, 13, 13, 0.9)` + `backdrop-filter: blur(20px)` |
| **Altura** | `64px` |
| **Border** | `border-bottom: 1px solid rgba(255,255,255,0.08)` |
| **Contenido** | Logo Anáhuac (variante blanca) a la izquierda. Números romanos de actos como navegación. Botón "volver arriba" a la derecha. |
| **Acto activo** | El número del acto visible lleva `color: #FF5900` y `border-bottom: 2px solid #FF5900` |
| **Transición** | `transform: translateY(-100%)` → `translateY(0)` al activarse |
| **z-index** | `1000` |
| **Mobile** | Colapsa a solo logo + indicador de acto actual |

#### `hero-fullscreen` — Hero de Apertura

```
┌─────────────────────────────────────────────────┐
│                                                  │
│         ░░░░ Imagen campus (desaturada) ░░░░    │
│         ░░░░ + overlay gradient oscuro  ░░░░    │
│                                                  │
│                                                  │
│            L A   L Í N E A                      │
│            I N V I S I B L E                    │
│                                                  │
│         Atención en Línea · Anáhuac Mayab       │
│            6 años · 60 personas                  │
│                                                  │
│                   ↓                              │
│              [scroll]                            │
│                                                  │
└─────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Altura** | `100vh` exacto |
| **Fondo** | Imagen desaturada del campus vacío (si existe) o gradiente `#000 → #1A1A1A` |
| **Overlay** | `linear-gradient(to bottom, rgba(0,0,0,0.4), rgba(0,0,0,0.8) 70%, #0D0D0D)` |
| **Título** | `font-size: --li-font-display`, `font-weight: 800`, `letter-spacing: 0.08em`, uppercase, color `#F3F3F1` |
| **Subtítulo** | `font-size: --li-font-subhead`, `font-weight: 400`, color `#A0A0A0` |
| **"Anáhuac Mayab"** | Siempre en `#FF5900` (regla del brand book) |
| **Indicador scroll** | Flecha animada con `animation: bounce 2s infinite` |
| **Parallax** | La imagen de fondo se mueve a `0.5x` velocidad del scroll |

#### `stat-hero` — Número Dramático

```
┌─────────────────────────────────────────────────┐
│                                                  │
│                                                  │
│                    6,000                         │  ← naranja, gigante
│                                                  │
│     alumnos que necesitaban respuestas           │  ← blanco, pequeño
│                                                  │
│                                                  │
└─────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Número** | `font-size: --li-font-hero` → `clamp(3.5rem, 8vw, 7rem)`, `font-weight: 800`, color `#FF5900` |
| **Subtexto** | `font-size: --li-font-body`, color `#A0A0A0`, max-width `480px`, centrado |
| **Layout** | Centrado vertical y horizontal, ocupa toda la viewport width |
| **Glow** | `text-shadow: 0 0 80px rgba(255, 89, 0, 0.2)` — glow sutil |
| **Fondo** | Radial gradient sutil: `radial-gradient(ellipse at center, rgba(255,89,0,0.05) 0%, transparent 70%)` |
| **Animación** | El número hace count-up desde 0 al entrar en viewport (IntersectionObserver). Duración: 1.5s, easing: ease-out. |
| **Spacing** | Padding vertical `--li-space-5xl` (128px) |

**Instancias en el sitio:**

| Número | Subtexto | Sección |
|--------|----------|---------|
| 6,000 | "alumnos que necesitaban respuestas" | Acto I |
| 150 | "conversaciones simultáneas · un solo agente" | Acto II |
| 300 | "atenciones cada día" | Acto IV |
| 2,000 | "en un solo día de carga académica" | Acto IV |
| 60+ | "personas en primera línea" | Acto IV |
| 15+ | "áreas articuladas" | Acto IV |
| 6 | "años de operación continua" | Acto IV |
| 400K+ | "interacciones procesadas" | Acto IV (complemento, del doc de producto) |

#### `quote-block` — Bloque de Cita

```
┌─────────────────────────────────────────────────┐
│                                                  │
│  ┃  "¿Qué pasa cuando seis mil personas         │
│  ┃   necesitan respuestas… y nadie sabe          │
│  ┃   por dónde empezar?"                         │
│                                                  │
└─────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Borde izquierdo** | `3px solid #FF5900` |
| **Padding** | `0 0 0 var(--li-space-lg)` |
| **Texto** | `font-size: --li-font-body-lg`, `font-style: italic`, color `#F3F3F1` |
| **Max-width** | `640px` |
| **Animación** | Fade-in desde la izquierda (`translateX(-20px)` → `0`) |

**Variante `quote-monument`** (para la frase de cierre del Acto V):

| Propiedad | Valor |
|-----------|-------|
| **Texto** | `font-size: --li-font-headline`, `font-weight: 700`, color `#F3F3F1` |
| **Sin borde** | Centrado, sin borde lateral |
| **Layout** | Centrado, max-width `800px`, padding vertical `--li-space-5xl` |
| **Highlight** | Las palabras clave ("alumno", "respuesta", "profesor", "emergencia") en `#FF5900` |
| **Animación** | Cada línea aparece secuencialmente con delay de 0.3s |

#### `timeline` — Línea del Tiempo

```
         Sep 2020                    Dic 2020                    2022                      2024
            ●━━━━━━━━━━━━━━━━━━━━━━━━━━●━━━━━━━━━━━━━━━━━━━━━━━━━━●━━━━━━━━━━━━━━━━━━━━━━━━━━●
            │                          │                          │                          │
     ┌──────┴──────┐           ┌───────┴───────┐          ┌───────┴───────┐          ┌───────┴───────┐
     │  Génesis     │           │   Pioneros    │          │  LeonEl Bot   │          │   Expansión   │
     │  CAA + DTI   │           │  WhatsApp API │          │  Efecto       │          │  +45 personas │
     │  6 agentes   │           │  Rocket.Chat  │          │  dominó       │          │  Operaciones  │
     └──────────────┘           └───────────────┘          └───────────────┘          └───────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Layout** | Horizontal en desktop (scroll horizontal si necesario), vertical en mobile |
| **Línea** | `2px solid #FF5900`, con gradiente de opacidad (empieza tenue, crece) |
| **Nodos** | Círculos `12px` con borde `2px solid #FF5900`, fondo `#0D0D0D`, `transition: scale` al hover |
| **Cards** | Fondo `#242424`, border `--li-border-subtle`, border-radius `--li-radius-md` |
| **Fecha** | `font-size: --li-font-overline`, color `#FF5900`, uppercase, tracking `0.15em` |
| **Título** | `font-size: --li-font-subhead`, `font-weight: 700`, color `#F3F3F1` |
| **Descripción** | `font-size: --li-font-body`, color `#A0A0A0` |
| **Animación** | Cada nodo y card aparecen secuencialmente al hacer scroll (stagger 0.15s) |

#### `milestone-card` — Tarjeta de Hito

```
┌───────────────────────────────┐
│  DICIEMBRE 2020               │  ← overline naranja
│                               │
│  Pioneros en México           │  ← título blanco
│                               │
│  Primera universidad en       │  ← descripción gris
│  conectar WhatsApp Business   │
│  a un sistema de atención     │
│  profesional.                 │
│                               │
│  🔗 Rocket.Chat · Twilio     │  ← tech badges
│     WhatsApp Business API     │
└───────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Fondo** | `#242424` |
| **Borde** | `1px solid rgba(255,255,255,0.08)` — cambia a `1px solid rgba(255,89,0,0.3)` en hover |
| **Border-radius** | `--li-radius-lg` (16px) |
| **Padding** | `--li-space-xl` (32px) |
| **Border-top** | `3px solid #FF5900` (acento superior) |
| **Animación** | Fade-in + slide up al entrar en viewport |

#### `expansion-grid` — Grid de Expansión (Efecto Dominó)

```
┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐
│  🎓    │ │  🔧    │ │  🚌    │ │  🛡️    │ │  ⚕️    │
│  Op.   │ │ Mant.  │ │Mayabus │ │Segur.  │ │ Salud  │
│ Académ │ │        │ │        │ │        │ │        │
└────────┘ └────────┘ └────────┘ └────────┘ └────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Layout** | `display: grid; grid-template-columns: repeat(auto-fit, minmax(120px, 1fr)); gap: 16px` |
| **Cards** | `padding: 24px; text-align: center; background: #242424; border-radius: 12px` |
| **Ícono** | `font-size: 2rem` (emoji o SVG) |
| **Label** | `font-size: --li-font-caption`, color `#A0A0A0` |
| **Animación** | Los items aparecen uno a uno con stagger de 0.1s (efecto dominó visual) |
| **Hover** | `border: 1px solid rgba(255,89,0,0.3); transform: translateY(-4px)` |

#### `ecosystem-diagram` — Diagrama del Ecosistema

```
┌─────────────────────────────────────────────────────────────┐
│                                                              │
│          ┌──────────┐                ┌──────────┐           │
│          │Rocket.Chat│──────────────│   GLPI    │           │
│          │  💬 Chat  │              │  📋 Tickets│           │
│          └─────┬─────┘              └─────┬─────┘           │
│                │                          │                  │
│                └────────┬─────────────────┘                  │
│                         │                                    │
│                    ┌────┴────┐                               │
│                    │  Vince  │                               │
│                    │ 🤖 IA   │                               │
│                    └────┬────┘                               │
│                         │                                    │
│                ┌────────┴────────┐                           │
│                │ Automatizaciones │                           │
│                │   ⚡ Conexiones  │                           │
│                └─────────────────┘                           │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Layout** | CSS Grid centrado, o SVG animado para las conexiones |
| **Nodos** | Cajas `#242424` con borde `--li-border-accent`, radius `--li-radius-lg`, padding `24px 32px` |
| **Ícono** | `font-size: 1.5rem`, centrado arriba del label |
| **Label** | `font-size: --li-font-subhead`, color `#F3F3F1` |
| **Conexiones** | Líneas SVG con `stroke: #FF5900; stroke-width: 2; stroke-dasharray: 4` animadas con `stroke-dashoffset` |
| **Animación** | Los nodos aparecen secuencialmente. Las líneas se "dibujan" con SVG stroke animation. |
| **Glow** | `box-shadow: 0 0 40px rgba(255,89,0,0.1)` en cada nodo |

#### `stat-cascade` — Stats en Cascada

```
┌─────────────────────────────────────────────────┐
│                                                  │
│    300          2,000        60+       15+       │
│   /día        en picos    personas    áreas     │
│                                                  │
└─────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Layout** | `display: grid; grid-template-columns: repeat(auto-fit, minmax(160px, 1fr)); gap: 32px` |
| **Número** | `font-size: clamp(2.5rem, 5vw, 4rem)`, `font-weight: 800`, color `#FF5900` |
| **Label** | `font-size: --li-font-caption`, color `#A0A0A0`, uppercase |
| **Divider** | Línea superior `2px solid rgba(255,89,0,0.3)` sobre cada stat |
| **Animación** | Count-up secuencial — cada stat empieza 0.3s después del anterior |
| **Container** | Max-width `900px`, centrado |

#### `team-equation` — Ecuación del Equipo

```
┌─────────────────────────────────────────────────┐
│                                                  │
│     6         10          45       =    +60      │
│    CAA     Helpdesk   Operaciones    personas    │
│                                                  │
└─────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Layout** | Flexbox horizontal, centrado, con signos `+` y `=` entre números |
| **Números** | `font-size: clamp(2rem, 4vw, 3.5rem)`, `font-weight: 800`, color `#FF5900` |
| **Operadores (+, =)** | `font-size: 2rem`, color `#6F6F6F` |
| **Labels** | `font-size: --li-font-caption`, color `#A0A0A0` |
| **Resultado** | El `+60` tiene glow extra: `text-shadow: 0 0 60px rgba(255,89,0,0.3)` |
| **Animación** | Los números aparecen uno a uno de izquierda a derecha |

#### `before-after-split` — Contraste Antes/Después

```
┌────────────────────────┬────────────────────────┐
│                        │                        │
│      📱               │         🌐             │
│                        │                        │
│   150 chats            │    Ecosistema           │
│   1 teléfono           │    integrado            │
│   11:00 PM             │    Cada pregunta al     │
│   Solo voluntad        │    lugar correcto       │
│                        │                        │
│    ░░ oscuro ░░        │    ░░ iluminado ░░     │
│    (desaturado)        │    (acento naranja)     │
│                        │                        │
│       ANTES            │       DESPUÉS           │
└────────────────────────┴────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Layout** | Grid 2 columnas en desktop, stack en mobile |
| **Lado izquierdo** | `background: #0D0D0D`, tono frío, desaturado. Tipografía `color: #6F6F6F`. |
| **Lado derecho** | `background: #1A1A1A` con `border-left: 3px solid #FF5900`. Tipografía `color: #F3F3F1`. Acento naranja. |
| **Divider** | Línea vertical `3px solid #FF5900` entre ambos lados |
| **Animación** | Scroll trigger: el lado izquierdo aparece primero (opacity 1), luego el derecho se "ilumina" |
| **Mobile** | Stack vertical — Antes arriba, Después abajo, con divider horizontal |

#### `team-mosaic` — Mosaico del Equipo

```
┌─────────────────────────────────────────────────┐
│                                                  │
│   ┌────┐ ┌────┐ ┌────┐ ┌────┐ ┌────┐ ┌────┐   │
│   │ 👤 │ │ 👤 │ │ 👤 │ │ 👤 │ │ 👤 │ │ 👤 │   │
│   └────┘ └────┘ └────┘ └────┘ └────┘ └────┘   │
│   ┌────┐ ┌────┐ ┌────┐ ┌────┐ ┌────┐ ┌────┐   │
│   │ 👤 │ │ 👤 │ │ 👤 │ │ 👤 │ │ 👤 │ │ 👤 │   │
│   └────┘ └────┘ └────┘ └────┘ └────┘ └────┘   │
│                                                  │
│   "Para quienes sostienen la línea cada día"    │
│                                                  │
└─────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Layout** | Grid flexible: `repeat(auto-fill, minmax(64px, 1fr))`, gap `8px` |
| **Fotos** | Si existen: `border-radius: 50%`, `object-fit: cover`, `64×64px` con borde `2px solid rgba(255,89,0,0.3)` |
| **Alternativa sin fotos** | 60 cuadros de `48×48px` color `#242424` con borde `1px solid rgba(255,89,0,0.15)`. Representación abstracta de las 60 personas. |
| **Texto inferior** | Quote block centrado, `font-style: italic`, color `#A0A0A0` |
| **Animación** | Los cuadros/fotos aparecen uno a uno en cascada rápida (stagger 0.02s = 60 × 0.02 = 1.2s total) |
| **Hover** (cuadros) | `background: rgba(255,89,0,0.2); transform: scale(1.1)` |

#### `icon-badge` — Badge de Tecnología

```
┌───────────────────────────┐
│  📱  WhatsApp Business    │
└───────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Fondo** | `#242424` |
| **Borde** | `--li-border-subtle` |
| **Radius** | `--li-radius-full` (pill) |
| **Padding** | `8px 16px` |
| **Ícono** | `16px`, a la izquierda |
| **Texto** | `font-size: --li-font-caption`, `font-weight: 500`, color `#F3F3F1` |

#### `dramatic-pause` — Pausa Dramática

```
┌─────────────────────────────────────────────────┐
│                                                  │
│                                                  │
│                                                  │
│           (vacío intencional)                    │
│                                                  │
│                                                  │
│                                                  │
└─────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Altura** | `50vh` |
| **Fondo** | `#000000` puro (más oscuro que el fondo normal) |
| **Contenido** | Vacío. O una sola frase que aparece lentamente en el centro. |
| **Uso** | Replica las pantallas negras del guión coral. Momentos de silencio visual. |

#### `section-overline` — Indicador de Acto

```
         ── ACTO III ──
         EL PACTO
```

| Propiedad | Valor |
|-----------|-------|
| **Overline** | `font-size: --li-font-overline`, `text-transform: uppercase`, `letter-spacing: 0.15em`, color `#FF5900` |
| **Líneas** | Dos líneas horizontales `1px solid rgba(255,89,0,0.3)` a los lados |
| **Título** | `font-size: --li-font-display`, `font-weight: 800`, color `#F3F3F1` |
| **Spacing** | `margin-bottom: --li-space-4xl` |

#### `closing-phrase` — Frase de Cierre

```
┌─────────────────────────────────────────────────┐
│                                                  │
│   Está hecha de 60 personas                     │
│   que eligieron, cada día                       │
│   durante 6 años…                               │
│                                                  │
│              no soltar.                          │  ← naranja, peso mayor
│                                                  │
└─────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Texto principal** | `font-size: --li-font-headline`, `font-weight: 700`, color `#F3F3F1` |
| **"no soltar."** | `font-size: --li-font-display`, `font-weight: 800`, color `#FF5900` |
| **Layout** | Centrado, max-width `700px` |
| **Animación** | Las líneas aparecen una a una. "no soltar." aparece último con delay de 1s y escala desde 0.9 → 1.0 |

#### `final-title` — Título Final

```
┌─────────────────────────────────────────────────┐
│                                                  │
│                                                  │
│          La Línea Invisible                     │
│                                                  │
│     Atención en Línea · Anáhuac Mayab           │
│               6 años                             │
│                                                  │
│          [Logo Anáhuac Mayab]                   │
│                                                  │
│                                                  │
└─────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Altura** | `100vh` centrado |
| **Título** | `font-size: --li-font-display`, color `#F3F3F1` |
| **Subtítulo** | `font-size: --li-font-subhead`, color `#A0A0A0`. "Anáhuac Mayab" en `#FF5900`. |
| **Logo** | Variante blanca/naranja, max-height `48px` |
| **Fondo** | `#0D0D0D` con glow radial naranja muy sutil al centro |

#### `map-mexico` — Mapa de Impacto Nacional

```
┌─────────────────────────────────────────────────┐
│                                                  │
│              🇲🇽 [Mapa de México]                │
│                                                  │
│         ● Mérida  ──→  Red Anáhuac              │
│         (origen)       (adopción nacional)       │
│                                                  │
│   GLPI · Nacido aquí · Adoptado por la Red      │
│                                                  │
└─────────────────────────────────────────────────┘
```

| Propiedad | Valor |
|-----------|-------|
| **Implementación** | SVG simplificado de México con Mérida resaltada como punto naranja pulsante |
| **Flechas** | SVG con `stroke-dasharray` animado, apuntando de Mérida hacia fuera |
| **Color mapa** | `fill: #242424`, `stroke: rgba(255,255,255,0.1)` |
| **Punto Mérida** | `fill: #FF5900` con animación `pulse` (scale 1 → 1.3 → 1, infinito) |
| **Texto** | Caption inferior centrado |
| **Animación** | El mapa aparece fade-in, luego Mérida pulsa, luego las flechas se dibujan |

---

## 4. Guía de Animaciones / Transiciones

### 4.1 Principios de Animación

| Principio | Implementación |
|-----------|---------------|
| **Scroll-driven** | Las animaciones se disparan por IntersectionObserver, NO por tiempo |
| **Progressive disclosure** | Los elementos aparecen conforme se revelan, nunca antes de ser visibles |
| **Subtlety over spectacle** | Movimientos pequeños (10-20px), opacidad y escala. Nunca rotaciones ni bounces exagerados. |
| **Performance** | Solo animar `opacity` y `transform` (propiedades GPU-friendly). Nunca `width`, `height`, `margin`. |
| **Reduced motion** | `@media (prefers-reduced-motion: reduce)` desactiva TODAS las animaciones. Contenido visible inmediatamente. |
| **One direction** | Los elementos se revelan UNA vez. No se ocultan al hacer scroll up. |

### 4.2 Animaciones Base

#### Fade In Up (default para la mayoría de elementos)

```css
.reveal {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.8s ease, transform 0.8s ease;
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}
```

#### Fade In Left (para quote-block)

```css
.reveal-left {
  opacity: 0;
  transform: translateX(-30px);
  transition: opacity 0.8s ease, transform 0.8s ease;
}
.reveal-left.visible {
  opacity: 1;
  transform: translateX(0);
}
```

#### Scale In (para stat-hero numbers)

```css
.reveal-scale {
  opacity: 0;
  transform: scale(0.8);
  transition: opacity 1s ease, transform 1s cubic-bezier(0.16, 1, 0.3, 1);
}
.reveal-scale.visible {
  opacity: 1;
  transform: scale(1);
}
```

#### Stagger (para grids y listas)

```css
.stagger-item {
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.stagger-item.visible {
  opacity: 1;
  transform: translateY(0);
}
/* delay escalonado aplicado con JS: element.style.transitionDelay = `${index * 0.1}s` */
```

#### Count Up (para números)

```javascript
// IntersectionObserver trigger
function countUp(element, target, duration = 1500) {
  const start = 0;
  const startTime = performance.now();
  
  function update(currentTime) {
    const elapsed = currentTime - startTime;
    const progress = Math.min(elapsed / duration, 1);
    const eased = 1 - Math.pow(1 - progress, 3); // ease-out cubic
    const current = Math.floor(start + (target - start) * eased);
    element.textContent = current.toLocaleString('es-MX');
    if (progress < 1) requestAnimationFrame(update);
  }
  requestAnimationFrame(update);
}
```

#### SVG Line Draw (para ecosystem diagram connections)

```css
.svg-line {
  stroke-dasharray: 200;
  stroke-dashoffset: 200;
  transition: stroke-dashoffset 1.5s ease;
}
.svg-line.visible {
  stroke-dashoffset: 0;
}
```

#### Parallax (para hero background)

```javascript
// Solo en hero, performance-safe
window.addEventListener('scroll', () => {
  const scrolled = window.pageYOffset;
  if (scrolled < window.innerHeight) {
    heroImage.style.transform = `translateY(${scrolled * 0.3}px)`;
  }
}, { passive: true });
```

### 4.3 Scroll Triggers por Sección

| Sección | Trigger | Animaciones |
|---------|---------|-------------|
| **Hero** | On load (inmediato) | Título fade-in-up (0.5s delay). Subtítulo fade-in (1s delay). Scroll indicator (2s delay). Background parallax. |
| **Acto I** | `threshold: 0.2` | Overline fade-in. Narrativa reveal por párrafos. `6,000` scale-in + count-up. Quote fade-left. |
| **Acto II** | `threshold: 0.2` | Icon badge fade-in. `150` scale-in + count-up. Texto narrativo reveal. Dramatic pause (elemento vacío). |
| **Acto III** | `threshold: 0.15` | Timeline nodos stagger. Milestone cards fade-up stagger. Expansion grid dominó stagger. Map SVG draw. |
| **Acto IV** | `threshold: 0.15` | Ecosystem diagram: nodos → conexiones SVG draw. Stat cascade count-up secuencial. Team equation left-to-right. Before/After split reveal. |
| **Acto V** | `threshold: 0.3` | Team mosaic cascade (rápida). Quote monument línea por línea. Closing phrase con "no soltar" delayed. Final title slow fade (2s). |

### 4.4 Transición entre Secciones

| Tipo | Implementación |
|------|---------------|
| **Color de fondo** | Las secciones con diferente `background` hacen una transición suave de 50vh de overlap con gradiente CSS |
| **Separadores** | Línea horizontal `1px solid rgba(255,89,0,0.15)`, `max-width: 200px`, centrada, con `margin: 64px auto` |
| **Breathing room** | Mínimo `128px` de padding vertical entre el final de una sección y el inicio de la siguiente |

### 4.5 Reduced Motion

```css
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
  .reveal, .reveal-left, .reveal-scale, .stagger-item {
    opacity: 1 !important;
    transform: none !important;
  }
}
```

---

## 5. Responsive Breakpoints

### 5.1 Breakpoints

| Token | Valor | Dispositivo |
|-------|-------|-------------|
| `--li-bp-mobile` | `480px` | Teléfonos pequeños |
| `--li-bp-tablet` | `768px` | Tablets portrait |
| `--li-bp-desktop` | `1024px` | Tablets landscape, laptops |
| `--li-bp-wide` | `1280px` | Desktop estándar |
| `--li-bp-ultra` | `1600px` | Monitores grandes |

### 5.2 Container System

```css
.container {
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 var(--li-space-lg);
}
.container--narrow {
  max-width: 680px; /* Para texto narrativo */
}
.container--medium {
  max-width: 900px; /* Para stats y diagramas */
}
.container--wide {
  max-width: 1200px; /* Para grids y split layouts */
}
.container--full {
  max-width: none; /* Full bleed */
  padding: 0;
}
```

### 5.3 Adaptación por Componente

| Componente | Mobile (<768px) | Tablet (768–1024px) | Desktop (>1024px) |
|-----------|-----------------|--------------------|--------------------|
| **nav-floating** | Solo logo + acto actual | Logo + actos abreviados | Logo + actos + botón |
| **hero-fullscreen** | Título 3.5rem, sin parallax | Título 5rem, parallax | Título 7rem, parallax |
| **stat-hero** | `font-size: 3.5rem`, padding 64px | `font-size: 5rem`, padding 96px | `font-size: 7rem`, padding 128px |
| **quote-block** | Full width con padding | Max 640px centrado | Max 640px centrado |
| **timeline** | Vertical, cards full width | Vertical, cards 80% | Horizontal con scroll |
| **milestone-card** | Full width stack | 2 columnas | 2 columnas con texto lateral |
| **expansion-grid** | 2 columnas | 3 columnas | 5 columnas (una fila) |
| **ecosystem-diagram** | Vertical stack (sin líneas SVG) | Grid 2×2 | Grid radial con SVG |
| **stat-cascade** | 2 columnas | 4 columnas | 4 columnas inline |
| **team-equation** | Stack vertical (6 → + → 10 → + → 45 → = → 60) | Horizontal con wrap | Horizontal inline |
| **before-after-split** | Stack vertical | Split 50/50 | Split 50/50 con padding |
| **team-mosaic** | 6 columnas (cuadros 40px) | 10 columnas | 12 columnas |
| **closing-phrase** | `font-size: 1.75rem` | `font-size: 2rem` | `font-size: 2.5rem` |

### 5.4 Typography Responsive

Ya incluido en la escala tipográfica mediante `clamp()`:
- `--li-font-hero: clamp(3.5rem, 8vw, 7rem)` — de 56px a 112px
- `--li-font-display: clamp(2.5rem, 5vw, 4.5rem)` — de 40px a 72px
- `--li-font-headline: clamp(1.75rem, 3.5vw, 2.5rem)` — de 28px a 40px
- `--li-font-body: clamp(1rem, 1.2vw, 1.25rem)` — de 16px a 20px

### 5.5 Section Padding Responsive

```css
section {
  padding: var(--li-space-3xl) 0; /* 64px mobile */
}
@media (min-width: 768px) {
  section { padding: var(--li-space-4xl) 0; } /* 96px tablet */
}
@media (min-width: 1024px) {
  section { padding: var(--li-space-5xl) 0; } /* 128px desktop */
}
```

---

## 6. Mapa de Contenido

### 6.1 HERO

| Elemento | Contenido | Componente |
|----------|-----------|------------|
| **Fondo** | Imagen B/N del campus vacío (o gradiente oscuro) | `hero-fullscreen` |
| **Título** | "La Línea Invisible" | display, tracking amplio |
| **Subtítulo** | "Atención en Línea · **Anáhuac Mayab**" | subhead, "Anáhuac Mayab" en naranja |
| **Dato** | "6 años · 60 personas · 1 promesa" | caption |
| **CTA** | Indicador scroll (flecha ↓) | bounce animation |

### 6.2 ACTO I — El Mundo Conocido

| Orden | Elemento | Contenido | Componente |
|-------|----------|-----------|------------|
| 1 | Overline | "ACTO I" | `section-overline` |
| 2 | Título | "El Mundo Conocido" | display |
| 3 | Fecha | "Marzo de 2020" | caption naranja |
| 4 | Narrativa | "El campus en silencio. Los pasillos vacíos. Las ventanillas cerradas." | body, reveal por frase |
| 5 | Stat | **6,000** — "alumnos que necesitaban respuestas" | `stat-hero` |
| 6 | Quote | "¿Qué pasa cuando seis mil personas necesitan respuestas… y nadie sabe por dónde empezar?" | `quote-block` |
| 7 | Pausa | Vacío dramático (50vh negro) | `dramatic-pause` |

### 6.3 ACTO II — El Caos

| Orden | Elemento | Contenido | Componente |
|-------|----------|-----------|------------|
| 1 | Overline | "ACTO II" | `section-overline` |
| 2 | Título | "El Caos" | display |
| 3 | Badge | 📱 WhatsApp — "El canal de facto" | `icon-badge` |
| 4 | Narrativa | "Sacamos el teléfono. WhatsApp personal. Sin protocolo. Sin horario. Sin límites." | body |
| 5 | Stat | **150** — "conversaciones simultáneas · un solo agente" | `stat-hero` |
| 6 | Detalle | "A las once de la noche. En fin de semana." | body-lg, italic, muted |
| 7 | Narrativa | "Las personas que estaban atendiendo se estaban agotando. No había sistema que los protegiera." | body |
| 8 | Quote | "Necesitábamos más que buena voluntad. Necesitábamos un pacto." | `quote-block` |
| 9 | Pausa | Vacío dramático | `dramatic-pause` |

### 6.4 ACTO III — El Pacto

| Orden | Elemento | Contenido | Componente |
|-------|----------|-----------|------------|
| 1 | Overline | "ACTO III" | `section-overline` |
| 2 | Título | "El Pacto" | display |
| 3 | Timeline | **Sep 2020**: Génesis — CAA toca la puerta de DTI. "Nosotros también necesitamos estar ahí." 6 agentes + 6,000 alumnos. Sin bots. | `timeline` nodo 1 |
| 4 | Timeline | **Dic 2020**: Pioneros — WhatsApp Business API + Rocket.Chat + Twilio. Primera universidad en México. "Lo que no existía, lo inventamos." | `timeline` nodo 2 + `milestone-card` |
| 5 | Timeline | **2022**: El efecto dominó — Op. Académica + Escuelas. Nace LeonEl Bot (proteger, no reemplazar). | `timeline` nodo 3 |
| 6 | Timeline | **2024**: Expansión — Operaciones llega. +45 personas. | `timeline` nodo 4 |
| 7 | Grid | Áreas: 🎓 Op. Académica · 🔧 Mantenimiento · 🚌 Mayabus · 🛡️ Seguridad · ⚕️ Salud · 📚 Biblioteca · 🧹 Limpieza | `expansion-grid` |
| 8 | Narrativa | "La línea de atención ya no era solo académica — conectaba desde una duda sobre calificaciones… hasta una emergencia médica en campus." | body-lg |
| 9 | Mapa | GLPI: nacido en Mérida, adoptado por la Red Anáhuac + SERUA | `map-mexico` |
| 10 | Quote | "Lo que construimos como solución local… se volvió referente nacional." | `quote-block` |

### 6.5 ACTO IV — El Ecosistema

| Orden | Elemento | Contenido | Componente |
|-------|----------|-----------|------------|
| 1 | Overline | "ACTO IV" | `section-overline` |
| 2 | Título | "El Ecosistema" | display |
| 3 | Narrativa | "Hoy lo que tenemos ya no es un chat. Es un ecosistema." | body-lg |
| 4 | Diagrama | Rocket.Chat (💬) + GLPI (📋) + Vince (🤖 IA) + Automatizaciones (⚡) — interconectados | `ecosystem-diagram` |
| 5 | Transition | "Los números cuentan la historia mejor que yo." | body, italic |
| 6 | Stats | **300**/día · **2,000** en picos | `stat-cascade` |
| 7 | Equation | **6** CAA + **10** Helpdesk + **45** Operaciones = **+60** personas | `team-equation` |
| 8 | Stats extra | **+15** áreas · **6** años · sin réplica en la Red | `stat-cascade` (segunda fila) |
| 9 | Card | "6 años · Sin un solo día fuera de servicio · Sin réplica en toda la Red de Universidades Anáhuac" | `differentiator-card` (milestone-card variante con borde naranja) |
| 10 | Split | **Antes:** 1 teléfono, 150 chats, 11 PM, solo voluntad → **Después:** ecosistema integrado, cada pregunta al lugar correcto, quien atiende protegido | `before-after-split` |
| 11 | Quote | "Pero un ecosistema no se mide en herramientas. Se mide en personas." | `quote-block` |

### 6.6 ACTO V — El Legado

| Orden | Elemento | Contenido | Componente |
|-------|----------|-----------|------------|
| 1 | Overline | "ACTO V" | `section-overline` |
| 2 | Título | "El Legado" | display |
| 3 | Mosaic | 60 cuadros representando a las 60 personas (o fotos reales si existen) | `team-mosaic` |
| 4 | Narrativa | "Hay personas que durante seis años han sido la voz que contesta cuando alguien no sabe a quién acudir." | body-lg |
| 5 | Frase | "Esto no fue un proyecto de tecnología. Fue un proyecto de confianza." | `quote-monument` |
| 6 | Narrativa | "Áreas que no estaban obligadas a trabajar juntas… y eligieron hacerlo." | body |
| 7 | Frase | "Eso no se instala. No se compra. No se replica." | body-lg, naranja |
| 8 | Monument | "Hay una línea que conecta a un **alumno** con su **respuesta**, a un **profesor** con su **solución**, a una **emergencia** con su **auxilio**." | `quote-monument` (palabras clave en naranja) |
| 9 | Closing | "Está hecha de **60** personas que eligieron, cada día durante **6** años… **no soltar.**" | `closing-phrase` |
| 10 | Pausa | Silencio visual (3s equivalente = espacio vacío 30vh) | `dramatic-pause` |
| 11 | Final | "La Línea Invisible · Atención en Línea · **Anáhuac Mayab** · 6 años" + Logo | `final-title` |

---

## 7. CSS Custom Properties

```css
/* ═══════════════════════════════════════════════════════════════
   LA LÍNEA INVISIBLE — Design Tokens
   Web Storytelling Experience
   Universidad Anáhuac Mayab · 2026
   ═══════════════════════════════════════════════════════════════ */

:root {
  /* ─── Colores: Fondos ─── */
  --li-bg-primary:       #0D0D0D;
  --li-bg-section:       #1A1A1A;
  --li-bg-elevated:      #242424;
  --li-bg-glass:         rgba(26, 26, 26, 0.85);

  /* ─── Colores: Marca ─── */
  --li-accent:           #FF5900;
  --li-accent-hover:     #FF7900;
  --li-accent-glow:      rgba(255, 89, 0, 0.15);
  --li-accent-gradient:  linear-gradient(135deg, #FF5900, #FF7900);
  --li-purple:           #432F64;

  /* ─── Colores: Texto ─── */
  --li-text-primary:     #F3F3F1;
  --li-text-secondary:   #A0A0A0;
  --li-text-muted:       #6F6F6F;
  --li-text-accent:      #FF5900;
  --li-text-inverse:     #0D0D0D;

  /* ─── Colores: Funcionales ─── */
  --li-divider:          rgba(255, 255, 255, 0.08);
  --li-divider-accent:   rgba(255, 89, 0, 0.3);
  --li-overlay-dark:     rgba(0, 0, 0, 0.6);
  --li-overlay-gradient: linear-gradient(to bottom, transparent, #0D0D0D);

  /* ─── Tipografía ─── */
  --li-font-family:      'Manrope', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --li-font-hero:        clamp(3.5rem, 8vw, 7rem);
  --li-font-display:     clamp(2.5rem, 5vw, 4.5rem);
  --li-font-headline:    clamp(1.75rem, 3.5vw, 2.5rem);
  --li-font-subhead:     clamp(1.25rem, 2vw, 1.5rem);
  --li-font-body-lg:     clamp(1.125rem, 1.5vw, 1.375rem);
  --li-font-body:        clamp(1rem, 1.2vw, 1.25rem);
  --li-font-caption:     0.875rem;
  --li-font-overline:    0.75rem;

  /* ─── Pesos tipográficos ─── */
  --li-weight-light:     300;
  --li-weight-regular:   400;
  --li-weight-medium:    500;
  --li-weight-semibold:  600;
  --li-weight-bold:      700;
  --li-weight-extrabold: 800;

  /* ─── Spacing (escala 8px) ─── */
  --li-space-xs:   4px;
  --li-space-sm:   8px;
  --li-space-md:   16px;
  --li-space-lg:   24px;
  --li-space-xl:   32px;
  --li-space-2xl:  48px;
  --li-space-3xl:  64px;
  --li-space-4xl:  96px;
  --li-space-5xl:  128px;
  --li-space-6xl:  160px;

  /* ─── Bordes ─── */
  --li-radius-sm:   8px;
  --li-radius-md:   12px;
  --li-radius-lg:   16px;
  --li-radius-xl:   24px;
  --li-radius-full: 9999px;
  --li-border-subtle:        1px solid rgba(255, 255, 255, 0.08);
  --li-border-accent:        1px solid rgba(255, 89, 0, 0.3);
  --li-border-accent-strong: 2px solid #FF5900;

  /* ─── Sombras ─── */
  --li-shadow-sm:    0 2px 8px rgba(0, 0, 0, 0.3);
  --li-shadow-md:    0 8px 32px rgba(0, 0, 0, 0.4);
  --li-shadow-glow:  0 0 60px rgba(255, 89, 0, 0.15);
  --li-shadow-text:  0 2px 40px rgba(0, 0, 0, 0.5);
  --li-blur-glass:   blur(20px);

  /* ─── Transiciones ─── */
  --li-transition-fast:    0.2s ease;
  --li-transition-base:    0.4s ease;
  --li-transition-slow:    0.8s ease;
  --li-transition-reveal:  0.8s cubic-bezier(0.16, 1, 0.3, 1);

  /* ─── Breakpoints (para referencia JS — CSS usa media queries) ─── */
  --li-bp-mobile:  480px;
  --li-bp-tablet:  768px;
  --li-bp-desktop: 1024px;
  --li-bp-wide:    1280px;
  --li-bp-ultra:   1600px;

  /* ─── Z-Index ─── */
  --li-z-base:    1;
  --li-z-above:   10;
  --li-z-nav:     1000;
  --li-z-overlay: 2000;
}

/* ─── Base Reset ─── */
*, *::before, *::after {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  font-size: 16px;
  scroll-behavior: smooth;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  font-family: var(--li-font-family);
  font-size: var(--li-font-body);
  font-weight: var(--li-weight-regular);
  line-height: 1.7;
  color: var(--li-text-primary);
  background: var(--li-bg-primary);
  overflow-x: hidden;
}

/* ─── Selection ─── */
::selection {
  background: rgba(255, 89, 0, 0.3);
  color: #FFFFFF;
}

/* ─── Scrollbar (WebKit) ─── */
::-webkit-scrollbar {
  width: 8px;
}
::-webkit-scrollbar-track {
  background: var(--li-bg-primary);
}
::-webkit-scrollbar-thumb {
  background: rgba(255, 89, 0, 0.3);
  border-radius: var(--li-radius-full);
}
::-webkit-scrollbar-thumb:hover {
  background: rgba(255, 89, 0, 0.5);
}

/* ─── Accessibility: Reduced Motion ─── */
@media (prefers-reduced-motion: reduce) {
  *, *::before, *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }
  .reveal, .reveal-left, .reveal-scale, .stagger-item {
    opacity: 1 !important;
    transform: none !important;
    transition-delay: 0s !important;
  }
}
```

---

## 8. Guía de Implementación

### 8.1 Stack Tecnológico

| Capa | Tecnología | Razón |
|------|-----------|-------|
| **HTML** | Semántico (article, section, figure, blockquote) | Accesibilidad, SEO |
| **CSS** | Custom Properties + vanilla CSS | Zero dependency, máximo rendimiento |
| **JS** | Vanilla JS (IntersectionObserver, requestAnimationFrame) | Sin frameworks, <10KB minified |
| **Fonts** | Google Fonts (Manrope) | CDN rápido, sin self-hosting |
| **Deployment** | HTML estático (single file o minimal files) | Hosteable en cualquier lado |

### 8.2 Estructura de Archivos

```
la-linea-invisible/
├── index.html          ← Documento principal (self-contained o con refs)
├── css/
│   ├── tokens.css      ← Custom properties (este documento, sección 7)
│   ├── components.css  ← Estilos de componentes
│   └── animations.css  ← Animaciones y scroll triggers
├── js/
│   ├── scroll-observer.js  ← IntersectionObserver para reveals
│   ├── count-up.js         ← Animación de números
│   └── nav.js              ← Navegación flotante + scroll tracking
├── assets/
│   ├── campus-bw.jpg       ← Foto del campus (hero)
│   ├── team-mosaic/        ← Fotos del equipo (si existen)
│   ├── logo-anahuac-white.svg
│   └── map-mexico.svg      ← Mapa simplificado
└── README.md
```

### 8.3 Estructura HTML Semántica

```html
<body>
  <header class="nav-floating" id="nav" aria-label="Navegación principal">
    <!-- Logo + nav actos + volver arriba -->
  </header>

  <main>
    <section class="hero-fullscreen" id="hero" aria-label="Apertura">
      <!-- Hero content -->
    </section>

    <article class="act" id="acto-1" aria-label="Acto I: El Mundo Conocido">
      <div class="container container--narrow">
        <!-- Contenido Acto I -->
      </div>
    </article>

    <article class="act" id="acto-2" aria-label="Acto II: El Caos">
      <div class="container container--narrow">
        <!-- Contenido Acto II -->
      </div>
    </article>

    <article class="act" id="acto-3" aria-label="Acto III: El Pacto">
      <div class="container container--medium">
        <!-- Contenido Acto III (más ancho para timeline) -->
      </div>
    </article>

    <article class="act" id="acto-4" aria-label="Acto IV: El Ecosistema">
      <div class="container container--wide">
        <!-- Contenido Acto IV (más ancho para diagrama y stats) -->
      </div>
    </article>

    <article class="act" id="acto-5" aria-label="Acto V: El Legado">
      <div class="container container--narrow">
        <!-- Contenido Acto V (vuelve a estrecho para intimidad) -->
      </div>
    </article>
  </main>

  <footer class="footer" aria-label="Créditos">
    <!-- Final title + logo -->
  </footer>
</body>
```

### 8.4 Performance Budget

| Métrica | Target |
|---------|--------|
| **Total page weight** | < 500KB (sin imágenes) |
| **First Contentful Paint** | < 1.5s |
| **Largest Contentful Paint** | < 2.5s |
| **CSS total** | < 15KB minified |
| **JS total** | < 10KB minified |
| **Fonts** | 1 familia, 4 pesos = ~80KB |
| **Images** | Lazy loading, WebP, max 200KB c/u |

### 8.5 Accesibilidad

| Requisito | Implementación |
|-----------|---------------|
| **Contraste** | #FF5900 sobre #0D0D0D = 5.3:1 (AA ✅). #F3F3F1 sobre #0D0D0D = 18.1:1 (AAA ✅). |
| **Reduced motion** | `@media (prefers-reduced-motion: reduce)` desactiva todo |
| **Semántica** | `<article>` para actos, `<blockquote>` para citas, `<figure>` para stats |
| **Keyboard nav** | Focus visible en todos los links del nav |
| **aria-label** | En cada `<section>` y `<article>` |
| **Skip link** | "Ir al contenido" oculto, visible en focus |
| **Alt text** | Descripciones en imágenes del mapa y mosaico |
| **Font sizing** | Mínimo 16px para body text, rem units |

---

## 9. Assets Requeridos

### 9.1 Imágenes Necesarias

| Asset | Descripción | Tamaño | Formato | Fallback |
|-------|------------|--------|---------|----------|
| `campus-bw.jpg` | Foto B/N del campus vacío o pasillos desiertos | 1920×1080 | WebP + JPG | Gradiente oscuro CSS |
| `logo-anahuac-white.svg` | Logo Anáhuac Mayab variante blanca | Vector | SVG | Texto "Anáhuac Mayab" en naranja |
| `map-mexico.svg` | Mapa simplificado de México con Mérida | Vector | SVG | Texto descriptivo |
| `team-photos/*.jpg` | Fotos del equipo (si existen) | 128×128 | WebP + JPG | Cuadros abstractos CSS |
| `icon-whatsapp.svg` | Ícono WhatsApp | 24×24 | SVG | Emoji 📱 |
| `icon-rocketchat.svg` | Ícono Rocket.Chat | 24×24 | SVG | Emoji 💬 |

### 9.2 Logos Disponibles

Del brand kit existente en `/brand-kit-anahuac/logos/`:
- `mayab/` — Logos de Anáhuac Mayab
- `tejido/` — Isotipo del tejido
- `base64/` — Data URIs para embedding directo

### 9.3 Favicon

```html
<link rel="icon" type="image/svg+xml" href="data:image/svg+xml,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 100 100'><text y='.9em' font-size='90'>🟠</text></svg>">
```

O usar el distintivo Anáhuac si está disponible como PNG/SVG.

---

## Apéndice A — Checklist de Implementación

- [ ] **Tokens CSS** cargados como primera hoja de estilos
- [ ] **Google Fonts** Manrope incluido en `<head>`
- [ ] **Favicon** configurado
- [ ] **Meta tags** (viewport, charset, description, Open Graph)
- [ ] **Hero** con imagen o gradiente fallback
- [ ] **Nav flotante** con IntersectionObserver
- [ ] **5 secciones** (actos) con contenido mapeado
- [ ] **IntersectionObserver** para reveals
- [ ] **Count-up** para los 8 números dramáticos
- [ ] **SVG** del ecosistema con line-draw
- [ ] **SVG** del mapa de México
- [ ] **Before/After split** responsive
- [ ] **Team mosaic** con 60 elementos
- [ ] **Closing phrase** con animación por línea
- [ ] **Reduced motion** respetado
- [ ] **Performance** < 500KB sin imágenes
- [ ] **Contraste WCAG AA** verificado
- [ ] **Mobile tested** en 375px, 768px, 1024px
- [ ] **Logo Anáhuac** variante blanca/naranja incluido
- [ ] **"Anáhuac Mayab"** siempre en naranja #FF5900

---

## Apéndice B — Arco Emocional Visual

```
Intensidad visual (color naranja + densidad de datos)

  ▲
  │                                              ████
  │                                            ██    ██
  │                                          ██  IV    ██
  │                                    ████ ██          ██
  │                                  ██ III ██            ██
  │                                ██                      ████
  │                              ██                         V  ██
  │                ████████████ ██                               ██
  │    ████████████  II       ██                                   ██
  │  ██  I                                                          ██
  ██ ─────────────────────────────────────────────────────────────────── ▶
     Hero    Acto I    Acto II    Acto III    Acto IV    Acto V    Fin
     (oscuro) (sombrío) (tensión)  (construir)  (poder)  (solemne)
     
     Negro     B/N      Naranja     Naranja     Naranja    Naranja
     puro    mínimo    empieza     crece       MÁXIMO     cálido
```

El naranja actúa como **metáfora visual de la línea que se va construyendo**: empieza invisible (Hero, Acto I casi sin color), aparece tímidamente con los datos del caos (Acto II), crece con la construcción (Acto III), explota en el ecosistema (Acto IV), y se asienta cálido y solemne en el cierre (Acto V).

---

*Documento generado como Fase 5b del pitch "La Línea Invisible"*  
*Blueprint para implementación HTML/CSS/JS estático*  
*Skills aplicados: `color-system`, `type-system`, `design-screen`, `responsive-audit`, `tokenize`, `scroll-animation`, `design-interaction`*  
*Siguiente fase sugerida: implementación del HTML/CSS/JS por un agente Frontend Developer*
