# Requirements Document

## Introduction

This feature involves creating comprehensive game guides for multiple games in the berrybyte wiki that currently have placeholder "Guides coming soon" content. The system needs to generate SEO-optimized, user-friendly guides following the existing style and format of successful guides like the Palworld series, while covering essential topics for each game including server setup, joining servers, configuration, mods, and troubleshooting.

## Requirements

### Requirement 1

**User Story:** As a wiki content manager, I want to generate complete guide sets for games that currently have placeholder content, so that users can find comprehensive information for all supported games.

#### Acceptance Criteria

1. WHEN a game has placeholder "Guides coming soon" content THEN the system SHALL generate all guides listed in that game's introduction page
2. WHEN generating guides THEN the system SHALL follow the existing markdown format and structure used in successful guides like Palworld
3. WHEN creating guides THEN the system SHALL include frontmatter in the format: title, sidebarTitle, description (140-160 characters), and tags
4. WHEN writing content THEN the system SHALL use H1 for guide titles, H2 for main sections, and H3 only when necessary
5. WHEN structuring content THEN the system SHALL use numbered steps with short, active-voice instructions (max 2 sentences each)
6. WHEN relevant THEN the system SHALL link to related guides within the same game and general panel/support guides, but SHALL NOT include links to other games
7. WHEN creating new guides THEN the system SHALL add the guide path to the appropriate game section in docs.json navigation
8. WHEN writing H1 titles THEN the system SHALL use simple, natural titles without any suffixes like "- Complete X Guide", "- Complete Connection Guide", or similar patterns (e.g., use "How to Join a Valheim Server" NOT "How to Join a Valheim Server - Complete Connection Guide")
9. WHEN writing any content sections THEN the system SHALL keep all content concise and avoid bloated explanations, flowery language, or unnecessary marketing copy that could overwhelm users
10. WHEN including troubleshooting or common questions THEN the system SHALL use AccordionGroup and Accordion components for better organization and scannability

### Requirement 2

**User Story:** As an SEO specialist, I want all generated guides to be optimized for search engines with natural keyword integration, so that the wiki ranks well for game-specific hosting searches.

#### Acceptance Criteria

1. WHEN creating guide titles THEN the system SHALL include natural long-tail SEO keywords like "Valheim server hosting" or "Factorio dedicated server setup"
2. WHEN writing introductions THEN the system SHALL keep them brief (1-2 sentences maximum) and naturally incorporate target keywords without bloated marketing language
3. WHEN structuring content THEN the system SHALL optimize for Google featured snippets with clear, scannable formatting
4. WHEN adding descriptions THEN the system SHALL write SEO-friendly meta descriptions that include relevant keywords and are 140-160 characters in length
5. WHEN creating tags THEN the system SHALL include game-specific and hosting-related tags for better categorization

### Requirement 3

**User Story:** As a user seeking help with game server setup, I want guides that follow a consistent format and tone, so that I can easily navigate and understand instructions across different games.

#### Acceptance Criteria

1. WHEN writing guides THEN the system SHALL use a clear, concise, and professional tone consistent with existing guides
2. WHEN structuring content THEN the system SHALL start each guide with a short introduction that includes keywords naturally
3. WHEN organizing information THEN the system SHALL use bullet points, numbered lists, and tables where appropriate for scannability
4. WHEN concluding guides THEN the system SHALL end with quick tips, FAQs, or related guides when relevant
5. WHEN formatting THEN the system SHALL maintain consistency with existing guide layouts and styling

### Requirement 4

**User Story:** As a game server administrator, I want comprehensive coverage of essential topics for each game, so that I can find all necessary information for server management in one place.

#### Acceptance Criteria

1. WHEN generating guides for a game THEN the system SHALL create all guides referenced in the game's introduction page
2. WHEN creating server setup guides THEN the system SHALL include step-by-step instructions for berrybyte hosting setup
3. WHEN writing join server guides THEN the system SHALL include IP finding instructions and connection steps
4. WHEN covering configuration THEN the system SHALL include server settings and optimization information
5. WHEN addressing troubleshooting THEN the system SHALL include common issues, admin commands, and solutions

### Requirement 5

**User Story:** As a content maintainer, I want the guide generation process to prioritize specific games in order, so that the most important games get comprehensive guides first.

#### Acceptance Criteria

1. WHEN starting guide generation THEN the system SHALL begin with Valheim as the first priority
2. WHEN Valheim guides are complete THEN the system SHALL proceed to Factorio as the second priority  
3. WHEN Factorio guides are complete THEN the system SHALL proceed to Sons of the Forest as the third priority
4. WHEN the priority games are complete THEN the system SHALL continue with remaining games that have placeholder content
5. WHEN processing each game THEN the system SHALL complete all guides for that game before moving to the next

### Requirement 6

**User Story:** As a user reading guides, I want content that is practical and actionable without unnecessary fluff, so that I can quickly accomplish my server setup and management tasks.

#### Acceptance Criteria

1. WHEN writing instructions THEN the system SHALL prioritize clarity and user-friendliness over word count
2. WHEN providing steps THEN the system SHALL make each step immediately actionable by users
3. WHEN including information THEN the system SHALL avoid unnecessary fluff and focus on practical guidance
4. WHEN structuring content THEN the system SHALL keep layouts neat and scannable for quick reference
5. WHEN adding examples THEN the system SHALL include relevant code snippets, CLI commands, or configuration examples where helpful