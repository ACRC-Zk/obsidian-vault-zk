# Curaduría y Agentes Validadores

La capa que mantiene la **calidad y veracidad** del contenido de la
[[Plataforma de Opinión Verificada]] sin silenciar a las personas. Desarrolla la idea de
curaduría planteada en [[IDEA]].

## El problema que resuelve

Aunque cada usuario sea una [[Prueba de Persona Única|persona real y única]], el contenido
**igual se puede ensuciar**: desinformación, artículos sin respaldo, discurso de odio. El
reto es filtrar eso **sin perder el criterio de la persona** — es decir, sin convertirse
en censura.

## Cómo funciona: curaduría en dos niveles

```mermaid
flowchart TB
    C["📄 Contenido publicado<br/>(opinión / artículo / estudio)"] --> A["🤖 Agente validador"]
    A --> D{¿Puede resolverlo?}
    D -->|Sí| OK["✅ Curado / etiquetado<br/>(veracidad evaluada)"]
    D -->|No / caso ambiguo| M["🧑‍⚖️ Moderadores humanos"]
    M --> R["Resolución con criterio humano"]
```

### Nivel 1 — Agentes validadores (automático)

Agentes de IA que actúan como **curadores**: revisan el contenido y evalúan su veracidad
y calidad (por ejemplo: ¿el estudio cita fuentes?, ¿el artículo es coherente y
verificable?, ¿hay señales de abuso?).

### Nivel 2 — Moderadores humanos (derivación)

Cuando un agente **se topa con una problemática que no sabe resolver** (un caso ambiguo,
sensible o fuera de su criterio), **lo deriva a moderadores** humanos. Así se combina la
escala de la automatización con el **criterio humano** para los casos difíciles.

## Principio rector

> **No perder el criterio de la persona.** La curaduría busca filtrar ruido, abuso y
> desinformación — **no** acallar opiniones legítimas. La derivación a humanos existe
> justamente para que ningún caso dudoso se resuelva con un automatismo ciego.

## Relación con la identidad

La curaduría se apoya en que cada autor es una persona única y, opcionalmente, en que su
actividad puede ser **pública** (ver [[Identidad Pública vs Anónima]]). Cuando el
comportamiento de una persona es público y persistente, es más fácil distinguir si una
intervención **nace desde el odio** o de alguien que **realmente quiere aportar** — y eso
alimenta el criterio de la curaduría.

## Preguntas abiertas

- [ ] ¿Qué evalúa exactamente un agente? (veracidad, fuentes, toxicidad, plagio…)
- [ ] ¿Dónde está el límite preciso entre lo que resuelve el agente y lo que va a moderación?
- [ ] ¿Cómo se eligen y gobiernan los moderadores? (¿son personas verificadas? ¿reputación?)
- [ ] ¿La curaduría es on-chain, off-chain, o híbrida? (los agentes corren off-chain)
- [ ] ¿Hay apelación de una decisión de moderación?

Relacionado: [[IDEA]] · [[Plataforma de Opinión Verificada]] · [[Identidad Pública vs Anónima]] · [[Prueba de Persona Única]]
