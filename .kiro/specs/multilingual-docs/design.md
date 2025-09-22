# Design Document

## Overview

The multilingual documentation system will extend berrybyte's existing Mintlify documentation to support German (`de`) and Spanish (`es`) alongside English, using Mintlify's native `navigation.languages` feature. The design preserves all existing English content and URLs while introducing parallel German and Spanish documentation trees with localized slugs, natural translations, and proper cross-referencing.

The architecture follows a "mirror and localize" approach where German and Spanish content mirrors the English structure but uses natural terminology for slugs, titles, and content in each respective language. This ensures both technical accuracy and cultural appropriateness for German and Spanish-speaking users.

## Architecture

### File System Structure

```
docs/
├── docs.json                           # Extended with German and Spanish navigation
├── introduction.mdx                    # English (unchanged)
├── quickstart.mdx                      # English (unchanged)
├── games/minecraft/introduction.mdx    # English (unchanged)
├── de/                                 # German content directory
│   ├── einfuehrung.mdx                # German introduction
│   ├── schnellstart.mdx               # German quickstart
│   └── spiele/
│       └── minecraft/
│           ├── einfuehrung.mdx        # German Minecraft intro
│           ├── server-beitreten.mdx   # German join server guide
│           └── mods-installieren.mdx  # German mod installation
├── es/                                 # New Spanish content directory
│   ├── introduccion.mdx               # Spanish introduction
│   ├── inicio-rapido.mdx              # Spanish quickstart
│   └── juegos/
│       └── minecraft/
│           ├── introduccion.mdx       # Spanish Minecraft intro
│           ├── unirse-servidor.mdx    # Spanish join server guide
│           └── instalar-mods.mdx      # Spanish mod installation
└── images/                            # Shared assets (unchanged)
```

### URL Structure

- **English (unchanged)**: `/introduction`, `/games/minecraft/join-server`
- **German**: `/de/einfuehrung`, `/de/spiele/minecraft/server-beitreten`
- **Spanish (new)**: `/es/introduccion`, `/es/juegos/minecraft/unirse-servidor`

### Configuration Architecture

The `docs.json` file will be extended to include German and Spanish language blocks within the existing `navigation.languages` array, maintaining the current English configuration while adding parallel German and Spanish navigation.

## Components and Interfaces

### Language Configuration Interface

```json
{
  "navigation": {
    "languages": [
      {
        "language": "en",
        "dropdowns": [/* existing English navigation */]
      },
      {
        "language": "de", 
        "dropdowns": [
          {
            "dropdown": "Allgemeine Anleitungen",
            "icon": "book",
            "description": "Erste Schritte, Abrechnung und Server-Verwaltungsanleitungen",
            "groups": [
              {
                "group": "Willkommen",
                "pages": [
                  "de/einfuehrung",
                  "de/schnellstart",
                  "de/migration",
                  "de/changelog"
                ]
              }
            ]
          }
        ]
      },
      {
        "language": "es", 
        "dropdowns": [
          {
            "dropdown": "Guías Generales",
            "icon": "book",
            "description": "Primeros pasos, facturación y guías de gestión de servidores",
            "groups": [
              {
                "group": "Bienvenido",
                "pages": [
                  "es/introduccion",
                  "es/inicio-rapido",
                  "es/migracion",
                  "es/changelog"
                ]
              }
            ]
          }
        ]
      }
    ]
  }
}
```

### Content Translation Interface

Each German and Spanish MDX file will follow this structure:

**German Example:**
```mdx
---
title: "Minecraft Server-Hosting Anleitungen - Setup, Mods, Plugins & Fehlerbehebung"
sidebarTitle: "Minecraft"
description: "Umfassende Minecraft Server-Hosting Anleitungen für Setup, Modpacks, Plugins wie Dynmap und Geyser, Performance-Optimierung mit Aikar's Flags und Fehlerbehebung."
---

# Minecraft Server-Hosting Anleitungen

Unsere umfassenden Minecraft Server-Hosting Anleitungen decken alles ab...

## Setup & Installation

<CardGroup cols={2}>
  <Card title="Server beitreten" href="/de/spiele/minecraft/server-beitreten" icon="users">
    Verbinde dich mit deinem Minecraft-Server und lade Freunde ein
  </Card>
</CardGroup>
```

