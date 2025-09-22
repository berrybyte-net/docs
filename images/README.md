# Image Organization

This document describes the new categorized image structure for the berrybyte Wiki.

## Directory Structure

```
images/
├── games/           # Game-specific screenshots and images
│   ├── enshrouded/  # Enshrouded game images
│   ├── minecraft/   # Minecraft game images
│   ├── palworld/    # Palworld game images
│   ├── soulmask/    # Soulmask game images
│   └── vrising/     # V Rising game images
├── general/         # General-purpose images used across multiple contexts
├── panel/           # Game panel and control interface images
└── site/            # Website and landing page images

logo/                # Logo files (separate directory)
├── dark-new.webp
├── dark.svg
├── light-new.webp
└── light.svg
```

## Categories

### Games (`/images/games/`)
Game-specific screenshots, UI elements, and instructional images organized by game:
- **enshrouded/**: Server setup, world management
- **minecraft/**: World conversion, server setup
- **palworld/**: Server configuration, admin settings, Xbox setup
- **soulmask/**: Server management, player administration
- **vrising/**: Server connection, gameplay UI

### General (`/images/general/`)
Reusable images that apply to multiple games or general server management:
- Server connection interfaces
- Steam-related screenshots
- File management operations
- Archive/backup operations

### Panel (`/images/panel/`)
Game control panel and administrative interface screenshots:
- Server control panels
- Backup interfaces
- User management
- Server startup configurations

### Site (`/images/site/`)
Website and marketing-related images:
- Landing pages
- Game selection interfaces
- Site navigation examples

## Usage Guidelines

When adding new images:
1. Place them in the appropriate category folder
2. Use descriptive, kebab-case filenames
3. Include the game name prefix for game-specific images
4. Update this README if adding new categories

## External Images

Game banners are hosted externally on `berrybyte.net/assets/games/banners/` and referenced in the introduction page. These are not part of the local image structure.