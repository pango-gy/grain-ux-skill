# grain — skill de revisión UX para agentes de IA

> Trabaja a favor de cómo las personas realmente piensan, leen, deciden, confían y se recuperan.

**Idiomas:** [English](README.md) | [한국어](README.ko.md) | [日本語](README.ja.md) | [简体中文](README.zh-CN.md) | [Español](README.es.md)

Mantenido por [Pango Gy](https://pango-gy.com).

`grain` es un skill portable para agentes de IA que revisa y guía decisiones de producto visibles para usuarios. No es un tema visual, una librería de componentes ni un sistema de diseño. Es una capa de juicio UX que cuestiona flujos, formularios, errores, acciones de IA, permisos y etiquetas de botones cuando trabajan contra usuarios reales.

Úsalo junto con builders frontend, skills de sistemas de diseño, UI kits y revisión de código de producto. Esas herramientas ayudan al agente a construir la interfaz; `grain` ayuda a comprobar si la interfaz respeta el esfuerzo, la atención, la accesibilidad, la confianza y la recuperación del usuario.

## El Nombre

`grain` significa la dirección o textura natural de un material, como la veta de la madera. Trabajar "with the grain" es avanzar con esa estructura natural en vez de luchar contra ella. Este skill usa ese nombre porque una buena UX sigue cómo las personas realmente piensan, leen, deciden, confían y se recuperan.

## Instalación

```bash
npx skills add pango-gy/grain-ux-skill
```

Por defecto, `skills` CLI instala skills de proyecto en `./.agents/skills/grain`. Ese directorio compartido es la ubicación de proyecto usada por agentes universales como Codex y Gemini CLI. Los agentes con su propio directorio de skills de proyecto, como Claude Code, reciben un symlink o una copia cuando ese directorio existe en el proyecto.

Para crear copias reales en todos los directorios de agentes compatibles:

```bash
npx skills add pango-gy/grain-ux-skill --agent '*' --skill '*' -y --copy
```

Ejecuta de nuevo el comando add para actualizar.

Para eliminarlo:

```bash
npx skills remove grain
```

Esto elimina los directorios de skill instalados. Si tu proyecto usa `skills-lock.json`, revisa ese archivo después de eliminar porque la CLI puede conservar metadata de origen para flujos de restauración o actualización.

## Cuándo Se Activa

`grain` se activa automáticamente en decisiones visibles para usuarios:

- Escribir, refactorizar o revisar componentes UI, pantallas, formularios y flujos
- Diseñar o criticar estados vacíos, de carga, fallidos, parciales, offline y sin permisos
- Redactar copy, etiquetas, microcopy, mensajes de error, onboarding o notificaciones
- Revisar accesibilidad, comportamiento con teclado, orden de foco, targets táctiles, movimiento y responsive
- Diseñar formularios, importaciones, filtros, ajustes, permisos, compartir, facturación, output de IA o automatización
- Revisar screenshots, prototipos, dashboards, herramientas internas, superficies admin o workflows SaaS

Debe permanecer en silencio para lógica puramente backend, infraestructura o trabajos sin comportamiento visible para usuarios.

## Qué Cubre

Siete dominios, una sola voz:

- **Flujo de usuario y arquitectura de información** — caminos antes que páginas, tareas antes que tablas.
- **Carga cognitiva y simplicidad** — menos decisiones, no solo menos clics.
- **Formularios e input** — cada campo debe justificar su costo, y la validación debe ayudar en vez de regañar.
- **Accesibilidad e interacción inclusiva** — teclado, touch, foco, movimiento, contraste y viewport son UX base.
- **Confianza, consentimiento y agencia** — nada de envíos, compartidos, cobros, borrados, commits de IA o automatizaciones sorpresa.
- **Errores, casos borde y recuperación** — estados vacíos/carga/fallo/offline como parte central del producto.
- **Microcopy y tono** — los botones describen resultados, los errores no culpan y cada frase debe poder leerse en voz alta.

Cada dominio tiene una referencia más profunda en [`skill/references/`](skill/references). `SKILL.md` indica cuándo cargar cada referencia para mantener el skill principal enfocado.

## Filosofía Central

`grain` aplica primero estas leyes:

- Haz obvia la siguiente acción.
- Simplifica la regla antes que la pantalla.
- Muestra valor antes de pedir esfuerzo.
- Preserva el esfuerzo del usuario.
- No sorprendas al usuario.
- Permite deshacer, no solo confirmar.
- Trata la accesibilidad como UX base, no como un modo.
- Diseña los estados de fallo como parte del producto.

El conjunto completo de leyes, rutas de dominio y anti-patrones vive en [`skill/SKILL.md`](skill/SKILL.md).

## Posicionamiento

`grain` funciona mejor como companion skill:

- Combínalo con un **frontend builder** para detectar regresiones UX antes de que el código entre.
- Combínalo con un **sistema de diseño** para asegurar que los componentes se usan para la tarea correcta, no solo con el estilo correcto.
- Combínalo con un **skill de IA/automatización** para exigir preview, consent, status, history y explicit approval antes de acciones duraderas o externas.
- Combínalo con un **workflow de revisión de producto** para convertir feedback vago en leyes y anti-patrones concretos.

No genera identidad visual, no elige paletas de marca y no reemplaza investigación de producto. Da a los agentes un estándar UX reutilizable para las decisiones que ya toman al programar o revisar.

## Ejemplos De Prompts De Revisión

```text
Use grain to review this checkout flow for trust, consent, and recovery.
```

```text
Use grain while refactoring this settings form. Preserve input and improve validation UX.
```

```text
Use grain to check whether this AI-generated email flow needs preview, edit, and approval states.
```

```text
Use grain to review this dashboard for cognitive load, accessibility, and empty states.
```

## Autor

CTO de Pango Gy, 유승재 ([pinkyooysj@pango-gy.com](mailto:pinkyooysj@pango-gy.com))

Empresa: [Pango Gy](https://pango-gy.com)

## Licencia

[MIT](LICENSE). Úsalo, haz fork o reescríbelo con tu propia voz. El objetivo es que más productos traten UX como una preocupación de primer nivel.

## Linaje

Se apoya en Donald Norman, Jakob Nielsen, Steve Krug, Bruce Tognazzini, Alan Cooper, Dan Saffer y Edward Tufte. Consulta la sección `Lineage` en [`skill/SKILL.md`](skill/SKILL.md) para ver de dónde viene cada idea.
