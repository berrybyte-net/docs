# Implementation Plan

- [x] 1. Configure multilingual support in Mintlify
  - Extend docs.json with German language configuration while preserving all existing English navigation
  - Create German navigation structure mirroring English groups with natural German group names
  - Validate that build process works with partial German translations
  - _Requirements: 2.1, 2.2, 4.2, 3.2_

- [x] 1.1 Add Spanish language configuration to Mintlify
  - Extend docs.json with Spanish language configuration alongside existing English and German
  - Create Spanish navigation structure mirroring English groups with natural Spanish group names
  - Validate that build process works with partial Spanish translations
  - _Requirements: 2.1, 2.2, 4.3, 3.2_

- [x] 2. Create German directory structure and foundation files
  - Create docs/de/ directory with mirrored structure for initial content categories
  - Implement German introduction page (de/einfuehrung.mdx) with natural translation
  - Implement German quickstart guide (de/schnellstart.mdx) with localized content
  - _Requirements: 1.1, 4.1, 4.4_

- [x] 2.1 Create Spanish directory structure and foundation files
  - Create docs/es/ directory with mirrored structure for initial content categories
  - Implement Spanish introduction page (es/introduccion.mdx) with natural translation
  - Implement Spanish quickstart guide (es/inicio-rapido.mdx) with localized content
  - _Requirements: 1.1, 4.2, 4.5_

- [x] 3. Implement high-priority Minecraft German translations
  - [x] 3.1 Create German Minecraft introduction page
    - Translate games/minecraft/introduction.mdx to de/spiele/minecraft/einfuehrung.mdx
    - Use natural German gaming terminology and maintain technical accuracy
    - Implement German CardGroup components with localized titles and descriptions
    - _Requirements: 1.4, 8.2, 8.3_

  - [x] 3.2 Create German Minecraft join server guide
    - Translate games/minecraft/join-server.mdx to de/spiele/minecraft/server-beitreten.mdx
    - Preserve all code blocks, IP addresses, and technical commands exactly as-is
    - Translate image alt text and captions to German while maintaining accessibility
    - _Requirements: 1.4, 8.1, 8.5_

  - [x] 3.3 Create German Minecraft common errors guide
    - Translate games/minecraft/common-errors/connection-timed-out.mdx to de/spiele/minecraft/haeufige-fehler/verbindung-zeitueberschreitung.mdx
    - Maintain all technical error messages and commands in original English
    - Translate explanatory text and troubleshooting steps to natural German
    - _Requirements: 1.4, 8.1, 8.3_

- [x] 4. Implement high-priority Palworld German translations
  - [x] 4.1 Create German Palworld introduction page
    - Translate games/palworld/introduction.mdx to de/spiele/palworld/einfuehrung.mdx
    - Use appropriate German gaming terminology for Palworld-specific concepts
    - Maintain all external links and technical specifications unchanged
    - _Requirements: 1.4, 8.2, 8.3_

  - [x] 4.2 Create German Palworld join server guide
    - Translate games/palworld/join-server.mdx to de/spiele/palworld/server-beitreten.mdx
    - Preserve all IP addresses, port numbers, and technical connection details
    - Translate UI element references to appropriate German equivalents
    - _Requirements: 1.4, 8.1, 8.4_

- [x] 4.3 Implement high-priority Minecraft Spanish translations
  - [x] 4.3.1 Create Spanish Minecraft introduction page
    - Translate games/minecraft/introduction.mdx to es/juegos/minecraft/introduccion.mdx
    - Use natural Spanish gaming terminology and maintain technical accuracy
    - Implement Spanish CardGroup components with localized titles and descriptions
    - _Requirements: 1.1, 8.2, 8.3_

  - [x] 4.3.2 Create Spanish Minecraft join server guide
    - Translate games/minecraft/join-server.mdx to es/juegos/minecraft/unirse-servidor.mdx
    - Preserve all code blocks, IP addresses, and technical commands exactly as-is
    - Translate image alt text and captions to Spanish while maintaining accessibility
    - _Requirements: 1.1, 8.1, 8.5_

  - [x] 4.3.3 Create Spanish Minecraft common errors guide
    - Translate games/minecraft/common-errors/connection-timed-out.mdx to es/juegos/minecraft/errores-comunes/conexion-tiempo-agotado.mdx
    - Maintain all technical error messages and commands in original English
    - Translate explanatory text and troubleshooting steps to natural Spanish
    - _Requirements: 1.1, 8.1, 8.3_

- [x] 4.4 Implement high-priority Palworld Spanish translations
  - [x] 4.4.1 Create Spanish Palworld introduction page
    - Translate games/palworld/introduction.mdx to es/juegos/palworld/introduccion.mdx
    - Use appropriate Spanish gaming terminology for Palworld-specific concepts
    - Maintain all external links and technical specifications unchanged
    - _Requirements: 1.1, 8.2, 8.3_

  - [x] 4.4.2 Create Spanish Palworld join server guide
    - Translate games/palworld/join-server.mdx to es/juegos/palworld/unirse-servidor.mdx
    - Preserve all IP addresses, port numbers, and technical connection details
    - Translate UI element references to appropriate Spanish equivalents
    - _Requirements: 1.1, 8.1, 8.4_

- [x] 5. Implement internal link resolution system
  - [x] 5.1 Update German pages with proper internal linking
    - Convert internal links in German pages to point to German equivalents where available
    - Implement temporary English links with German notice for untranslated pages
    - Create reusable German notice component for untranslated content references
    - _Requirements: 5.1, 5.3, 3.4_

  - [x] 5.2 Validate asset path consistency
    - Ensure all image references in German pages use correct relative paths
    - Verify that shared assets load properly from German page contexts
    - Test that all CardGroup icons and components render correctly in German pages
    - _Requirements: 5.5, 2.4_

