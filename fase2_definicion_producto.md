# Atención en Línea UAM — Definición del Producto

> **Documento de Producto · Fase 2 — Definición del Ecosistema**
> Universidad Anáhuac Mayab · Septiembre 2026

---

## 1. Propuesta de Valor

> **"Un acuerdo vivo entre personas, habilitado por tecnología, que convierte a toda la universidad en una sola ventanilla de atención para el alumno."**

Atención en Línea UAM no es un software. Es la decisión institucional de que ningún alumno se quede sin respuesta — sin importar el canal, el horario o la complejidad de su necesidad.

---

## 2. Definición del Producto

### Qué es

Atención en Línea UAM es un **ecosistema de servicio omnicanal** que articula personas, procesos y herramientas tecnológicas para ofrecer atención continua, trazable y escalable a la comunidad universitaria.

Su naturaleza es triple:

| Dimensión | Descripción |
|---|---|
| **Acuerdo organizacional** | Un pacto entre +15 áreas de la universidad para operar bajo un modelo compartido de atención, con reglas de escalamiento, tiempos de respuesta y responsabilidades claras. |
| **Modelo operativo** | Un diseño de servicio en dos líneas (primer contacto y especialistas) con flujos definidos de triage, derivación y cierre. |
| **Plataforma tecnológica** | Un stack de herramientas (Rocket.Chat, GLPI, WhatsApp Business API, Vince) que habilitan la omnicanalidad, la trazabilidad y la automatización — pero que son *instrumentos*, no el producto. |

### Qué NO es

| Confusión común | Realidad |
|---|---|
| ❌ "Es el chat de la página web" | Es un ecosistema completo de atención que incluye chat, WhatsApp, tickets, IA y atención humana coordinada. |
| ❌ "Es un proyecto de TI" | Es un acuerdo institucional entre áreas académicas, administrativas y operativas. TI lo habilita, no lo posee. |
| ❌ "Es un bot" | Los bots (LeonEl, Vince) son aceleradores del modelo, no el modelo mismo. La inteligencia está en el diseño organizacional. |
| ❌ "Es un call center" | No hay un centro aislado. Es una red distribuida de equipos que operan como uno solo ante el alumno. |
| ❌ "Es un software que se compra" | No existe en el mercado. Se construyó como capacidad institucional propia a lo largo de 6 años. |

### La metáfora

Si la universidad fuera un hospital, Atención en Línea no es el equipo médico — es el **sistema de triaje**: la inteligencia organizacional que asegura que cada paciente llegue al especialista correcto, en el tiempo correcto, con su historial completo.

---

## 3. Modelo Operativo

### 3.1 Arquitectura de Líneas de Servicio

