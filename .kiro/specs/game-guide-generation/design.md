# Design Document

## Overview

The Game Guide Generation system is designed to create comprehensive, SEO-optimized guides for multiple games in the berrybyte wiki that currently have placeholder "Guides coming soon" content. The system will generate consistent, user-friendly guides following established patterns from successful guides like the Palworld series.

Based on research, the following games require guide generation:
- **Priority 1:** Valheim (8 guides needed)
- **Priority 2:** Factorio (8 guides needed) 
- **Priority 3:** Sons of the Forest (8 guides needed)
- **Additional games:** CS2, Conan Exiles, Don't Starve Together, FiveM, Garry's Mod, and others (6-8 guides each)

## Architecture

### Content Generation Pipeline

The system follows a structured approach for each game:

1. **Game Analysis Phase**: Parse the game's introduction.mdx file to extract required guide titles and metadata
2. **Template Selection Phase**: Select appropriate content templates based on guide type (setup, join, configuration, etc.)
3. **Content Generation Phase**: Generate SEO-optimized content following established patterns
4. **Quality Assurance Phase**: Validate formatting, SEO compliance, and consistency
5. **File Creation Phase**: Create properly formatted .mdx files with correct frontmatter

### Guide Categories

Based on analysis of existing introduction pages, guides fall into these categories:

**Core Setup Guides:**
- Server Setup
- Join Your Server

**Enhancement Guides:**
- Installing Mods/Plugins/Resources/Addons
- Popular [Game-specific] Mods

**Configuration Guides:**
- Server Configuration
- Performance Optimization
- World Management/Generation Settings

**Management Guides:**
- Admin Commands
- Common Server Issues
- Player Management

## Components and Interfaces

### GuideGenerator Interface

```typescript
interface GuideGenerator {
  generateGuide(gameId: string, guideType: string, guideTitle: string): GuideContent
  validateContent(content: GuideContent): ValidationResult
  createMdxFile(content: GuideContent, filePath: string): void
}
```

### ContentTemplate Interface

```typescript
interface ContentTemplate {
  frontmatter: FrontmatterTemplate
  introduction: IntroductionTemplate
  sections: SectionTemplate[]
  conclusion: ConclusionTemplate
}
```

### Game-Specific Configuration

Each game requires specific configuration including:
- SEO keywords and phrases
- Technical requirements (RAM, CPU, storage)
- Specific terminology and features
- Related guide references
- berrybyte hosting URLs

## Data Models

### GuideContent Model

```typescript
interface GuideContent {
  frontmatter: {
    title: string           // SEO-optimized title with keywords
    sidebarTitle: string    // Shorter title for navigation
    description: string     // 140-160 character SEO description
    tags: string           // Comma-separated game and hosting tags
  }
  introduction: string      // 1-2 sentences with natural keyword integration
  sections: Section[]       // Main content sections with H2 headers
  relatedGuides: string[]   // Links to related guides for SEO
  conclusion?: string       // Optional quick tips or FAQ
}
```

### Section Model

```typescript
interface Section {
  title: string            // H2 section header
  content: string          // Section content with numbered steps
  subsections?: Subsection[] // Optional H3 subsections
}
```

### GameConfig Model

```typescript
interface GameConfig {
  id: string               // Game identifier (e.g., "valheim")
  name: string             // Display name (e.g., "Valheim")
  keywords: string[]       // SEO keywords for this game
  hostingUrl: string       // berrybyte hosting page URL
  requirements: {          // System requirements
    ram: string
    cpu: string
    storage: string
  }
  steamAppId?: string      // Steam app ID for SteamCMD instructions
  modSystem?: string       // Mod system type (BepInEx, Workshop, etc.)
}
```

## Error Handling

### Content Validation

- **Frontmatter Validation**: Ensure all required fields are present and description length is 140-160 characters
- **SEO Validation**: Verify keyword integration is natural and not over-optimized
- **Format Validation**: Check markdown syntax, heading hierarchy, and link validity
- **Consistency Validation**: Ensure tone and style match existing guides