- [ ] 5.3 Implement Spanish internal link resolution system
  - [ ] 5.3.1 Update Spanish pages with proper internal linking
    - Convert internal links in Spanish pages to point to Spanish equivalents where available
    - Implement temporary English links with Spanish notice for untranslated pages
    - Create reusable Spanish notice component for untranslated content references
    - _Requirements: 5.2, 5.4, 3.4_

  - [ ] 5.3.2 Validate Spanish asset path consistency
    - Ensure all image references in Spanish pages use correct relative paths
    - Verify that shared assets load properly from Spanish page contexts
    - Test that all CardGroup icons and components render correctly in Spanish pages
    - _Requirements: 5.5, 2.4_

- [x] 6. Update navigation configuration for translated content
  - Add German Minecraft pages to German navigation groups in docs.json
  - Add German Palworld pages to German navigation groups in docs.json
  - Ensure German navigation only includes pages that actually exist to prevent 404s
  - _Requirements: 4.3, 3.2, 3.3_

- [x] 6.1 Update navigation configuration for Spanish content
  - Add Spanish Minecraft pages to Spanish navigation groups in docs.json
  - Add Spanish Palworld pages to Spanish navigation groups in docs.json
  - Ensure Spanish navigation only includes pages that actually exist to prevent 404s
  - _Requirements: 4.3, 3.2, 3.3_

- [x] 7. Implement SEO and metadata optimization
  - [x] 7.1 Add German SEO metadata to all translated pages
    - Write natural German titles and descriptions for all translated pages
    - Ensure German meta descriptions are 140-160 characters and include relevant keywords
    - Add appropriate German tags and keywords to frontmatter
    - _Requirements: 6.1, 6.3, 6.5_

  - [x] 7.2 Implement localized slug structure
    - Use natural German terminology for all German page slugs
    - Ensure German URLs reflect terms German users would search for
    - Maintain consistent slug naming conventions across German content
    - _Requirements: 1.1, 4.4, 6.7_

- [ ] 7.3 Add Spanish SEO metadata to all translated pages
  - Write natural Spanish titles and descriptions for all translated pages
  - Ensure Spanish meta descriptions are 140-160 characters and include relevant keywords
  - Add appropriate Spanish tags and keywords to frontmatter
  - _Requirements: 6.2, 6.4, 6.5_

- [ ] 7.4 Implement Spanish localized slug structure
  - Use natural Spanish terminology for all Spanish page slugs
  - Ensure Spanish URLs reflect terms Spanish users would search for
  - Maintain consistent slug naming conventions across Spanish content
  - _Requirements: 1.1, 4.5, 6.7_

- [x] 8. Create cross-reference system between languages
  - [x] 8.1 Implement related guides sections in German
    - Translate "Related Guides" sections with appropriate German links
    - Link to German equivalents where available, English with notice where not
    - Maintain logical content relationships across language boundaries
    - _Requirements: 5.1, 5.3, 5.6_

  - [x] 8.2 Add cross-game references in German content
    - Implement German cross-references between similar guides (e.g., join server guides)
    - Maintain the cross-referencing patterns established in English content
    - Use natural German phrasing for cross-reference descriptions
    - _Requirements: 5.1, 5.6, 8.3_

- [ ] 8.3 Implement related guides sections in Spanish
  - Translate "Related Guides" sections with appropriate Spanish links
  - Link to Spanish equivalents where available, English with notice where not
  - Maintain logical content relationships across language boundaries
  - _Requirements: 5.2, 5.4, 5.6_

- [ ] 8.4 Add cross-game references in Spanish content
  - Implement Spanish cross-references between similar guides (e.g., join server guides)
  - Maintain the cross-referencing patterns established in English content
  - Use natural Spanish phrasing for cross-reference descriptions
  - _Requirements: 5.2, 5.6, 8.3_

- [-] 9. Implement build validation and testing
  - [ ] 9.1 Create automated link validation for German content
    - Write tests to verify all internal links in German pages resolve correctly
    - Validate that German navigation only references existing pages
    - Ensure build process fails gracefully if German links are broken
    - _Requirements: 3.1, 3.3, 2.4_

  - [ ] 9.2 Create automated link validation for Spanish content
    - Write tests to verify all internal links in Spanish pages resolve correctly
    - Validate that Spanish navigation only references existing pages
    - Ensure build process fails gracefully if Spanish links are broken
    - _Requirements: 3.1, 3.3, 2.4_

  - [ ] 9.3 Validate English content preservation
    - Write tests to ensure no existing English URLs have changed
    - Verify that English navigation and content remain exactly as before
    - Test that English page functionality is unaffected by multilingual additions
    - _Requirements: 2.1, 2.2, 2.3_

- [ ] 10. Create translation quality assurance system
  - [ ] 10.1 Implement German content validation
    - Create checklist for German translation quality (technical accuracy, natural flow)
    - Validate that all code blocks and technical commands remain unchanged
    - Ensure German gaming terminology is used consistently across all content
    - _Requirements: 8.1, 8.2, 8.3_

  - [ ] 10.2 Implement Spanish content validation
    - Create checklist for Spanish translation quality (technical accuracy, natural flow)
    - Validate that all code blocks and technical commands remain unchanged
    - Ensure Spanish gaming terminology is used consistently across all content
    - _Requirements: 8.1, 8.2, 8.3_

  - [ ] 10.3 Test incremental rollout functionality
    - Verify site builds successfully with only partial German and Spanish translations
    - Test that missing German and Spanish pages don't break navigation or cause 404s
    - Validate that German and Spanish users can navigate available content without errors
    - _Requirements: 3.1, 3.2, 3.3_