**Spanish Example:**
```mdx
---
title: "Guías de Hosting de Servidores Minecraft - Configuración, Mods, Plugins y Solución de Problemas"
sidebarTitle: "Minecraft"
description: "Guías completas de hosting de servidores Minecraft para configuración, modpacks, plugins como Dynmap y Geyser, optimización de rendimiento con Aikar's Flags y solución de problemas."
---

# Guías de Hosting de Servidores Minecraft

Nuestras guías completas de hosting de servidores Minecraft cubren todo...

## Configuración e Instalación

<CardGroup cols={2}>
  <Card title="Unirse al servidor" href="/es/juegos/minecraft/unirse-servidor" icon="users">
    Conéctate a tu servidor de Minecraft e invita a amigos
  </Card>
</CardGroup>
```

### Link Resolution System

Internal links within German and Spanish content will be processed according to these rules:

1. **German-to-German**: `[Server beitreten](/de/spiele/minecraft/server-beitreten)` - Direct German link
2. **Spanish-to-Spanish**: `[Unirse al servidor](/es/juegos/minecraft/unirse-servidor)` - Direct Spanish link
3. **German-to-English (temporary)**: `[Erweiterte Konfiguration](/games/minecraft/advanced-config)` with German notice
4. **Spanish-to-English (temporary)**: `[Configuración Avanzada](/games/minecraft/advanced-config)` with Spanish notice
5. **External links**: Unchanged unless localized equivalents exist

### Translation Notice Component

For untranslated references, standardized notices will be used:

**German Notice:**
```mdx
<Info>
Dieser Abschnitt ist derzeit nur auf Englisch verfügbar. [Zur englischen Version →](/games/minecraft/advanced-config)
</Info>
```

**Spanish Notice:**
```mdx
<Info>
Esta sección está disponible actualmente solo en inglés. [Ir a la versión en inglés →](/games/minecraft/advanced-config)
</Info>
```

## Data Models

### Language Mapping Model

```typescript
interface LanguageMapping {
  en: {
    slug: string;
    title: string;
    path: string;
  };
  de: {
    slug: string;
    title: string;
    path: string;
  };
  es: {
    slug: string;
    title: string;
    path: string;
  };
}

// Example mapping
const minecraftIntro: LanguageMapping = {
  en: {
    slug: "introduction",
    title: "Minecraft Server Hosting Guides",
    path: "games/minecraft/introduction"
  },
  de: {
    slug: "einfuehrung", 
    title: "Minecraft Server-Hosting Anleitungen",
    path: "de/spiele/minecraft/einfuehrung"
  },
  es: {
    slug: "introduccion",
    title: "Guías de Hosting de Servidores Minecraft",
    path: "es/juegos/minecraft/introduccion"
  }
};
```

### Content Structure Model

```typescript
interface TranslatedContent {
  frontmatter: {
    title: string;
    sidebarTitle: string;
    description: string;
    tags?: string;
  };
  content: {
    headings: string[];
    body: string;
    codeBlocks: CodeBlock[]; // Preserved as-is
    links: InternalLink[];
    images: ImageReference[];
  };
}

interface CodeBlock {
  language: string;
  content: string; // Never translated
  comments?: string[]; // Translated if present
}
```

## Error Handling

### Build-Time Error Prevention

1. **Missing Translation Validation**: Build process will validate that all referenced German pages exist
2. **Link Validation**: Internal links in German content will be checked for valid targets
3. **Asset Path Validation**: Image and asset references will be verified during build

### Runtime Error Handling

1. **404 Prevention**: German navigation will only include pages that actually exist
2. **Graceful Fallbacks**: Missing German pages will redirect to English equivalents with language notice
3. **Asset Loading**: Shared assets will maintain consistent paths across languages

### Incremental Rollout Safety

```json
// German navigation only includes translated pages
{
  "group": "Minecraft",
  "pages": [
    "de/spiele/minecraft/einfuehrung",
    "de/spiele/minecraft/server-beitreten"
    // "de/spiele/minecraft/mods-installieren" - Not included until translated
  ]
}

// Spanish navigation only includes translated pages
{
  "group": "Minecraft",
  "pages": [
    "es/juegos/minecraft/introduccion",
    "es/juegos/minecraft/unirse-servidor"
    // "es/juegos/minecraft/instalar-mods" - Not included until translated
  ]
}
```

## Testing Strategy

### Translation Quality Assurance