```
┌─────────────────────────────────────────────────────────────┐
│                     ALUMNO / COMUNIDAD                      │
│              (canal de su preferencia)                       │
└──────────┬──────────┬──────────┬──────────┬─────────────────┘
           │          │          │          │
       Web Chat   WhatsApp    App GLPI    Vince (IA)
           │          │          │          │
           ▼          ▼          ▼          ▼
┌─────────────────────────────────────────────────────────────┐
│                  CAPA DE OMNICANALIDAD                       │
│         Rocket.Chat (Omnichannel) + GLPI + Vince            │
│         Unificación de conversaciones y tickets              │
└──────────────────────┬──────────────────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────────────────┐
│              🟢 PRIMERA LÍNEA — Primer Contacto              │
│                                                              │
│  ┌──────────────┐ ┌──────────────┐ ┌──────────────────────┐ │
│  │     CAA      │ │   Helpdesk   │ │    Operaciones       │ │
│  │  Centro de   │ │   Soporte    │ │  Mantenimiento       │ │
│  │  Atención a  │ │   Técnico    │ │  Mayabus · Salud     │ │
│  │  Alumnos     │ │   DTI        │ │  Seguridad · Limp.   │ │
│  │  (6 pers.)   │ │  (10 pers.)  │ │  (+45 pers.)         │ │
│  └──────────────┘ └──────────────┘ └──────────────────────┘ │
│                                                              │
│  + Especialistas LMS (Tecnología Educativa)                  │
└──────────────────────┬──────────────────────────────────────┘
                       │ Escalamiento por reglas
                       ▼
┌─────────────────────────────────────────────────────────────┐
│          🔵 SEGUNDA LÍNEA — Áreas Especializadas             │
│                                                              │
│  ┌────────────────┐ ┌────────────────┐ ┌──────────────────┐ │
│  │ Administración │ │   Finanzas     │ │   Sistemas UAM   │ │
│  │ Escolar, Cert. │ │  Caja · Becas  │ │   Redes UAM      │ │
│  │ y Titulación   │ │                │ │   (vía ticket)   │ │
│  └────────────────┘ └────────────────┘ └──────────────────┘ │
│                                                              │
│  ┌────────────────┐ ┌────────────────────────────────────┐  │
│  │   Biblioteca   │ │  Op. Académica · Escuelas y Fac.   │  │
│  │                │ │  Coordinadores (épocas de cargas)   │  │
│  └────────────────┘ └────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

### 3.2 Mapa de Canales y Funciones

| Canal | Tecnología | Función principal | Tipo de interacción |
|---|---|---|---|
| **Web Chat** | Rocket.Chat Omnichannel | Atención en tiempo real desde el portal UAM | Síncrona, humano + bot |
| **WhatsApp** | WhatsApp Business API (evolución desde Twilio a implementación propia) | Canal preferido por alumnos; primer punto de contacto masivo | Síncrona/asíncrona |
| **GLPI** | Plataforma ITSM open-source + App Móvil | Tickets con seguimiento en el tiempo; trazabilidad ITIL; gestión de activos | Asíncrona, con SLA |
| **Vince** | Agentes de IA (NLU + GenAI) | Atención inmediata 24/7; triage inteligente; respuestas automatizadas | Automatizada con escalamiento |

### 3.3 Flujo Tipo — Ciclo de Vida de una Atención

| Paso | Acción | Responsable | Herramienta |
|---|---|---|---|
| 1 | El alumno inicia contacto por cualquier canal | Alumno | Web Chat / WhatsApp / App GLPI |
| 2 | Triage automático: IA clasifica intención y urgencia | Vince / LeonEl | NLU + reglas de negocio |
| 3 | Si la IA resuelve → cierre inmediato con encuesta | Vince | Respuesta automatizada |
| 4 | Si requiere humano → derivación a Primera Línea (CAA, Helpdesk u Operaciones según categoría) | Sistema | Rocket.Chat + cola de atención |
| 5 | Agente de primera línea atiende; si resuelve → cierre | CAA / Helpdesk / Operaciones | Rocket.Chat + GLPI |
| 6 | Si requiere especialista → escalamiento a Segunda Línea con contexto completo | Agente 1L | GLPI (ticket) |
| 7 | Área especializada resuelve y documenta | Área 2L | GLPI |
| 8 | Cierre, notificación al alumno y registro para métricas | Sistema | GLPI + Rocket.Chat |

---

## 4. Métricas de Impacto

### Magnitud operativa

| Métrica | Valor | Contexto humano |
|---|---|---|
| **Atenciones diarias (promedio)** | **300/día** | Equivale a vaciar y llenar un auditorio de 300 personas *cada día*, uno por uno. |
| **Atenciones en pico** | **2,000/día** | En un solo día de cargas académicas, se atiende a 1 de cada 3 alumnos de la universidad. |
| **Comunidad atendida** | **+8,500 alumnos** (6,000 en 2020, hoy 8,500) | Toda la matrícula tiene acceso a atención omnicanal. |
| **Años de operación continua** | **6 años** (sep 2020 – sep 2026) | Nació como respuesta de emergencia; se convirtió en infraestructura institucional permanente. |
| **Áreas articuladas** | **+15 áreas** | Desde TI hasta Mantenimiento, desde Becas hasta Coordinaciones Académicas — operando como una sola entidad ante el alumno. |
| **Personal involucrado** | **+60 personas** en primera línea | Sin contar segunda línea, que se activa bajo demanda. |

### Antes y después

| Dimensión | Antes (pre-2020) | Después (2020–2026) |
|---|---|---|
| **Canales de atención** | Presencial, teléfono, correo disperso | Omnicanal: WhatsApp, Web Chat, App GLPI, IA |
| **Tiempo de primera respuesta** | Horas o días (dependía de encontrar a la persona correcta) | Minutos (triage automático + colas inteligentes) |
| **Trazabilidad** | Nula — "¿quién atendió esto?" | Completa — cada interacción tiene ticket, historial y responsable |
| **Horario de atención** | Horario de oficina presencial | 24/7 para IA; horario extendido para humanos |
| **Experiencia del alumno** | "Me mandan de oficina en oficina" | "Escribo por WhatsApp y me resuelven" |
| **Visibilidad institucional** | Cada área con su propio buzón invisible | Dashboard unificado con métricas en tiempo real |
| **Escalabilidad en crisis** | Colapso (filas, saturación telefónica) | Absorción elástica (2,000 atenciones/día sin degradación) |

### La cifra que importa

> En 6 años, Atención en Línea UAM ha procesado un estimado de **+400,000 interacciones** con la comunidad universitaria — sin un solo día fuera de operación.
>
> *(~300 atenciones/día × ~220 días hábiles/año × 6 años = ~396,000 atenciones)*

---

## 5. Diferenciador Competitivo

### ¿Por qué no existe réplica en la Red Anáhuac?

Atención en Línea UAM no es un sistema que se instala. Es el resultado de **6 años de negociación organizacional, iteración tecnológica y construcción de cultura de servicio**. Su irreplicabilidad no es técnica — es institucional.

| Factor | Por qué es difícil de replicar |
|---|---|
| **Acuerdo entre áreas** | Requiere que +15 áreas acepten un modelo compartido de atención, cedan autonomía sobre "sus" canales y operen bajo reglas comunes. Esto es un logro político-organizacional, no tecnológico. |
| **Cultura de servicio construida** | 6 años de operación crearon hábitos, expectativas y estándares. Los alumnos *esperan* respuesta por WhatsApp. Las áreas *saben* que deben atender tickets. Eso no se instala. |
| **Conocimiento tácito acumulado** | El CAA ha resuelto +400K interacciones. Ese conocimiento de patrones, excepciones y soluciones no está en un manual — está en las personas y en los datos. |
| **Evolución orgánica del stack** | La tecnología se fue adaptando al modelo (no al revés): de Twilio a API propia, de Lex a Vince, de tickets básicos a ITIL. Cada evolución respondió a una necesidad real, no a una tendencia. |
| **Efecto de red interno** | Cada área que se suma al ecosistema lo hace más valioso para todas las demás. Desmontar una pieza afecta a todo el sistema. |
| **Liderazgo sostenido** | Requirió un equipo que defendiera el modelo durante 6 años, a través de cambios de administración, presupuestos y prioridades. |

### Paradoja de la adopción parcial

Otras universidades de la Red Anáhuac han adoptado **componentes** del ecosistema:
- **GLPI** fue adoptado por la mayoría de universidades de la red y por SERUA (Servicios de la Red de Universidades Anáhuac).

Pero adoptar la herramienta no es adoptar el modelo. GLPI sin el acuerdo organizacional es solo un sistema de tickets. **La herramienta sin el pacto es infraestructura inerte.**

---

## 6. Evolución del Producto — Fases de Madurez

| Fase | Período | Nombre | Hito clave | Naturaleza del cambio |
|---|---|---|---|---|
| **0** | Mar – Ago 2020 | **Emergencia** | Pandemia obliga a cerrar ventanillas presenciales. Se improvisa atención remota. | Supervivencia |
| **1** | Sep 2020 – Dic 2020 | **Génesis** | Lanzamiento formal de Atención en Línea. Rocket.Chat como hub. Primeras colas de atención. WhatsApp vía Twilio. | Fundación del acuerdo organizacional |
| **2** | 2021 | **Estabilización** | GLPI se integra para trazabilidad ITIL. Se definen líneas de servicio (1L y 2L). Áreas especializadas se incorporan. | Institucionalización |
| **3** | 2022 | **Automatización v1** | LeonEl Bot (AWS Lex + Lambda) para triage automático. Bot especializado de cargas académicas. Reducción de carga en primera línea. | Primera capa de IA |
| **4** | 2024 | **Expansión** | App Móvil GLPI. Operaciones (+45 personas) se integra al modelo. Cobertura de mantenimiento, transporte, salud, seguridad. | Ampliación del acuerdo organizacional |
| **5** | 2024 | **Inteligencia** | Migración de Twilio a WhatsApp Business API propia. Evolución de LeonEl a Vince (IA generativa). Atención 24/7 por IA. | Autonomía tecnológica + GenAI |
| **6** | 2025 – 2026 | **Madurez** | 6 años de operación. +400K interacciones acumuladas. Modelo documentado como producto. Referencia en la Red Anáhuac. | Consolidación y legado |

### Lectura de la evolución

```
Emergencia → Acuerdo → Proceso → Automatización → Expansión → Inteligencia → Madurez
   (2020)    (2020)    (2021)      (2022)          (2023)       (2024)       (2025-26)

   Técnico:  Chat ──→ Chat+Tickets ──→ +Bot NLU ──→ +App Móvil ──→ +GenAI ──→ Ecosistema
   Humano:   6 pers ──→ +10 pers ──→ +especialistas ──→ +45 Ops ──→ +IA 24/7 ──→ +60 pers
   Orga:     1 área ──→ 3 áreas ──→ +8 áreas ──→ +15 áreas ──→ Red Anáhuac adopta GLPI