### File System Operations

- **Path Validation**: Verify target directories exist and are writable
- **Duplicate Detection**: Check for existing files and handle overwrites appropriately
- **Backup Strategy**: Create backups of existing files before overwriting

### Content Quality Checks

- **Readability Validation**: Ensure steps are concise (max 2 sentences) and actionable
- **Link Validation**: Verify all internal and external links are functional
- **Image Reference Validation**: Check that referenced images exist in the images directory

## Testing Strategy

### Unit Testing

- **Template Generation**: Test each guide template generates valid content
- **SEO Compliance**: Verify meta descriptions, titles, and keyword integration
- **Content Formatting**: Validate markdown syntax and structure
- **Game Configuration**: Test game-specific data integration

### Integration Testing

- **File Creation**: Test complete guide generation and file system operations
- **Cross-Reference Validation**: Verify related guide links are accurate
- **Batch Processing**: Test generating multiple guides for a single game

### Content Quality Testing

- **Style Consistency**: Compare generated content against existing successful guides
- **SEO Effectiveness**: Validate keyword density and natural integration
- **User Experience**: Ensure guides are scannable and actionable

### Manual Review Process

- **Content Accuracy**: Technical review of game-specific information
- **Brand Consistency**: Ensure berrybyte branding and messaging alignment
- **Editorial Review**: Grammar, tone, and clarity validation

## Implementation Approach

### Phase 1: Core Infrastructure
- Implement base GuideGenerator class
- Create content templates for each guide type
- Set up game configuration system
- Implement validation framework

### Phase 2: Priority Game Implementation
- Generate all guides for Valheim (Priority 1)
- Generate all guides for Factorio (Priority 2)
- Generate all guides for Sons of the Forest (Priority 3)
- Validate and refine templates based on results

### Phase 3: Remaining Games
- Generate guides for CS2, Conan Exiles, Don't Starve Together
- Generate guides for FiveM, Garry's Mod, and other remaining games
- Implement batch processing for efficiency

### Phase 4: Quality Assurance
- Comprehensive testing of all generated content
- SEO validation and optimization
- Cross-reference link validation
- Final editorial review

## SEO Optimization Strategy

### Keyword Integration

- **Title Optimization**: Include primary keywords naturally in H1 titles
- **Meta Description**: Craft compelling 140-160 character descriptions with keywords
- **Content Keywords**: Integrate long-tail keywords naturally throughout content
- **Tag Strategy**: Use game-specific and hosting-related tags consistently

### Internal Linking

- **Related Guides**: Link to relevant guides within the same game
- **Same-Game Focus**: Keep related guides focused on the same game and general panel/support guides, avoiding cross-game references
- **Panel Integration**: Link to relevant panel management guides
- **Hub Pages**: Ensure proper linking back to game introduction pages

### Featured Snippet Optimization

- **Numbered Lists**: Structure steps as numbered lists for snippet eligibility
- **Clear Headers**: Use descriptive H2 and H3 headers for content organization
- **Concise Answers**: Provide direct answers to common questions
- **Table Usage**: Use tables for system requirements and comparison data

## Content Consistency Framework

### Style Guidelines

- **Tone**: Professional, clear, and helpful (matching existing guides)
- **Voice**: Active voice with concise instructions
- **Formatting**: Consistent use of bold, code blocks, and emphasis
- **Structure**: Standardized section organization across all guides

### Template Standardization

- **Introduction Pattern**: Game name + hosting benefit + guide purpose
- **Step Format**: Numbered steps with 1-2 sentence instructions
- **Conclusion Pattern**: Quick tips, troubleshooting, or related guides
- **Frontmatter Format**: Consistent metadata structure across all guides

### Quality Metrics

- **Readability Score**: Target 8th-grade reading level for accessibility
- **Content Length**: Optimize for comprehensive coverage without fluff
- **Link Density**: Appropriate internal linking without over-optimization
- **Keyword Density**: Natural keyword integration (1-2% density target)