1. **Technical Accuracy Testing**: Verify that code blocks, commands, and file paths remain unchanged
2. **Terminology Consistency**: Ensure German gaming and technical terms are used consistently
3. **Natural Language Flow**: Review translations for natural German phrasing and readability
4. **Cross-Reference Validation**: Test that internal links work correctly between languages

### Build and Deployment Testing

1. **Incremental Build Testing**: Verify site builds successfully with partial German translations
2. **URL Preservation Testing**: Confirm all existing English URLs remain unchanged
3. **Navigation Testing**: Validate that German sidebar shows only translated content
4. **Asset Loading Testing**: Ensure images and resources load correctly from German pages

### User Experience Testing

1. **Language Switching Testing**: Verify language switcher functionality (if available)
2. **Search Functionality Testing**: Confirm German content appears in German search results
3. **Mobile Responsiveness Testing**: Ensure German content displays properly on mobile devices
4. **SEO Metadata Testing**: Validate German meta titles and descriptions are properly set

### Performance Testing

1. **Build Time Impact**: Measure build time increase with German content addition
2. **Page Load Testing**: Ensure German pages load at comparable speeds to English
3. **Search Index Size**: Monitor search index growth with German content addition

## Implementation Phases

### Phase 1: Foundation Setup
- Extend `docs.json` with German language configuration
- Create `docs/de/` directory structure
- Implement translation guidelines and tooling

### Phase 2: High-Priority Content Translation
- Translate introduction and quickstart guides
- Translate top 3 game categories (Minecraft, Palworld, Rust)
- Implement cross-referencing system

### Phase 3: Content Expansion
- Translate remaining game guides
- Translate help and support sections
- Implement advanced SEO features

### Phase 4: Optimization and Enhancement
- Add language switching capabilities
- Implement hreflang attributes
- Optimize search functionality for multilingual content

## SEO and Metadata Strategy

### URL Structure for SEO

German and Spanish URLs will use natural terms that users would search for:

**German URLs:**
- `/de/spiele/minecraft/server-beitreten` (natural German search term)
- `/de/spiele/palworld/server-einrichten` (localized terminology)
- `/de/hilfe/server-ausstehend` (translated help topics)

**Spanish URLs:**
- `/es/juegos/minecraft/unirse-servidor` (natural Spanish search term)
- `/es/juegos/palworld/configurar-servidor` (localized terminology)
- `/es/ayuda/servidor-pendiente` (translated help topics)

### Metadata Localization

**German Example:**
```mdx
---
title: "Minecraft Server beitreten - Schritt-für-Schritt Anleitung"
description: "Detaillierte Anleitung zum Beitreten von Minecraft-Servern für Multiplayer-Gameplay. Lerne Server-IP finden, Verbindung herstellen und häufige Probleme lösen."
---
```

**Spanish Example:**
```mdx
---
title: "Unirse a Servidor Minecraft - Guía Paso a Paso"
description: "Guía detallada para unirse a servidores de Minecraft para juego multijugador. Aprende a encontrar IP del servidor, establecer conexión y resolver problemas comunes."
---
```

### Hreflang Implementation

When supported by Mintlify or hosting layer:

```html
<link rel="alternate" hreflang="en" href="https://docs.berrybyte.net/games/minecraft/join-server" />
<link rel="alternate" hreflang="de" href="https://docs.berrybyte.net/de/spiele/minecraft/server-beitreten" />
<link rel="alternate" hreflang="es" href="https://docs.berrybyte.net/es/juegos/minecraft/unirse-servidor" />
<link rel="canonical" href="https://docs.berrybyte.net/es/juegos/minecraft/unirse-servidor" />
```

## Security and Compliance Considerations

### Content Security
- All German and Spanish content will undergo the same security review as English content
- Code examples and commands will be validated for security best practices
- External links will be reviewed for trustworthiness and relevance

### GDPR Compliance
- German and Spanish content will maintain the same privacy standards as English content
- Analytics and tracking will respect user language preferences
- Cookie notices and privacy policies will be appropriately localized

## Monitoring and Analytics

### Translation Performance Metrics
- German and Spanish page view statistics
- User engagement metrics for German and Spanish content
- Search query analysis for German and Spanish terms

### Technical Performance Monitoring
- Build time impact measurement
- Page load speed comparison between languages
- Search functionality performance for German and Spanish queries

### Content Quality Metrics
- User feedback on translation quality
- Support ticket analysis for language-specific issues
- Cross-reference click-through rates between languages