```

---

## 7. Glosario

| Término | Definición |
|---|---|
| **Atención en Línea UAM** | Ecosistema de servicio omnicanal de la Universidad Anáhuac Mayab. Acuerdo organizacional entre áreas, habilitado por tecnología, para atención integral al alumno. |
| **CAA** | Centro de Atención a Alumnos. Equipo de 6 personas que opera como ventanilla única (one-stop) en primera línea. |
| **DTI** | Dirección de Tecnologías de la Información. Área que administra el Helpdesk de Soporte Técnico y los Especialistas LMS. |
| **Primera Línea (1L)** | Nivel de primer contacto. Incluye CAA, Helpdesk DTI, Especialistas LMS y Operaciones. Resuelve o escala. |
| **Segunda Línea (2L)** | Áreas especializadas que reciben escalamientos: Administración Escolar, Finanzas, Becas, Sistemas, Redes, Biblioteca, Operación Académica. |
| **Rocket.Chat** | Plataforma de mensajería open-source con módulo Omnichannel. Hub central de conversaciones en tiempo real (Web Chat + WhatsApp). |
| **GLPI** | Gestionnaire Libre de Parc Informatique. Sistema de tickets ITSM con enfoque ITIL. Proporciona trazabilidad, SLAs y seguimiento en el tiempo. Adoptado por la mayoría de universidades de la Red Anáhuac. |
| **Vince** | Plataforma de agentes de IA (NLU + IA generativa) para atención automatizada inmediata. Evolución de LeonEl Bot. |
| **LeonEl Bot** | Primer bot de triage (2022). Arquitectura: AWS API Gateway + Lambda + Lex + conector Rocket.Chat. Precursor de Vince. |
| **WhatsApp Business API** | Canal de mensajería masiva. Inicialmente operado vía Twilio; evolucionó a implementación propia para mayor control y reducción de costos. |
| **Omnicanalidad** | Capacidad de atender al alumno por múltiples canales (WhatsApp, Web Chat, App, tickets) manteniendo contexto unificado. |
| **Triage** | Proceso de clasificación inicial de una solicitud por tipo, urgencia y área responsable. Puede ser automático (IA) o manual (agente 1L). |
| **Escalamiento** | Derivación de una atención de primera línea a segunda línea cuando requiere conocimiento especializado. Siempre con contexto y ticket. |
| **One-stop** | Modelo de ventanilla única: el alumno no necesita saber a qué área dirigirse; el sistema lo resuelve internamente. |
| **ITIL** | Information Technology Infrastructure Library. Marco de buenas prácticas para gestión de servicios de TI. Base del modelo de tickets en GLPI. |
| **NLU** | Natural Language Understanding. Capacidad de un sistema de IA para comprender la intención del usuario en lenguaje natural. |
| **GenAI** | Inteligencia Artificial Generativa. Modelos de lenguaje capaces de generar respuestas contextuales (base de Vince). |
| **SLA** | Service Level Agreement. Acuerdo de nivel de servicio que define tiempos máximos de respuesta y resolución por tipo de ticket. |
| **SERUA** | Servicios de la Red de Universidades Anáhuac. Entidad de servicios compartidos de la red que adoptó GLPI. |
| **Red Anáhuac** | Red de Universidades Anáhuac. Sistema de universidades privadas en México al que pertenece la Universidad Anáhuac Mayab. |
| **Mayabus** | Servicio de transporte universitario operado por el área de Operaciones e integrado al ecosistema de atención. |
| **Stack tecnológico** | Conjunto de herramientas tecnológicas que habilitan el ecosistema: Rocket.Chat + GLPI + WhatsApp API + Vince. |

---

## Nota Final

> Este documento define **el producto tal como existe hoy**: un ecosistema maduro de 6 años que transformó la relación entre la universidad y sus alumnos.
>
> La tecnología fue el habilitador. Las personas fueron el motor. El acuerdo organizacional fue — y sigue siendo — el producto.

---

*Documento generado como parte de la documentación estratégica del ecosistema Atención en Línea UAM.*
*Fase 2 — Definición del Producto · Septiembre 2026*
