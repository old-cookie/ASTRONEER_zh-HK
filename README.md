# ASTRONEER Simplified Chinese to Traditional Chinese Localization Guide

Last Updated: Nov 23, 2026

## Overview

This guide provides detailed instructions for converting ASTRONEER's Simplified Chinese (zh-Hans) localization to Traditional Chinese (zh-HK). The process involves extracting game files, modifying localization resources, and creating a custom language pack.

## Prerequisites

- ASTRONEER game installation
- Required Tools:
  - [Game Extractor](https://www.watto.org/game_extractor.html)
  - [UnrealLocresEditor v1.4.6](https://github.com/Snoozeds/UnrealLocresEditor/releases/download/1.4.6/UnrealLocresEditor-1.4.6-win-x64.zip)
  - [UnrealPak Utility](https://github.com/RiotOreO/unrealpak/archive/refs/heads/main.zip)

## Installation

1. Download the latest version of `zzz_ASTRONEER_zh-HK_p.pak`
2. Place the file in your ASTRONEER installation directory:

   ```
   [GAME_INSTALL_LOCATION]\ASTRONEER\
   ```

**Note:** To restore the original game files, simply remove the `zzz_ASTRONEER_zh-HK_p.pak` file from the installation directory.

## Development Guide

### 1. Extracting Game Files
Use Game Extractor

### 2. Localization Process

#### 2.1 Engine Localization

1. Install UnrealLocresEditor v1.4.6
2. Launch `UnrealLocresEditor.Desktop.exe`
3. Confirm the download of `UnrealLocres.exe` when prompted
4. Open the Engine localization file:

   ```
   [TEMP]\Engine\Content\Localization\Engine\zh-Hans\Engine.locres
   ```

5. Perform the translation
6. Export the modified locres file to:

   ```
   zzz_[MOD_NAME]_p\Astro\Content\Localization\Game\zh-Hans\Engine.locres
   ```

### 3. File Structure

Ensure your mod directory follows this exact structure:

```
zzz_[MOD_NAME]_p/
├── Astro/
│   └── Content/
│       └── Localization/
│           └── Game/
│               └── zh-Hans/
│                   └── Game.locres
└── Engine/
    └── Content/
        └── Localization/
            └── Engine/
                └── zh-Hans/
                    └── Engine.locres
```

### 4. Creating the PAK File

1. Extract the UnrealPak utility
2. Open Command Prompt
3. Execute the following command:

   ```bash
   "[UNREALPAK_LOCATION]\unrealpak-main\UnrealPak.exe" "[MOD_LOCATION]\zzz_[MOD_NAME]_p.pak" -create=filelist.txt -compress
   ```

## Technical Notes

- File naming is critical:
  - The `_p` suffix indicates it's a patch file
  - The `zzz_` prefix ensures the game loads this PAK file last in the loading order, which is necessary for proper mod functionality
- Maintain original file structure within the PAK file
- Use appropriate character encoding (UTF-8) when editing localization files

## Version Compatibility

This guide is tested with:

- ASTRONEER v1.36.43.0
- UnrealLocresEditor v1.4.6
